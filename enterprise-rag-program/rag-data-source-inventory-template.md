# RAG Data Source Inventory Template

The inventory the data workstream runs on. Owned by Data Engineering and Data Governance jointly, because half these columns are technical and half are policy.

A filled-in row, weak against better: [Sample RAG Inventory Row and Failure Trace](../examples/sample-rag-inventory-row-and-failure-trace.md).

Fill this before architecture is finalized. The access-control column in particular drives the retrieval design, and discovering in week 12 that a priority source has no machine-readable permission model is the most expensive way to learn it.

## Inventory

| ID | Source | Type | Shape | Path | Owner | Sensitivity | Access control model | Permission hygiene | Metadata available | Volume | Change rate | Refresh | Permission-change propagation | Deletion propagation | In scope | Notes |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| DS-01 | | | | | | | | not reviewed | | | | | | | | |
| DS-02 | | | | | | | | not reviewed | | | | | | | | |

Column guidance:

- **Type** - wiki, ticketing, file share, CRM, database, email, code repository, PDF archive
- **Shape** - structured (tables, records, transactions) or unstructured (documents, pages, messages). Some sources are both: a CRM has records and free-text notes. Not everything becomes a vector; see the [primer](rag-architecture-primer.md#structured-and-unstructured-information).
- **Path** - **indexed** (ingested, chunked, embedded), **live query** (SQL, API, or semantic layer at question time), or **both**. Numeric questions over structured data are usually best answered live, as the user; embedding rows to answer them is the wrong tool. Indexing *about* structured data is often right: table and metric descriptions, entity names, and free-text fields such as CRM notes. Decided by the data lead, with AI engineering consulted.
- **Metadata available** - which knowledge-card fields the source can actually supply, marked **native** (the source exports it), **derived** (the pipeline must extract it, such as an effective date from the text, or entities), or **manual**. Most sources supply only created and modified dates natively. A missing effective date means superseded versions cannot be told apart from current ones. See the [primer's knowledge card](rag-architecture-primer.md#a-chunk-is-a-knowledge-card).
- **Permission-change propagation** - the target window for a permission change (a user leaving a group, a folder moved, sharing revoked) to take effect in retrieval, and whether it has been tested. Changes like these often don't touch the document or its modified date, so ordinary content refresh will not catch them.
- **Sensitivity** - public, internal, confidential, restricted, regulated
- **Access control model** - the actual mechanism, not the aspiration. "Group-based ACL, exportable per document" is usable. "People just know" is not.
- **Permission hygiene** - one of: **not reviewed** / **reviewed** (permissions checked, no oversharing found) / **remediated** (oversharing found and fixed at source) / **restricted** (oversharing found, source limited to a named group or excluded until fixed). Every row starts at "not reviewed." A source is not ingested in that state. Permission-aware retrieval inherits whatever the source grants, so this column is the oversharing workstream's scoreboard. See the charter's Oversharing Remediation section.
- **Change rate** - how often content changes, which sets the refresh requirement
- **Refresh** - real time, hourly, daily, weekly, static
- **Deletion propagation** - the target window for a document deleted or revoked at source to stop being retrievable from the index and any caches, and whether that window has been tested. "Not wired" is a valid entry and a blocking one.

## Per Source Assessment

Copy per in-scope source.

### DS-__ : _______________

**Owner and escalation path:** _______________

**Why this source, for which use case:** _______________

**Document count and total size:** _______________

**Formats present:** _______________ (PDF, HTML, Office, plain text, images, scanned documents)

**Extraction difficulty:** _______________ Scanned documents and complex tables are where ingestion estimates go wrong.

**Permission model detail.** The critical question is whether permissions can be resolved per document at query time for the requesting user.

- [ ] Permissions are documented
- [ ] Permissions are machine-readable
- [ ] Permissions can be resolved per document at query time
- [ ] Permission changes propagate to the index within _____ (target)

If the third box is unchecked, this source cannot ship in a permission-aware system. Escalate rather than working around it.

**For a live-query source:** how the query runs as the requesting user (row-level security, a user-scoped token, delegated OAuth), and confirmation that it does not run as the integration's service account. If the source offers no per-user access, record the exception and how the user's entitlements are enforced instead (see the [security playbook](https://github.com/ChefPlex/security-program-playbooks/blob/main/enterprise-rag-security/rag-security-playbook.md)). _______________

**Chunk boundaries (indexed sources).** Where meaning starts and ends in this source: paragraph, heading, policy clause, table section, ticket comment. Not a token count. _______________

**Domain vocabulary.** Acronyms, codenames, product names, and aliases this source uses that a general model would not understand. Record them in the [Glossary](#glossary) below. _______________

**Content quality issues:** _______________ Duplicates, outdated documents, contradictions, drafts mixed with approved versions.

**Retention or deletion requirements:** _______________

**Cross-border or residency constraints:** _______________

**Deletion propagation.** When a document is deleted at source, how does it leave the index, and within what window?

_______________

## Readiness Gate

A source is ready for ingestion when all of these hold. Track partial readiness explicitly rather than ingesting and hoping.

- [ ] Owner named and engaged
- [ ] Sensitivity classified
- [ ] Permission hygiene is reviewed, remediated, or restricted (never "not reviewed")
- [ ] Permission model machine-readable and resolvable per document, or (live query) the query runs as the user
- [ ] Permission-change propagation defined, with a target window, and tested
- [ ] Extraction path proven on a representative sample
- [ ] Chunk boundaries chosen for this source, and a sample of ____ chunks reviewed by ____: each makes sense on its own
- [ ] Glossary terms for this source reviewed by the source owner
- [ ] Refresh mechanism defined and costed
- [ ] Deletion propagation defined, with a target window, and tested
- [ ] Content quality assessed, known issues logged as risks
- [ ] Legal and privacy review complete for regulated content

## Common Findings

Log these as risks or issues when found rather than absorbing them silently:

- **The wiki has three versions of the same policy.** Content governance problem. Retrieval will faithfully return the wrong one.
- **A folder is shared with the whole company.** Permission-aware retrieval will enforce that share exactly as written. Mark the source restricted until it is fixed.
- **Permissions live in a system that cannot export them.** Blocks permission-aware retrieval entirely.
- **A third of the corpus is scanned PDFs.** OCR quality now sets retrieval quality.
- **Nobody has owned the source since a reorg.** No one can approve inclusion or fix content.
- **The source contains regulated data nobody flagged.** Discovered during ingestion, which is the worst time.
- **The source has no effective dates.** Old and current policy rank side by side, and retrieval cannot prefer the one in force.
- **The source is mostly internal shorthand.** Codenames and acronyms dominate. Vector-only retrieval will underperform; plan for hybrid retrieval and a glossary.
- **Someone proposes embedding a database table to answer numeric questions.** Usually the wrong path. Query it live, as the user, and index the table's descriptions instead so the planner can find it.

## Glossary

The enterprise vocabulary retrieval needs, owned by the data lead (or a named delegate). Each source owner reviews the terms for their source before it is ingested. Feed it to hybrid retrieval (keyword synonyms and aliases), to metadata tagging, and to the eval set's terminology questions.

| Term | Means | Aliases and acronyms | Source(s) | Reviewed by |
|---|---|---|---|---|
| | | | | |
