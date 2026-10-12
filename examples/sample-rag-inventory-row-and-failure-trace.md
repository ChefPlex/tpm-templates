# Sample RAG Inventory Row and Failure Trace

Two artifacts from an enterprise RAG program, each written twice. The first is one row of the [Data Source Inventory](../enterprise-rag-program/rag-data-source-inventory-template.md). The second is one wrong answer from the pilot, traced through the [Evaluation Plan's Which Layer Failed](../enterprise-rag-program/rag-evaluation-plan-template.md#which-layer-failed) table.

They connect: the gap in the weak inventory row is the cause of the failure in the trace. That is the usual shape. Most wrong answers a RAG pilot produces were decided months earlier, in a data inventory nobody read closely.

**Scenario (sanitized).** The same company as the other examples in this folder, after the encryption program. Its first RAG use case is a security-policy assistant: *"Engineers can ask questions about security standards and get accurate answers with citations."* The encryption program's TLS standard is one of the documents in the corpus. Names, dates, and numbers are illustrative.

---

## Part 1: One Inventory Row

### Weak

| Field | Entry |
|---|---|
| Source | Security wiki |
| Type | Wiki |
| Owner | Security team |
| Sensitivity | Internal |
| Access control model | Wiki permissions |
| Permission hygiene | Reviewed |
| Refresh | Daily |
| In scope | Yes |

### Why This Fails

Every cell is filled and almost none of them can be acted on. "Security team" is not a person anyone can ask to fix a page. "Wiki permissions" doesn't say whether permissions can be exported per page, which decides whether this source can ship at all. "Reviewed" has no date and no reviewer.

The blanks that matter are the ones the row doesn't have. Nothing says whether pages carry an effective date, so nobody knows that superseded standards sit next to current ones with nothing to tell them apart. Nothing records the wiki's internal vocabulary, so nobody notices that half the TLS pages call it "Keystone," the encryption program's codename. Nothing says what happens when a page is deleted or a space is locked down. This row will pass a readiness review and produce the wrong answer in Part 2.

### Better

| Field | Entry |
|---|---|
| ID | DS-03 |
| Source | Security Standards wiki space (`SECSTD`) |
| Type | Wiki |
| Shape | Unstructured |
| Path | Indexed |
| Owner | Priya N., Security Architecture (escalation: Director, Security Architecture) |
| Sensitivity | Internal; 6 pages Confidential (incident write-ups) |
| Access control model | Space-level groups plus page restrictions. Exportable per page through the wiki API, including inherited restrictions |
| Permission hygiene | **Restricted**, 2026-03-04, reviewed by Priya N.: 6 incident pages were readable by all employees; moved under a restricted parent. Re-review after the move: reviewed, 2026-03-11 |
| Metadata available | Created and modified dates, author, labels: **native**. Status (draft or approved): **native** label, applied inconsistently. Effective date: **not native**; appears in page text on about 60% of standards, must be **derived**. Superseded flag: **manual**, does not exist today |
| Volume | 412 pages, 38 attachments (PDF) |
| Change rate | 10 to 20 page edits a week |
| Refresh | Hourly, through the wiki's change feed |
| Permission-change propagation | Target 1 hour. Page-restriction changes come through the change feed. Group membership changes do not; resolved at query time from the identity provider. **Tested** 2026-03-18 |
| Deletion propagation | Target 1 hour from the change feed, plus nightly reconciliation against the full page list. **Tested** 2026-03-18 |
| In scope | Yes, priority 1 |
| Notes | Effective dates missing on about 40% of standards (logged under R-01, source data quality, owner Priya N.; it will surface as stale answers, R-09). Internal codename "Keystone" means the TLS standard (glossary entry G-04). Draft pages excluded until the status label is applied consistently |

### Why This Works

Every cell answers a question someone will ask later, and two of them predict a failure before it happens. The metadata cell separates **native**, **derived**, and **manual**, which turns "we have metadata" into an engineering estimate, and it flags that this source cannot tell a current standard from a superseded one. The notes put that gap in the RAID log with an owner. The codename is in the glossary before anyone asks about Keystone. The permission cells say how each kind of change reaches the index, and that it was tested, with a date.

---

## Part 2: One Wrong Answer, Traced

**The question,** from a platform engineer during the pilot:

> "Does Keystone allow TLS 1.1 for internal service-to-service traffic?"

**The answer the system gave:** "Yes. Internal service-to-service traffic may use TLS 1.1 until migration is complete," citing *TLS Standard v1 (2025)*.

**The right answer:** No. *TLS Standard v2*, in force since 2026-01-15, requires TLS 1.2 or later for all traffic, internal included.

### Weak Trace

> **Issue:** Model hallucinated the TLS answer.
> **Fix:** Added "always use the most recent policy" to the system prompt.
> **Owner:** AI engineering.

### Why This Fails

It blames the layer people reach for first, and it's wrong on the facts. The model didn't hallucinate: it answered faithfully from the document it was given. The prompt fix asks the model to judge which document is newer, using information the documents don't reliably carry, so it fixes nothing and hides the real problem. The owner is the team that can't fix the cause. The same failure will come back with the next superseded standard.

### Better Trace

Worked through the [Which Layer Failed](../enterprise-rag-program/rag-evaluation-plan-template.md#which-layer-failed) table, using the per-question retrieval log:

| Step | Question | Finding |
|---|---|---|
| 0 | Routed to the right source and path? | Yes. Security Standards wiki, documents only |
| 1 | Evidence in the corpus? | Yes. *TLS Standard v2* is indexed |
| 2 | Ingested, parsed, chunked, and tagged correctly? | **No.** v2's effective date is in a table in the page header, which the parser drops. v1 and v2 both carry no effective date and no superseded flag |
| 3 | Did retrieval find it? | Yes. Keyword search matched "Keystone" through glossary entry G-04; vector search found both versions. v2's chunk was candidate 4 |
| 4 | Ranked high enough to be kept? | Partly. The reranker put v1 first (its wording, "internal service-to-service," matches the question exactly) and v2 third |
| 5 | Made it into the context? A stale version instead? | **Both versions in context, v1 first**, with nothing marking which was in force |
| 6 | Given the right evidence, did the model use it correctly? | The model was given two contradictory standards and no way to tell which applied. It picked the first. That is a reasonable reading of bad evidence, not a reasoning failure |

**Root cause:** Step 2. Missing effective-date metadata, caused by a parser that drops header tables. Step 5 is where it surfaced.

**Classified as:** step 2, an ingestion and metadata gap (seeded as R-01, already logged from the inventory), which surfaced as stale content (R-09). Not a model failure.

**Fixes, each with its owner:**

| Fix | Owner | Due |
|---|---|---|
| Parser keeps header tables; effective date extracted and stored on every chunk of this source | Data engineering | 2026-04-10 |
| Superseded versions marked with a manual flag, then excluded from retrieval by a metadata filter (applied inside the search, not afterward) | Priya N., source owner | 2026-04-17 |
| Eval set gains five old-versus-current questions for this source, including this one, tagged by type | QA | 2026-04-10 |
| Superseded-retrieval rate for this source added to the pilot dashboard | AI engineering | 2026-04-10 |

### Why This Works

It finds the layer that failed and gives the fix to the people who can make it. Step 6 is checked last and cleared on evidence, not assumed. The trace was only possible because the system logged which chunks were retrieved, how they ranked, and what went into the context. Without that log, "the model hallucinated" is the only story anyone can tell.

It also closes the loop to Part 1. The better inventory row had already flagged the missing effective dates as a risk. The trace shows what that risk looked like when it landed, which is the case for doing the inventory properly in Phase 0.

---

## The Pattern That Works

For an inventory row:

- Can a named person act on every cell?
- Does the metadata cell say what is native, what must be derived, and what someone has to add by hand?
- Does it say how deletions and permission changes reach the index, and when that was last tested?

For a failure trace:

- Was every layer before the model checked, with evidence, before the model was blamed?
- Does the fix go to the layer that failed and the owner who can change it?
- Did the failure become an eval question, so it can't quietly come back?

---

*Part of the [tpm-templates](https://github.com/ChefPlex/tpm-templates) repo. See the [Enterprise RAG Program](../enterprise-rag-program/) for the full framework and the [RAG Architecture Primer](../enterprise-rag-program/rag-architecture-primer.md) for the terms.*
