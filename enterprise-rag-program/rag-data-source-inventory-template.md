# RAG Data Source Inventory Template

The inventory the data workstream runs on. Owned by Data Engineering and Data Governance jointly, because half these columns are technical and half are policy.

Fill this before architecture is finalized. The access-control column in particular drives the retrieval design, and discovering in week 12 that a priority source has no machine-readable permission model is the most expensive way to learn it.

## Inventory

| ID | Source | Type | Owner | Sensitivity | Access control model | Volume | Change rate | Refresh | In scope | Notes |
|---|---|---|---|---|---|---|---|---|---|---|
| DS-01 | | | | | | | | | | |
| DS-02 | | | | | | | | | | |

Column guidance:

- **Type** - wiki, ticketing, file share, CRM, database, email, code repository, PDF archive
- **Sensitivity** - public, internal, confidential, restricted, regulated
- **Access control model** - the actual mechanism, not the aspiration. "Group-based ACL, exportable per document" is usable. "People just know" is not.
- **Change rate** - how often content changes, which sets the refresh requirement
- **Refresh** - real time, hourly, daily, weekly, static

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

**Content quality issues:** _______________ Duplicates, outdated documents, contradictions, drafts mixed with approved versions.

**Retention or deletion requirements:** _______________

**Cross-border or residency constraints:** _______________

**Deletion propagation.** When a document is deleted at source, how does it leave the index, and within what window?

_______________

## Readiness Gate

A source is ready for ingestion when all of these hold. Track partial readiness explicitly rather than ingesting and hoping.

- [ ] Owner named and engaged
- [ ] Sensitivity classified
- [ ] Permission model machine-readable and resolvable per document
- [ ] Extraction path proven on a representative sample
- [ ] Refresh mechanism defined and costed
- [ ] Deletion propagation defined
- [ ] Content quality assessed, known issues logged as risks
- [ ] Legal and privacy review complete for regulated content

## Common Findings

Log these as risks or issues when found rather than absorbing them silently:

- **The wiki has three versions of the same policy.** Content governance problem. Retrieval will faithfully return the wrong one.
- **Permissions live in a system that cannot export them.** Blocks permission-aware retrieval entirely.
- **A third of the corpus is scanned PDFs.** OCR quality now sets retrieval quality.
- **Nobody has owned the source since a reorg.** No one can approve inclusion or fix content.
- **The source contains regulated data nobody flagged.** Discovered during ingestion, which is the worst time.
