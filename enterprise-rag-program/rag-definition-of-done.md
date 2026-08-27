# RAG Definition of Done

The gate for calling an enterprise RAG platform production-ready. Ten dimensions, each with a named owner and a verifiable result.

The value of a written DoD is that it is agreed before anyone is under launch pressure. Deferring a dimension is legitimate; deferring it silently in week 22 is not. Record every deferral with an approver and a date.

## The Gate

### 1. Business

- [ ] Business owner signs off that the delivered capability is worth its run cost
- [ ] Measured improvement against the Phase 0 baseline is documented
- [ ] Ongoing cost is budgeted and owned

Owner: Business owner

### 2. Retrieval

- [ ] Recall@K meets target on the full eval set
- [ ] Precision meets target
- [ ] Performance verified across every in-scope data source, not just the largest

Owner: AI engineering lead

### 3. Generation

- [ ] Groundedness meets target
- [ ] Answer correctness meets target
- [ ] Citation accuracy meets target
- [ ] Refusal behavior correct on the unanswerable set

Owner: AI engineering lead

### 4. Security

- [ ] Identity and authorization validated end to end
- [ ] Permission-aware retrieval verified: no user can retrieve what they could not access directly
- [ ] Permission changes propagate to the index within the agreed window
- [ ] Encryption in transit and at rest confirmed
- [ ] Audit logging captures query, retrieved documents, and requesting identity
- [ ] Secrets management reviewed
- [ ] Model-provider data-handling terms reviewed and accepted

Owner: Security lead

### 5. Safety

- [ ] Direct prompt-injection testing complete, zero successes
- [ ] Indirect injection testing complete against poisoned documents in the corpus
- [ ] Jailbreak testing complete
- [ ] Cross-user leakage testing complete
- [ ] Red team exercise conducted and findings closed or accepted
- [ ] Abuse and misuse scenarios tested

Owner: Security lead

### 6. Reliability

- [ ] SLOs defined and met under expected peak load
- [ ] Load testing complete at projected launch volume plus headroom
- [ ] Graceful degradation verified when retrieval or the model is unavailable
- [ ] Rollback path tested

Owner: Platform lead

### 7. Operations

- [ ] Monitoring and alerting live
- [ ] Incident response runbook written and walked through
- [ ] On-call ownership named
- [ ] Escalation path documented for wrong or harmful answers
- [ ] Kill switch exists and has been tested

Owner: Platform lead

### 8. Quality

- [ ] Automated evals run in CI
- [ ] Regression gates block merges
- [ ] Eval set meets size and composition targets
- [ ] Judge validated against human scoring
- [ ] Process exists for adding production failures to the eval set

Owner: AI engineering lead plus QA

### 9. Governance

- [ ] Model approval process operating
- [ ] Data source approval process operating
- [ ] Use case approval process operating with risk tiers
- [ ] Governance council meeting on a defined cadence
- [ ] Change process defined for adding sources or models post-launch

Owner: Program manager

### 10. Adoption

- [ ] Pilot users show measurable improvement against baseline
- [ ] Training and onboarding materials exist
- [ ] Feedback channel live and monitored
- [ ] Content ownership named for every in-scope source
- [ ] Answer-quality owner named for after launch

Owner: TPM plus business owner

## Deferrals

| Dimension | What is deferred | Why | Risk accepted by | Date | Revisit |
|---|---|---|---|---|---|
| | | | | | |

## Sign-Off

| Name | Role | Dimensions owned | Signed | Date |
|---|---|---|---|---|
| | Executive sponsor | Business | | |
| | Security lead | Security, Safety | | |
| | AI engineering lead | Retrieval, Generation, Quality | | |
| | Platform lead | Reliability, Operations | | |
| | Program manager | Governance | | |
| | Business owner | Adoption | | |
