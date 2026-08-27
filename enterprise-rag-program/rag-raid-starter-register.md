# RAG RAID Starter Register

A pre-seeded Risks, Assumptions, Issues and Dependencies register for an enterprise RAG program. Load it at kickoff instead of discovering these one at a time over six months.

Operating discipline, scoring, and review cadence: [RAID Log Guide](../raid-log-guide.md). This file is the RAG-specific content, not a second methodology.

Every row below has been seen on real programs. Delete what genuinely does not apply, but delete it deliberately rather than by not reading it.

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
| R-09 | Content goes stale | High | High | Refresh pipelines, freshness SLOs, source ownership | Data lead | Freshness SLO missed |
| R-10 | Users do not trust the answers | High | Medium | Citations, visible failure modes, honest refusals | Product | Adoption flat after pilot |
| R-11 | Ownership unclear across workstreams | High | Medium | RACI, governance council, named owner per workstream | TPM | Any unowned workstream |
| R-12 | Model or prompt change regresses quality | High | High | Eval gates in CI blocking merge | AI lead | Any gate bypassed |
| R-13 | Permission changes do not propagate to the index | **Critical** | Medium | Propagation testing, freshness monitoring on ACLs | Data lead | Propagation window exceeded |
| R-14 | Deleted source documents remain retrievable | **Critical** | Medium | Deletion propagation tested and monitored | Data lead | Any occurrence |
| R-15 | Regulated data discovered mid-ingestion | High | Medium | Classification before ingestion, legal review per source | Data governance | Any unclassified regulated content |

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

Four rows are marked Critical rather than High: R-04, R-05, R-13, R-14. All four are unauthorized-access paths, and they share a property that separates them from the quality risks.

A retrieval quality problem produces a bad answer, which a user notices and reports. An access-control problem produces a *good* answer, delivered confidently, to someone who should never have seen it, and nothing in the user experience signals that anything went wrong. Nobody files a ticket.

That is why the escalation trigger on all four is a single occurrence rather than a threshold, and why the corresponding CI gate has no tolerance band.
