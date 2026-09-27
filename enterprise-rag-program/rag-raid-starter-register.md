# RAG RAID Starter Register

A pre-seeded Risks, Assumptions, Issues and Dependencies register for an enterprise RAG program. Load it at kickoff instead of discovering these one at a time over six months.

Operating discipline, scoring, and review cadence: [RAID Log Guide](../raid-log-guide.md). This file is the RAG-specific content, not a second methodology.

Every row below has been seen on real programs. Delete what genuinely doesn't apply, but delete it deliberately rather than by not reading it.

## Risks

| ID | Risk | Impact | Likelihood | Mitigation | Owner | Trigger to escalate |
|---|---|---|---|---|---|---|
| R-01 | Source data quality is worse than assumed | High | High | Data quality program, source ownership, sample audit before ingestion | Data lead | Sample audit finds > 10% unusable |
| R-02 | Chunking strategy degrades retrieval | Medium | Medium | Retrieval evals before scale-out, ADR with revisit date | AI lead | Recall below target on any source |
| R-03 | Answers not grounded in retrieved content | High | Medium | Grounding requirement, citation enforcement, eval gate | AI lead | Groundedness below target |
| R-04 | Unauthorized retrieval | **Critical** | Medium | Permission-aware retrieval, pre-model filtering, boundary tests in CI | Security lead | Any single occurrence |
| R-05 | Prompt injection, direct or indirect | **Critical** | High | Threat model, red team, injection corpus in CI | Security lead | Any single success |
| R-06 | Model provider dependency | Medium | Medium | Abstraction layer, second provider evaluated | AI lead | Provider terms or pricing change |
| R-07 | Token cost grows past budget | High | High | Budget alerts, caching, model routing, cost per query gate | Platform lead | Cost per query up > 20% |
| R-08 | Latency unacceptable to users | Medium | Medium | Caching, routing, reranking budget | Platform lead | P95 above SLO |
| R-09 | Content goes stale: the index lags source changes, so answers cite superseded content | High | High | Refresh pipelines, freshness SLO per source, stale-document age monitored, source ownership | Data lead | Freshness SLO missed |
| R-10 | Users do not trust the answers | High | Medium | Citations, visible failure modes, honest refusals | Product | Adoption flat after pilot |
| R-11 | Ownership unclear across workstreams | High | Medium | RACI, governance council, named owner per workstream | TPM | Any unowned workstream |
| R-12 | Model or prompt change regresses quality | High | High | Eval gates in CI blocking merge | AI lead | Any gate bypassed |
| R-13 | Permission changes do not propagate to the index | **Critical** | Medium | Propagation testing, freshness monitoring on ACLs | Data lead | Propagation window exceeded |
| R-14 | Deleted or revoked source documents remain retrievable from the index or caches | **Critical** | Medium | Deletion propagation window per source in the inventory, tested and monitored, caches included | Data lead | Any occurrence |
| R-15 | Regulated data discovered mid-ingestion | High | Medium | Classification before ingestion, legal review per source | Data governance | Any unclassified regulated content |
| R-16 | Oversharing at source: permission-aware retrieval faithfully enforces permissions that were already too broad | **Critical** | High | Phase 0/1 permission review, per-source hygiene status in the inventory, interim restriction until remediated | Oversharing remediation owner | Any source ingested as "not reviewed" |
| R-17 | LLM judge drifts from human judgment after a judge model, rubric, or corpus change | High | Medium | Judge calibrated against human labels on this corpus, agreement reported, re-calibrated on any change | AI lead | Judge-human agreement drops below the recorded baseline |

### RAG Engineering Failure Points

