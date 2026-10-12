# RAG Architecture Primer

What a Retrieval-Augmented Generation (RAG) system actually does, in enough detail to run the program and argue with the architecture. Written for the TPM, the security architect, and the business owner who have to make decisions about RAG without building it.

Read this before the [Program Playbook](enterprise-rag-program-playbook.md) if the terms in it are new.

## One Question, End to End

An employee asks: *"Can I expense a hotel upgrade on a client trip?"*

1. The system already holds the company's documents split into short passages, called **chunks**, each a paragraph or a section long, prepared ahead of time.
2. It searches those chunks for the ones most likely to answer the question, skipping any the employee isn't allowed to see. It finds three: two paragraphs of the travel policy and one FAQ entry.
3. It pastes those three passages, with their sources, next to the question, and sends the whole thing to a **large language model (LLM)**: the kind of model behind ChatGPT or Claude.
4. The model writes an answer using only those passages, and cites the policy section it came from. If the passages don't answer the question, it says so.

That is RAG. Retrieval (the first two of those) finds the evidence. Generation (the last two) writes the answer from it. The rest of this primer is about what makes each step work well, and what makes it fail.

## The Model Is Fixed. The Context Changes.

RAG does not normally create, train, or fine-tune a model for your company, or for each question. The model is usually an existing one from a provider (OpenAI, Anthropic, Google, a model hosted inside a data platform, or a self-hosted open model), called through an API.

What changes on every request is the model's **context**: the text it is given to read alongside the question. The model's knowledge stays the same; the evidence it is handed is new each time.

Fine-tuning is a separate decision. Fine-tuning the LLM teaches a style, format, or task; it is a poor way to give a model facts that change, because those facts are frozen at training time and cannot be filtered per user. Fine-tuning the *search* models (the embedding model or reranker, below) on your own vocabulary is a different and sometimes worthwhile option. Either one is an architecture decision record (ADR): a short written record of the decision, the options, and why. The program keeps one per major decision ([ADR Template](../adr-template.md)).

## RAG Is a Lens

An enterprise has a large information horizon: every wiki, file share, ticket, contract, table, and system of record it owns. No model reasons over that whole horizon, and RAG doesn't ask it to.

Retrieval works like a lens pointed at part of that horizon. How the documents were split, what labels they carry, how the search works, what is filtered out, and how the results are re-sorted all decide where the lens points and what comes into focus. The model then reasons over whatever is in focus.

A telescope can give an extremely clear view of one valley and tell you nothing about the rest of the horizon. The model sees only what retrieval put in front of it, and has no way to know what it wasn't shown. So a capable model looking through the wrong lens produces a well-written answer grounded in the wrong evidence. A polished answer does not prove that retrieval worked.

## A Request, Step by Step

1. Receive the question, with the identity of the person asking.
2. Plan: decide which sources to use, and whether the question needs documents, structured data, or both. This step is often itself an LLM call.
3. Retrieve candidate evidence, with the permission filter and any other filters (date, region, product, document status) applied **inside the search**, not afterward.
4. Rerank the candidates so the best evidence is at the top.
5. Assemble the context: remove duplicates, pick what fits, decide the order, and attach the source to each piece.
6. Call the model with the instructions, the question, and the evidence.
7. The model generates an answer grounded in that evidence, or declines if the evidence doesn't support one.
8. Return the answer with citations back to the sources it used.

Steps 6 and 7 are the model call. Everything else, including any LLM you use for planning, is your system, not the model provider's. That is where most of the quality, most of the security, and most of the program's work lives.

## The Architecture

