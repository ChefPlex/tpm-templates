# RAG Milestone Exit Criteria

Exit criteria for M0 through M7. A milestone is met when every box is checked or the gap is explicitly accepted by the named approver.

The point of written exit criteria is to make "are we done with this phase" a question with an answer rather than an opinion.

## M0 - Program Approved

- [ ] Charter signed by executive sponsor
- [ ] Business problem and initial use case defined and narrow
- [ ] Baseline metrics measured and recorded
- [ ] Success targets set with numbers and owners
- [ ] Budget committed
- [ ] All seven workstreams have a named owner
- [ ] Risk tier assigned to the initial use case

Approver: Executive sponsor

**Most common failure:** baseline not measured, because it felt slow. Without it, every later claim of improvement is an assertion.

## M1 - Architecture Approved

- [ ] Architecture approved by governance council
- [ ] Security model and trust boundary approved
- [ ] ADRs recorded for chunking, embedding model, vector store, reranking, model selection, citation format
- [ ] Permission-aware retrieval design reviewed and accepted by security
- [ ] Cost model built with projected cost per query and per user
- [ ] Model-provider data-handling terms reviewed

Approver: Governance council plus security lead

**Most common failure:** embedding model chosen without an ADR. Changing it later means reindexing the entire corpus.

## M2 - Data Ready

- [ ] Priority sources ingested
- [ ] Permission model verified per source, resolvable per document at query time
- [ ] Permission change propagation tested end to end
- [ ] Deletion propagation tested
- [ ] Freshness pipeline running and monitored
- [ ] Content quality issues logged as risks with owners
- [ ] Legal and privacy review complete for regulated sources

Approver: Data lead plus security lead

**Most common failure:** ingestion declared complete while permission propagation is untested. The system works and leaks.

## M3 - RAG MVP

- [ ] End-to-end question to cited answer working against the real corpus
- [ ] Citations resolve to real, correct source documents
- [ ] Permission filtering active in the live path, not planned
- [ ] Eval set built to the minimum question count
- [ ] Baseline eval run recorded as the reference point

Approver: AI engineering lead

**Most common failure:** demo built against a clean subset. Run it against the messy real corpus or the number means nothing.

## M4 - Quality Gate

- [ ] Retrieval targets met on the full eval set
- [ ] Generation targets met
- [ ] Refusal behavior correct on unanswerable questions
- [ ] Permission-boundary questions correctly refused
- [ ] Evals running in CI with regression gates active
- [ ] Judge validated against human scoring on a sample

Approver: AI engineering lead plus QA

**Most common failure:** targets met on an eval set written by the engineers. Questions must come from real users.

## M5 - Production Ready

- [ ] SLOs met under expected peak load
- [ ] Observability live: latency, cost, retrieval quality, error rates
- [ ] Cost controls active with budget alerts
- [ ] Security testing complete including direct and indirect injection
- [ ] Red team findings closed or formally accepted
- [ ] Incident response runbook written and walked through
- [ ] Kill switch tested
- [ ] Rollback tested

Approver: Platform lead plus security lead

**Most common failure:** indirect injection untested. Direct injection gets tested because it is obvious; poisoned documents inside the corpus do not.

## M6 - Pilot Complete

- [ ] Real users in a real workflow for a defined period
- [ ] Measured improvement against the M0 baseline
- [ ] Feedback channel operating with responses acted on
- [ ] Production failures fed back into the eval set
- [ ] Support and escalation path exercised at least once
- [ ] Business owner confirms the value is real

Approver: Business owner plus TPM

**Most common failure:** pilot with friendly users who work around problems instead of reporting them.

## M7 - General Availability

- [ ] Full [Definition of Done](rag-definition-of-done.md) satisfied or deferrals formally accepted
- [ ] Operating model live with named owners
- [ ] Governance council operating on cadence
- [ ] Training and onboarding available
- [ ] Answer-quality owner named for steady state
- [ ] Change process defined for new sources and models
- [ ] Run cost budgeted and owned

Approver: Executive sponsor plus governance council

**Most common failure:** launch without a named owner for answer quality. Content drifts, answers degrade, and nobody is accountable.

## Milestone Record

| Milestone | Target date | Actual | Approver | Deferrals accepted |
|---|---|---|---|---|
| M0 | | | | |
| M1 | | | | |
| M2 | | | | |
| M3 | | | | |
| M4 | | | | |
| M5 | | | | |
| M6 | | | | |
| M7 | | | | |
