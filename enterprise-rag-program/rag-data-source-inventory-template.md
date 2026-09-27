# RAG Data Source Inventory Template

The inventory the data workstream runs on. Owned by Data Engineering and Data Governance jointly, because half these columns are technical and half are policy.

Fill this before architecture is finalized. The access-control column in particular drives the retrieval design, and discovering in week 12 that a priority source has no machine-readable permission model is the most expensive way to learn it.

## Inventory

| ID | Source | Type | Owner | Sensitivity | Access control model | Permission hygiene | Volume | Change rate | Refresh | Deletion propagation | In scope | Notes |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| DS-01 | | | | | | not reviewed | | | | | | |
| DS-02 | | | | | | not reviewed | | | | | | |

Column guidance:

- **Type** - wiki, ticketing, file share, CRM, database, email, code repository, PDF archive
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
- [ ] Permission model machine-readable and resolvable per document
- [ ] Extraction path proven on a representative sample
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