```text
   Question + user identity
              |
              v
   Query planning ------------------------------+
   (which sources, which path)                  |
              |                                 |
   UNSTRUCTURED PATH                     STRUCTURED PATH
              |                                 |
              v                                 v
   Hybrid retrieval                      Query drafted (often by an LLM)
   vector + keyword, with the            through a semantic layer or
   permission and metadata               templates, validated, then run
   filters applied INSIDE                AS THE USER (row-level
   the search                            security, user-scoped token)
              |                                 |
              v                                 |
   Reranking                                    |
              |                                 |
              +----------------+----------------+
                               |
                               v
                     Context assembly
                     (dedupe, order, source on every piece)
                               |
                               v
                              LLM
                               |
                               v
                  Answer with citations, or an action the
                  system proposes for an authorization layer
                  outside the model to allow or refuse
```

Behind the unstructured path sits an ingestion pipeline. It runs continuously, not once:

```text
   Source systems
     -> detect changes (change feeds where the source has them, recrawl where it doesn't)
     -> extract and parse (layout-aware for tables, scans, slides)
     -> deduplicate (the same file in two drives, attachments, version copies)
     -> chunk -> attach metadata -> embed + keyword index -> searchable index
   and keep it current:
     -> content changed      -> re-chunk and re-embed that document
     -> document deleted     -> remove it from the index and any caches
     -> permissions changed  -> update who may retrieve it (below)
     -> failed documents     -> a retry queue, not a silent gap
```

Changing the embedding model means re-embedding everything. Build the index so a new version can be built alongside the old one and switched over (and back) rather than rebuilt in place.

**Permissions.** There are two ways to enforce them. **Early binding** copies each document's access list into the index, usually as user and group IDs, and resolves the asking user's groups at query time; it is fast, and only as current as the last permission sync. **Late binding** checks with the source system at query time; it is current, and slower. Either way, store groups rather than expanded lists of people, or every change to a group's membership means re-indexing every document that group can see. Permission changes often don't touch the document at all (someone joins a group, a folder moves), so propagation needs its own mechanism and its own test.

**Where the filter sits matters.** If the search returns the 50 best matches and a later step then removes the 40 the user can't see, the answer is built from 10 leftovers, and better authorized documents that just missed the top 50 were never considered. Nothing unauthorized reached the model, so this is not a leak; it is a quality failure, and a common one. Filtering inside the search avoids it. Use the search engine's native filtered search, apply the filter on both the vector and keyword sides before their results are combined, and test it at realistic scale.

