# RAG Evaluation Plan Template

How the program proves quality, and the gate that stops a regression from reaching users.

**Measure retrieval and generation separately.** They fail separately and the fixes are unrelated. If the right document was never retrieved, no amount of prompt work will save the answer. If the right document was retrieved and the answer is still wrong, the retrieval metrics will look fine while users lose trust.

## The Eval Set

The artifact that decides whether any of the other numbers mean anything, and the one most often skipped.

**Source the questions from real users.** Invented questions produce an eval set that passes while the system fails in production, because engineers write questions the system is already good at without meaning to.

| Property | Target |
|---|---|
| Question count | 100 minimum to start, 300+ before general availability |
| Sourced from real users | 100% |
| Has a known correct answer | 100% |
| Has a known source document | 100% |
| Includes unanswerable questions | 10-15% |
| Includes permission-boundary questions | 5-10% |
| Reviewed by a subject matter expert | 100% |
| Held-out set the team does not tune against | 20-30% of questions, kept separate |

**Keep a held-out set.** Engineers tuning prompts, chunking, and retrieval against the full eval set will fit it, and the scores will rise while production quality does not. Split off a held-out portion, restrict access to it, and run it only at milestone gates. If the tuned set improves and the held-out set does not, the change fitted the test.

The unanswerable set matters more than it looks. A system that confidently answers a question the corpus cannot support is worse than one that says it does not know, and nothing else in the eval catches that behavior.

The permission-boundary set is questions where the answer exists in the corpus but the asking user is not entitled to it. Correct behavior is a refusal, not an answer.

**Cover the question types that break retrieval, not just the common ones.** Real user questions skew toward the easy cases. Check the set includes each of these, and add real examples where it doesn't:

| Question type | What it tests |
|:---|:---|
| Synonyms and paraphrase | Vector search finds meaning, not just shared words |
| Internal terminology, acronyms, codenames ("what's the status of Bluebird") | Keyword and glossary coverage a general embedding model lacks |
| Old vs current policy | Effective-date metadata, and whether the superseded version is ranked down |
| Versioned documents | The right version for the asker's product, region, or date |
| Competing sources that disagree | Which source is authoritative, and whether the answer says they disagree |
| Cross-document questions | Evidence assembled from more than one chunk or document |
| Structured plus unstructured ("why did renewals drop") | Both paths run and their results are combined correctly |
| Ambiguous questions | A clarifying question or a stated assumption, not a confident guess |
| No-answer questions | The unanswerable set above |

Tag each eval question with its type and its source, so a score can be read per type and per source. A system can pass overall while failing every codename question. The per-type floor below is what makes that visible.

## Retrieval Metrics

| Metric | What it measures | Target |
|---|---|---|
| Recall@K | Was the correct document in the top K retrieved | > ____ |
| Precision@K | How much of what was retrieved is relevant | > ____ |
| MRR | How high the first correct result ranks | > ____ |
| Recall@K per question type | The same measure, for each type in the table above. The floor applies to every type, not the average | > ____ for every type |
| Recall@K per source | The same measure for each in-scope source, with at least ____ questions per source, so one large source does not hide a broken small one | > ____ for every source |
| Metadata filter accuracy | On labelled queries with known right answers, filters (date, region, product, status) return what they should and exclude what they should | > ____ |
| Superseded-retrieval rate | On the old-vs-current questions, how often a superseded version is retrieved ahead of the one in force | < ____ |
| Freshness lag | Time between a change at source and the index reflecting it, from pipeline logs, per source (R-09) | < source SLO |
| Generated-query accuracy | For structured questions, the drafted SQL or API call returns the right rows, checked against a known answer | > ____ |

Recall is the one to optimize first. A document that is never retrieved cannot be used, and precision problems can be partly absorbed by reranking while recall problems cannot be absorbed at all.

## Generation Metrics

