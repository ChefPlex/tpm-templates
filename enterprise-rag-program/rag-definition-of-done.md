# RAG Definition of Done

The gate for calling an enterprise RAG platform production-ready. Eleven dimensions, each with a named owner and a verifiable result.

The value of a written DoD is that it's agreed before anyone is under launch pressure. Deferring a dimension is legitimate; deferring it silently in week 22 isn't. Record every deferral with an approver and a date.

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
- [ ] Permission-aware retrieval verified: no user can retrieve what they couldn't access directly
- [ ] Permission changes propagate to the index within the agreed window
- [ ] Encryption in transit and at rest confirmed
- [ ] Audit logging captures query, retrieved documents, and requesting identity
- [ ] Secrets management reviewed
- [ ] Model-provider data-handling terms reviewed and accepted
- [ ] Every in-scope source marked reviewed, remediated, or restricted for oversharing in the [Data Source Inventory](rag-data-source-inventory-template.md)
- [ ] Every item in the security workstream's GA sign-off checklist is checked or formally accepted: [Enterprise RAG Security Playbook, Sign-Off](https://github.com/ChefPlex/security-program-playbooks/blob/main/enterprise-rag-security/rag-security-playbook.md#sign-off)

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
- [ ] Judge validated against human scoring on this corpus, with judge-human and human-human agreement recorded
- [ ] Held-out eval set passes at the same level as the tuned set
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

### 11. Operational Validation

Pre-launch eval scores are necessary and not sufficient. Barnett et al., from three deployed RAG systems, conclude that "validation of a RAG system is only feasible during operation" ([arXiv 2401.05856](https://arxiv.org/abs/2401.05856)). This dimension is the gate that proves it in operation.

- [ ] Pilot ran on live traffic from real users for a defined period, not a replayed or curated set
- [ ] Failure-point review completed on the pilot's bad or refused answers: each classified by where it failed (content missing from the corpus, not retrieved or ranked too low, retrieved but not in context, in context but not used, wrong format, wrong level of detail, incomplete)
- [ ] Each failure class above a set threshold has an owner and a fix or an accepted risk in the RAID log
- [ ] Failures from the pilot added to the eval set
- [ ] Production monitoring can detect the same failure classes after launch

Owner: AI engineering lead plus TPM

## Deferrals

| Dimension | What is deferred | Why | Risk accepted by | Date | Revisit |
|---|---|---|---|---|---|
| | | | | | |

## Sign-Off

| Name | Role | Dimensions owned | Signed | Date |
|---|---|---|---|---|
| | Executive sponsor | Business | | |
| | Security lead | Security, Safety | | |
| | AI engineering lead | Retrieval, Generation, Quality, Operational validation | | |
| | Platform lead | Reliability, Operations | | |
| | Program manager | Governance | | |
| | Business owner | Adoption | | |