That last part is not optional, because filtered vector search is a known hard problem, not a solved feature. The ACORN paper (Patel et al., 2024) describes the two common methods and their costs: pre-filtering "performs brute force similarity-search over the filtered vector set. This approach scales poorly, becoming inefficient for medium to high selectivity predicates on large datasets" (that is, when a large share of the collection passes the filter), while with post-filtering, "since the database vectors closest to the query vector may not pass the predicate, post-filtering methods must typically expand the search scope. This is often expensive, particularly for search predicates with low selectivity or low correlation to the query vector" ([arXiv 2403.04871](https://arxiv.org/abs/2403.04871)). A permission filter is the hard case for post-filtering almost by definition: who may read a document has nothing to do with what the question means. And the two methods fail at opposite ends: post-filtering struggles for users who can see little, pre-filtering for users who can see a lot. So measure recall and latency with real permission filters for both kinds of user before choosing a vector store. (ACORN's own use of "hybrid search" means vectors plus filters, not the vector-plus-keyword sense used below.)

## Structured and Unstructured Information

Not everything becomes a vector. A common misunderstanding is that RAG means converting the whole enterprise into vectors.

| | Structured | Unstructured |
|:---|:---|:---|
| Examples | CRM, ERP, finance systems, warehouse tables, telemetry, inventory, transactions | SharePoint, Google Drive, PDFs, policies, design docs, support notes, contracts, wikis |
| How it is reached | SQL, APIs, a semantic layer (a governed set of business definitions over the tables, such as "net revenue"), analytical tools, agent tool calls | Ingestion, parsing, chunking, embeddings, keyword indexing, metadata, hybrid search, reranking |
| What it is good for | Exact numbers, current state, totals | Explanation, policy, context, reasons |
| Freshness | Usually queried live, so as fresh as the source; a warehouse is itself loaded on a schedule | Only as fresh as the last index refresh |
| Authorization | The source system's own controls, if the query runs as the user | Copied into the index (early binding) or checked at the source (late binding), and enforced at query time |

A production system often uses both paths for one answer. Take *"Why did enterprise renewals decline last quarter?"*

1. A query against the warehouse gets the actual renewal numbers.
2. Retrieval over account notes, support escalations, and win/loss reports finds the reasons people wrote down.
3. Both go into the context as evidence, and the model connects them.

Embedding rows of a table and hoping retrieval finds the right number is the wrong tool for numeric questions. Indexing *about* structured data is often right, though:

- table and column descriptions and semantic-layer definitions, so the planner can find the right table or metric to query
- names from the data (customers, products), so "Acme" in a question can be matched to the right account
- free-text fields inside records, such as CRM notes and ticket bodies, which are unstructured content that happens to live in a structured system

When an LLM writes the SQL, that query is a new place for errors and for injection. Prefer a semantic layer or parameterized templates over free-form SQL, run read-only as the user, validate before executing, cap rows, time, and cost, and evaluate generated-query accuracy like any other answer.

## Vector Search: A Map of Meaning

An **embedding model** turns a piece of text into a list of numbers (a vector) that places it at a point on a very large map. The map is arranged so that **text with similar meaning tends to land near each other.**

"Cancel my plan" and "terminate my subscription" share no important words, and will usually sit close together on that map. Vector search finds the chunks nearest to the question's point, which is why it finds content by meaning rather than by exact wording. At scale it searches approximately, trading a little accuracy for a lot of speed.

Two things that are commonly gotten wrong:

- **Synonyms don't get the same vector.** They get nearby ones. Nearness is a similarity score, not a match, and "nearby" sometimes includes things that are related without being relevant.
- **The map belongs to the embedding model.** A different model builds a different, incompatible map, and old and new vectors can't be mixed. That is why changing it means re-embedding the entire collection of documents, and why it is decided once, in an ADR.

## Enterprise Vocabulary

A general-purpose embedding model learned its map from public text. It has no idea that "Project Bluebird" is your billing-platform migration, that "the Q-form" is a procurement document, or that two teams use the same acronym for different things. It may place "Bluebird" near content about birds.

Enterprise knowledge is not just documents. It also includes the vocabulary and relationships that make those documents intelligible inside the organization. Retrieval may need:

- a business glossary: acronyms, aliases, product names, project codenames, and what they mean here
- an organizational taxonomy: departments, product lines, regions
- entity relationships: which team owns which service, which product replaced which
- domain metadata on each chunk (below)
- **keyword search alongside vector search**

Keyword search (BM25 is the standard scoring method) matches the exact term "Bluebird," an error code, or a part number that vector search treats loosely. Vector search finds the paraphrase that keyword search misses. Running both and merging their results is **hybrid retrieval**. Their scores aren't on the same scale, so the merge is a tuning decision, commonly done by combining rankings (reciprocal rank fusion) rather than raw scores.

The public evidence for not going vector-only is about text a model was never trained on, which is exactly what an enterprise collection is. BEIR (Thakur et al., NeurIPS 2021 Datasets and Benchmarks) tested ten retrieval approaches across 18 datasets without training on any of them, and found "BM25 is a robust baseline," while "dense and sparse-retrieval models are computationally more efficient but often underperform other approaches" ([arXiv 2104.08663](https://arxiv.org/abs/2104.08663)). Blended RAG (Sawarkar et al., IEEE MIPR 2024) reports that blending dense vector indexes and sparse-encoder indexes (a learned form of term matching) with hybrid query strategies "achieves better retrieval results" on public retrieval benchmarks (NQ and TREC-COVID), and better answers on a public question-answering set (SQuAD) ([arXiv 2404.07220](https://arxiv.org/abs/2404.07220)).

Both are public-benchmark results, and retrieval models have moved on since BEIR. Neither tells you what will win on your documents and your users' questions. Treat hybrid as the starting assumption, and let the eval set's terminology and paraphrase questions confirm or overturn it.

Someone has to own the glossary. The [Program Playbook](enterprise-rag-program-playbook.md) puts it with the data lead rather than inventing a new team.

## Chunking Is a Boundary Decision

Documents are split into chunks before indexing, and retrieval returns chunks, not whole documents. Chunking is usually described as picking a size in **tokens** (the word-pieces models count text in). It is better understood as deciding **where meaning begins and ends.**

Natural boundaries: paragraphs, subsections under a heading, individual policy clauses, table sections, any self-contained unit of meaning. The goal is enough context for a retrieved passage to keep its meaning, and not so much that unrelated material buries the useful part.

Both extremes fail, in different ways.

| Chunks too large | Chunks too small |
|:---|:---|
| One relevant sentence is diluted by pages of unrelated text, so similarity scores blur | The surrounding meaning is lost |
| Each chunk uses more of the **context window** (the limit on how much text the model can read at once), so fewer pieces of evidence fit | A rule is separated from its exception ("Employees may expense..." in one chunk, "...except contractors" in the next) |
| More irrelevant material reaches the model | References break: "the above," "this policy," "see table 3" point at nothing |
| Search is less precise | The passage is ambiguous on its own |

There is also a hard ceiling: embedding models and rerankers read only so many tokens, and anything past their limit is silently cut off.

Techniques for the too-small problem, none of them automatic requirements:

- **Overlap**: each chunk repeats the end of the one before. Costs index size.
- **Contextual headers**: prefix each chunk with its document title and section heading, so "this policy" has a referent.
- **Small-to-big retrieval**: search small, precise chunks, then hand the model the larger section around the match.

Different sources need different boundaries: a policy manual and a ticket thread don't break in the same places. Record the choice per source in the [Data Source Inventory](rag-data-source-inventory-template.md).

## A Chunk Is a Knowledge Card

An indexed chunk is more than its text. Think of it as a card carrying the evidence plus everything needed to find it, filter it, trust it, and cite it. Some fields come from the source system, some have to be derived by the pipeline, and some only a person can supply, which matters when estimating the work.

| Field | Why it is on the card | Usually |
|:---|:---|:---|
| Chunk text | The evidence itself | Native |
| Source document, document ID, heading or section | Citation, and finding the surrounding context | Native |
| Author, owner | Accountability and trust | Native, often stale |
| Created and last-modified dates | Freshness | Native |
| Effective date, version, status (draft or approved) | Which version is in force. Stops a superseded policy from answering | Derived from the text, or manual |
| Document type, business unit, product, region | Filtering to the right part of the business | Partly native, often derived |
| Entities mentioned | Connecting to the vocabulary and relationships above | Derived (entity extraction) |
| Classification | Sensitivity, retention, and handling | From sensitivity labels or data-loss-prevention scanning, else manual |
| Access-control attributes | Who may retrieve it. This is what the permission filter reads | Native, if the source can export it |
| Provenance | Where it came from and when it was ingested, so a bad chunk can be traced | Derived (written by the pipeline) |

Metadata is not decoration. It takes part in retrieval, filtering, governance, provenance, and security. A chunk with no effective date can't be told apart from its replacement, and a chunk with no access-control attributes can't be filtered at all. The security uses of these fields are in the [Enterprise RAG Security Playbook](https://github.com/ChefPlex/security-program-playbooks/blob/main/enterprise-rag-security/rag-security-playbook.md).

## Retrieval and Reranking

Retrieval gets you into the right neighborhood. Reranking picks the right house.

**First-pass retrieval** is built for **recall**: making sure the right chunk is somewhere in the results. It has to search the whole collection fast, so it uses cheap comparisons and returns a generous candidate set, often dozens of chunks. Missing the right chunk here can't be recovered later.

**Reranking** looks only at that candidate set and scores each candidate against the question with a slower, more precise model. A typical reranker (a cross-encoder, or an LLM used as a reranker) reads the question and the passage together, rather than comparing two vectors computed separately in advance. That is what lets it tell "related to the question" from "answers the question." It is not another keyword search. The same BEIR study found that "re-ranking and late-interaction-based models on average achieve the best zero-shot performances, however, at high computational costs" ([arXiv 2104.08663](https://arxiv.org/abs/2104.08663)), which is the trade a reranker makes: better ordering, paid for in latency, and affordable only because it runs on a short candidate list.

Ask about using sugar when baking bread, and first-pass retrieval may return passages on:

- sugar in bread dough
- sugar in coffee
- sugar chemistry
- baking bread in general
- yeast fermentation

All of them sit near the question on the map, because each shares a strong idea with it: "sugar" pulls in the coffee passage, "baking bread" pulls in the general one. First-pass retrieval scores each candidate on overall closeness, so a passage that is very much about sugar can outscore one that is a little about both. The reranker reads each passage against the whole question and pushes the ones about sugar's role *in bread* to the top, so those are the ones that fit in the context.

Context assembly then does its own work: remove near-duplicates, and put the strongest evidence where the model attends best. Liu et al. ("Lost in the Middle," accepted to TACL) found that "performance is often highest when relevant information occurs at the beginning or end of the input context, and significantly degrades when models must access relevant information in the middle of long contexts" ([arXiv 2307.03172](https://arxiv.org/abs/2307.03172)). Newer models handle long contexts better than the ones tested there, so check it on yours; the safe default is still fewer, better chunks, strongest first.

That is why reranking appears as an ADR in the playbook: it adds latency and cost, and it materially improves what the model gets to read.

## Quality = Lens Quality + Reasoning Quality

A wrong answer has two very different kinds of cause, with different owners and different fixes: the lens pointed at the wrong evidence, or the model reasoned badly over the right evidence. Teams reach for "the model got it wrong" first. It should be the last thing they conclude.

The [Evaluation Plan's Which Layer Failed](rag-evaluation-plan-template.md#which-layer-failed) section is the checklist for tracing a wrong answer to the layer that caused it, from "was the right source chosen" through "did the model use the evidence it was given." Use that one; it is linked to the risks and owners in the [RAID Starter Register](rag-raid-starter-register.md).

## A Pattern, Not a Product

There is no single product called RAG. A production system is orchestration (the code that connects the steps and decides what runs when) across:

- source systems and connectors
- ingestion, parsing, and document processing
- embeddings
- vector, keyword, or hybrid search
- metadata and the glossary
- reranking
- identity and policy enforcement
- the model API
- observability and evaluation

Products cover pieces of that list: managed search services, vector databases, search engines that do both vector and keyword search, model APIs, orchestration frameworks, and your own services connecting them. Some cover several pieces at once. None cover the permission model of your sources, the ownership of your glossary, or the definition of a correct answer for your users.

The vector database is not the RAG program. Choosing one is a decision inside the program, recorded as an ADR, made after the questions it has to answer are known.

## Where Security Comes In

The lens has a security reading too. Whatever retrieval brings into focus, the model reads, and the model cannot reliably tell evidence from instructions written inside that evidence. Two rules follow, both covered in full in the security workstream:

- The system can never retrieve information the requesting user could not have accessed directly, on either path.
- Retrieved content is evidence, never instruction, and the model is never the security boundary.

**[Enterprise RAG Security](https://github.com/ChefPlex/security-program-playbooks/tree/main/enterprise-rag-security)**

## Related

- [Enterprise RAG Program Playbook](enterprise-rag-program-playbook.md) - the program this architecture sits inside
- [Data Source Inventory](rag-data-source-inventory-template.md) - per-source path, chunking, metadata, and vocabulary
- [Evaluation Plan](rag-evaluation-plan-template.md) - measuring the lens and the reasoning separately
- [ADR Template](../adr-template.md) - for the decisions this primer keeps pointing at

Last reviewed: 2026-10-12.