Seven starter risks for where a RAG pipeline loses the right answer. They follow the seven failure points named by Barnett et al. from three deployed systems ([arXiv 2401.05856](https://arxiv.org/abs/2401.05856)). Each is a separate risk because each has a different fix and a different owner. Use them to classify pilot and production misses as well as to seed the log.

| ID | Risk | Impact | Likelihood | Mitigation | Owner | Trigger to escalate |
|---|---|---|---|---|---|---|
| R-18 | Missing content: the answer is not in the corpus, and the system answers anyway | High | High | Unanswerable questions in the eval set, refusal correctness gate, content-gap log fed to source owners | AI lead plus Business owner | Refusal correctness below target |
| R-19 | Missed the top-ranked documents: the answer is in the corpus but not ranked high enough to be returned | High | Medium | Recall@K per source, reranking, retrieval evals before scale-out | AI lead | Recall below target on any source |
| R-20 | Not in context: the document was retrieved but dropped when the context was assembled | Medium | Medium | Log retrieved versus included documents, eval context assembly separately | AI lead | Retrieved-but-dropped rate above threshold on failed answers |
| R-21 | Not extracted: the answer was in the context and the model did not use it, often because of noise or contradiction | High | Medium | Groundedness and nugget coverage evals, fewer and cleaner chunks | AI lead | Nugget coverage below target |
| R-22 | Wrong format: the answer ignores a required format such as a table or list | Low | Medium | Format checks in the eval suite | AI lead | Format failures above threshold |
| R-23 | Incorrect specificity: the answer is too general or too specific for the question | Medium | Medium | Real user questions in the eval set, SME review of answer level | Product | Recurring in pilot feedback |
| R-24 | Incomplete: the answer is correct but leaves out information that was available | Medium | High | Nugget coverage as a gated metric | AI lead | Nugget coverage below target |

## Assumptions

| ID | Assumption | If wrong | Validate by | Owner |
|---|---|---|---|---|
| A-01 | Priority sources have machine-readable permissions | Cannot ship permission-aware, scope changes | M2 | Data lead |
| A-02 | Content is authoritative and non-contradictory | Retrieval faithfully returns wrong answers | M2 | Business owner |
| A-03 | Users will accept citations as sufficient transparency | Trust and adoption suffer | Pilot | Product |
| A-04 | Projected query volume is roughly correct | Cost and capacity models wrong | Pilot | Platform lead |
| A-05 | Provider data-handling terms are acceptable to legal | Architecture change, possible self-hosting | M1 | Legal |
| A-06 | Subject matter experts are available to build the eval set | Eval set is engineer-written and misleading | M3 | QA |

## Issues

| ID | Issue | Impact | Owner | Target | Status |
|---|---|---|---|---|---|
| | | | | | |

## Dependencies

| ID | Dependency | Needed by | Provider | Status | Risk if late |
|---|---|---|---|---|---|
| D-01 | Source system access and service accounts | M2 | Source owners | | Ingestion blocked |
| D-02 | Permission model export per source | M2 | IAM team | | Cannot ship safely |
| D-03 | Model provider contract and data terms | M1 | Procurement, Legal | | Architecture blocked |
| D-04 | Security review capacity | M1, M5 | Security | | Milestone slip |
| D-05 | Subject matter expert time for eval set | M3 | Business owner | | Eval set invalid |
| D-06 | Pilot user group committed | M6 | Business owner | | No validation |

## Notes on the Critical Rows

Five rows are marked Critical rather than High: R-04, R-05, R-13, R-14, R-16. All five are unauthorized-access paths, and they share a property that separates them from the quality risks.

A retrieval quality problem produces a bad answer, which a user notices and reports. An access-control problem produces a *good* answer, delivered confidently, to someone who should never have seen it, and nothing in the user experience signals that anything went wrong. Nobody files a ticket.

That's why the escalation trigger on all five is a single occurrence rather than a threshold, and why the corresponding CI gate has no tolerance band.

R-16 is the one most programs miss, because nothing is broken. Permission-aware retrieval is necessary and not sufficient: it inherits whatever the source systems grant. Microsoft's Copilot deployment guidance puts "Remediate oversharing" first of its three pillars for this reason ([Microsoft Learn](https://learn.microsoft.com/en-us/microsoft-365/copilot/secure-govern-copilot-foundational-deployment-guidance)). The security detail is in the [Enterprise RAG Security Playbook](https://github.com/ChefPlex/security-program-playbooks/blob/main/enterprise-rag-security/rag-security-playbook.md).