| Metric | What it measures | Target |
|---|---|---|
| Groundedness | Is every claim supported by retrieved context | > ____ |
| Answer correctness | Is the answer right | > ____ |
| Citation accuracy | Do citations point at the content actually used | > ____ |
| Refusal correctness | Does it decline when the corpus cannot support an answer | > ____ |
| Completeness | Does it answer the whole question | > ____ |
| Nugget coverage | Share of the key facts ("nuggets") an SME listed for the question that the answer contains | > ____ |
| Citation support | Share of cited sentences whose cited passage actually supports them (fully, partially, not) | > ____ |

**Nugget coverage and citation support are answer measures used by the public TREC 2024 RAG Track** ([nugget evaluation, arXiv 2411.09607](https://arxiv.org/abs/2411.09607); [support evaluation, arXiv 2504.15205](https://arxiv.org/abs/2504.15205)). Nugget coverage is a practical, measurable form of completeness: an SME writes the few facts a good answer must contain, and the answer is scored on which it includes. Citation support is scored per sentence against the passage cited for it, which is stricter than asking whether the answer as a whole is grounded.

**Reference-free metrics extend coverage past the eval set.** The eval set has a known answer for every question. Production traffic and new questions do not, so classical reference-based scoring cannot reach them. Grounding checks and model-graded scoring with explicit criteria work without a reference answer.

Two approaches worth knowing:

- **Question-generation grounding.** Generate questions from the retrieved context, check the answer addresses them. Directly tests whether the answer reflects its sources.
- **Model-graded scoring with explicit criteria.** A judge model scores against a written rubric. Cheap, repeatable, and only as good as the rubric, so the rubric belongs in this document rather than in a prompt somewhere.

Whatever you choose, **validate the judge against human scoring on a sample before trusting it.** An unvalidated automated judge is a number that feels like evidence.

**Calibrate the judge on this program's own corpus and report the agreement.** A published agreement figure is evidence about that study's corpus, task, and judge model, not about yours. For scale: in the TREC 2024 RAG Track support evaluation, human and GPT-4o support labels agreed exactly on 56% of assessments done from scratch, and 72% when humans post-edited the model's labels; the same study found an independent human judge agreed more with GPT-4o than with the first human ([Thakur et al., arXiv 2504.15205](https://arxiv.org/abs/2504.15205)). Those are that study's figures, for one judge on one task. The lesson for a program is that humans also disagree with each other, so the calibration has to measure both: human-human agreement on a sample, and judge-human agreement on the same sample. Record both numbers and the sample size next to every judged metric.

**Treat off-the-shelf faithfulness scores as unvalidated until calibrated.** Popular faithfulness metrics come with thin published validation. RAGAS, for example, was validated on WikiEval, 50 questions built from 50 Wikipedia pages ([Es et al., arXiv 2309.15217](https://arxiv.org/abs/2309.15217)). A score that has not been checked against human labels on your corpus is a trend line at best, not a gate.

## Which Layer Failed

Every wrong or refused answer gets traced to the layer that failed, because the fix belongs to that layer and its owner. "The model got it wrong" is the conclusion teams reach first and should reach last. This table is the program's one classification of failures: the pilot's failure-point review, [Definition of Done §11](rag-definition-of-done.md#11-operational-validation), and production monitoring all use it. Work it in order:

| Step | Question | If no, the failure is | Starter risk |
|:---|:---|:---|:---|
| 0 | Did planning route the question to the right sources and path (documents, structured data, or both)? | Routing | None seeded; log as an issue |
| 1 | Was the evidence in the corpus or the system of record at all? | Missing content | R-18 |
| 2 | Was it ingested, parsed, chunked, and tagged correctly? | Ingestion, parsing, chunk boundary, or missing metadata | R-01, R-02 |
| 3 | Did retrieval find it? Check vector and keyword results separately, and the permission filter. For a live query: was the drafted SQL or API call correct, and did it return the right rows? | Embedding mismatch, vocabulary gap, keyword miss, over-filtering, or a wrong query | R-19, R-25 |
| 4 | Was it ranked high enough to be kept? | Ranking failure | R-19 |
| 5 | Did it make it into the assembled context? Was a stale version in instead? | Context assembly, or stale content | R-20, R-09 |
| 6 | Given the right evidence, did the model use it correctly? | Not extracted, wrong format, wrong specificity, incomplete | R-21 to R-24 |

A worked trace of one wrong pilot answer: [Sample RAG Inventory Row and Failure Trace](../examples/sample-rag-inventory-row-and-failure-trace.md#part-2-one-wrong-answer-traced).

Steps 0 to 5 are everything before the model reads the evidence, which the [primer](rag-architecture-primer.md#rag-is-a-lens) calls the lens. Only step 6 is the model's reasoning over it.

**This table can only be worked if the system logs, per question:** the rewritten or planned query; the vector and keyword candidate lists before they are merged, and how many candidates each returned with the permission filter applied; the reranked order; which chunks were included in context; any generated SQL and its result; and the index and embedding-model versions. Chunk IDs have to stay stable across re-indexing or old logs can't be traced. These logs hold retrieved text, some of it sensitive, so they need their own access control and retention period.

**Over-filtering needs a test, not a log.** Because the permission filter runs inside the search, production logs can't show what it removed, and must not try: a count of hidden results is a side channel. Detect over-filtering with the permission-boundary test users instead: run the same eval questions for a user who can see little and one who can see a lot, and compare recall on the documents both may read. Build this before the pilot (it is an M5 exit criterion), or the failure-point review has nothing to read.

## Operational Metrics

| Metric | Target |
|---|---|
| P50 latency | |
| P95 latency | |
| Cost per query | |
| Cost per active user per month | |
| Availability | |
| Cache hit rate | |

## Safety and Security Evals

Run alongside quality evals, not as a separate late-stage activity. Scenarios and corpus: [Prompt Injection Threat Model](https://github.com/ChefPlex/security-program-playbooks/tree/main/enterprise-rag-security).

| Check | Target |
|---|---|
| Unauthorized retrieval events | **0** |
| Direct prompt injection resisted | 100% of known corpus |
| Indirect injection resisted | 100% of known corpus |
| System prompt disclosure | 0 |
| Cross-user data leakage | 0 |

**What 100% of a known corpus means.** Passing every case in a known injection corpus means nothing obvious was found. It does not mean the system is safe. The corpus only contains attacks someone already wrote down, so keep adding new cases from red-team work and incidents, and report the result as "resisted N of N known cases, corpus version X," never as "secure."

## CI Gates

Evals run in continuous integration. A change that regresses a gate does not merge.

| Gate | Blocks on | Runs |
|---|---|---|
| Retrieval regression | Recall@K drops more than ____ | Every PR touching retrieval |
| Generation regression | Groundedness drops more than ____ | Every PR touching prompt or model |
| Security regression | Any injection or permission failure | Every PR, no exceptions |
| Cost regression | Cost per query rises more than ____ | Nightly |
| Full suite | Any gate | Pre-release |

The security gate has no tolerance band on purpose. Retrieval quality is a negotiation, unauthorized retrieval is not.

**Set the thresholds above the noise.** Model output varies from run to run, so a single eval run cannot tell a regression from ordinary variation. Before filling in the blanks above:

- **Run each eval suite N times** (N = ____, at least 3) on an unchanged baseline, and record the spread for each metric.
- **Set each regression threshold larger than that measured spread.** A threshold inside the noise blocks good changes at random and teaches the team to override the gate.
- **Gate on the repeated result**, not on one run: compare the mean of N runs against the baseline, and report the range with it.
- **The judge must differ from the generator** in model family or in method (for example a rule-based check, or human scoring on a sample). A judge that shares the generator's model tends to share its blind spots and will grade its own mistakes as correct.

## Review Cadence

| Activity | Frequency | Owner |
|---|---|---|
| Eval suite run | Every PR plus nightly | AI engineering |
| Eval set expansion from production questions | Monthly | Product plus QA |
| Judge validation against human scoring | Quarterly, and after any judge model or rubric change | AI engineering |
| Held-out set run | At each milestone gate only | QA |
| Failure-point review of production misses | Monthly during pilot, quarterly after | AI engineering plus Product |
| Metric target review | Quarterly | Program |

Production questions the system handled badly are the best source of new eval cases. Build the feedback path at launch, not after the first bad quarter.
