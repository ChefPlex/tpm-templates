# Enterprise RAG Program Playbook

A phase-based playbook for running Retrieval-Augmented Generation as an enterprise program rather than an AI experiment.

RAG is an architecture. The thing you are actually running is a platform program with a data workstream, a security workstream, and an adoption problem. This playbook is written for the TPM who has been handed "we want AI over our own documents" and needs it to survive contact with security review, a real user base, and a budget conversation.

## The Framing That Matters

Do not charter this as:

> "Implement RAG."

Charter it as:

> "Build an enterprise knowledge platform that securely connects authorized organizational data to AI models and returns measurable, grounded answers to employees and applications."

RAG is the enabling architecture, not the goal. That distinction is what turns an interesting AI project into a program with business outcomes, architecture standards, security controls, named ownership, and reusable infrastructure. It is also the difference between a demo that impresses an executive once and a platform other teams can build on.

The single most common failure is treating this as an AI engineering project. It is equally a data, security, platform, product, and operations program. Staff it that way or expect to discover the missing workstreams at the worst possible time.

## Phases

| Phase | Duration | Primary outcome |
|---|---:|---|
| 0. Program Definition | Weeks 1-2 | Business case, scope, ownership, success metrics |
| 1. Architecture and Governance | Weeks 2-5 | Approved architecture and security model |
| 2. Data Foundation | Weeks 3-8 | Content ingested, normalized, permission-aware |
| 3. RAG MVP | Weeks 5-10 | End-to-end retrieval and answering working |
| 4. Quality and Evals | Weeks 8-14 | Measurable retrieval and answer quality |
| 5. Production Platform | Weeks 10-17 | Scalable, observable, secured service |
| 6. Pilot | Weeks 15-20 | Real users, real workflow validation |
| 7. Enterprise Launch | Weeks 20-24 | Production release and operating model |
| 8. Scale | Ongoing | More sources, applications, models, users |

Phases overlap on purpose. Data foundation starts before architecture is fully approved because data discovery always takes longer than anyone plans, and evals start before the MVP is finished because writing the eval set is how you find out what "correct" means.

## Phase 0 - Program Definition

Weeks 1-2. **Do not start by selecting a vector database.** Start with the business problem.

Pick one high-value use case, narrow enough to actually finish:

> "Employees can ask questions about security policies and get accurate answers with citations."

> "Support engineers can retrieve troubleshooting information across the wiki, the ticket system, and product documentation."

Then define what success means numerically, before anyone writes code.

**Baseline the current state.** You cannot claim improvement without it, and the baseline is usually easy to get by asking twenty people and timing them.

```text
Average information search time:   18 minutes
Correct answer rate:               72%
Escalation rate:                   31%
```

**Set program targets.** These become the executive KPIs and they belong in the charter.

```text
Search time:              < 2 minutes
Answer correctness:       > 90%
Grounded responses:       > 95%
Citation accuracy:        > 98%
Unauthorized retrieval:   0
User satisfaction:        > 4.2 / 5
```

Note the one target that is not a percentage. Unauthorized retrieval is zero or the program is not shippable, and treating it as a rate you optimize is how programs end up negotiating about acceptable leakage in week 19.

Deliverable: [RAG Program Charter](rag-program-charter-template.md).

## The Seven Workstreams

```text
                       ENTERPRISE RAG PROGRAM

                              PROGRAM
                                 |
        +-----------+------------+------------+--------------+
        |           |            |            |              |
        v           v            v            v              v
     Product      Data         AI/ML       Platform       Security
        |           |            |            |              |
        +-----------+------+-----+------------+--------------+
                           |
                   +-------+-------+
                   v               v
               Evaluation      Adoption and
               and Quality      Operations
```

### 1. Product and Use Cases

Owner: Product Manager plus TPM.

Answer these before anything is built:

- Who is using this, and what questions are they actually asking?
- Where does the authoritative answer live today?
- What happens if the answer is wrong? (This determines the risk tier.)
- What actions, if any, can the system take on the user's behalf?

Deliverable: [Use Case Catalog](rag-use-case-catalog-template.md).

### 2. Data Foundation

Owner: Data Engineering plus Data Governance.

Usually the longest pole, and almost never the one that gets staffed first. Industry research consistently attributes the majority of AI project failures to data quality rather than model performance, and enterprise document estates are worse than anyone believes until they are inventoried.

The work is: inventory sources, resolve ownership, classify sensitivity, capture the access-control model for each source, build ingestion, then keep it fresh. Freshness is a permanent operating cost, not a one-time migration.

Deliverable: [Data Source Inventory](rag-data-source-inventory-template.md).

### 3. RAG and AI Engineering

Owner: AI and ML Engineering.

The pipeline is ingest, chunk, embed, index, retrieve, rerank, assemble prompt, generate, cite. The major decisions worth an ADR each:

| Decision | Why it needs a record |
|---|---|
| Chunking strategy and size | Silently determines retrieval quality and is expensive to change after indexing |
| Embedding model | Changing it means reindexing the entire corpus |
| Vector store | Operational burden, cost curve, and permission-filtering capability vary enormously |
| Reranking | Adds latency and cost, materially improves precision |
| Model selection and routing | Provider dependency, cost per query, data-handling terms |
| Citation format | Cheap to design in, painful to retrofit, and it is what users trust |

Use the existing [ADR Template](../adr-template.md) for each. The reindexing cost of an unrecorded embedding decision is the most common expensive surprise in this program.

### 4. Enterprise Security

Owner: Security Engineering plus the security TPM.

Make it a first-class workstream from week one, not a review gate at week 18. The controls, the trust boundary, and the prompt-injection threat model live in the companion playbook:

**[Enterprise RAG Security Playbook](https://github.com/ChefPlex/security-program-playbooks/tree/main/enterprise-rag-security)**

The one rule to carry into every architecture conversation:

> The system can never retrieve information the requesting user could not have accessed directly.

Authorization filtering happens before content reaches the model, never after. Post-filtering a response that was generated from unauthorized content is not a control, it is a hope.

### 5. Evaluation and Quality

Owner: AI Engineering plus QA.

You cannot manage what you cannot measure, and "it seems better" does not survive a steering committee. Retrieval and generation are measured separately because they fail separately, and an answer can be wrong for two completely different reasons that have two completely different fixes.

Deliverable: [Evaluation Plan](rag-evaluation-plan-template.md).

### 6. Platform Engineering

Owner: Platform and SRE.

Serving, scaling, caching, cost controls, model routing, observability, incident response. Token spend is a production cost line that grows with adoption, so cost controls belong in the architecture rather than in a later optimization phase.

### 7. Adoption and Operations

Owner: TPM plus the business owner.

The workstream that gets cut and then decides whether any of the rest mattered. Training, feedback channels, content ownership, escalation paths, and a named owner for answer quality after launch.

## Governance

Stand up an AI Platform Governance Council with representation from AI Engineering, Security, Privacy, Legal, Data Governance, Enterprise Architecture, Product, and SRE.

They approve: new data sources, new models, high-risk use cases, sensitive integrations, and any autonomous capability.

**Do not route every change through a committee.** Use risk tiers so low-risk work moves at engineering speed and the council spends its attention where the blast radius justifies it.

| Tier | Example | Control posture |
|---|---|---|
| 1 - Low | Internal documentation search | Standard review, team ships |
| 2 - Moderate | Engineering or support assistant | Eval gates, security sign-off |
| 3 - High | Customer-facing answers | Council approval, red team, human escalation path |
| 4 - Critical | Financial, health, security decisions, or autonomous action | Full council, external review, human in the loop, kill switch |

Tier is set by consequence of a wrong answer, not by technical complexity. A simple system answering compliance questions outranks a sophisticated one answering cafeteria questions.

## Timeline

An illustrative 24-week shape for a first enterprise deployment. Adjust for data estate size, not for optimism.

```text
Weeks  1-2    Program definition, charter, baseline metrics
Weeks  2-5    Architecture, security model, governance stand-up
Weeks  3-8    Data inventory, ingestion, permission mapping
Weeks  5-10   RAG MVP end to end
Weeks  8-14   Eval harness, quality gates, CI integration
Weeks 10-17   Production platform, observability, cost controls
Weeks 15-20   Pilot with real users
Weeks 20-24   Enterprise launch and operating model handoff
```

## Milestones

| ID | Milestone | Exit criteria |
|---|---|---|
| M0 | Program approved | Charter signed, sponsor named, budget committed, baseline captured |
| M1 | Architecture approved | Architecture and security model approved by council, ADRs recorded |
| M2 | Data ready | Priority sources ingested, permission model verified, freshness pipeline running |
| M3 | RAG MVP | End-to-end answering with citations against real corpus |
| M4 | Quality gate | Retrieval and generation targets met on the eval set, evals running in CI |
| M5 | Production ready | SLOs met under load, observability live, cost controls active, security testing complete |
| M6 | Pilot complete | Real users, measured improvement against baseline, feedback loop operating |
| M7 | General availability | Launched, operating model live, ownership and escalation named |

Full exit criteria per milestone: [Milestone Exit Criteria](rag-milestone-exit-criteria.md).

## Program Risks

Load these into the RAID log at kickoff rather than discovering them one at a time. Format and operating discipline: [RAID Log Guide](../raid-log-guide.md). Pre-seeded register: [RAG RAID Starter](rag-raid-starter-register.md).

| Risk | Impact | Mitigation |
|---|---|---|
| Poor source data quality | High | Data quality program, source ownership |
| Bad chunking strategy | Medium | Retrieval evals before scale-out |
| Hallucinated answers | High | Grounding requirement, citation enforcement, evals |
| Unauthorized retrieval | Critical | Permission-aware retrieval, pre-model filtering |
| Prompt injection | Critical | Threat model, red teaming, indirect injection tests |
| Provider dependency | Medium | Model abstraction layer |
| Runaway token cost | High | Budget controls, caching, model routing |
| Slow responses | Medium | Caching, routing, reranking budget |
| Stale content | High | Refresh pipelines, freshness SLOs |
| Low user trust | High | Citations, transparency, visible failure modes |
| Unclear ownership | High | RACI, governance council |
| Model regression | High | Eval gates in CI |

## Definition of Done

The platform is production-ready when all ten hold. Full checklist: [Definition of Done](rag-definition-of-done.md).

Business value signed off. Retrieval targets met. Generation targets met. Identity, authorization, data protection, and audit validated. Injection and abuse testing complete. SLOs met under expected load. Monitoring, incident response, and ownership defined. Automated evals running in CI. Model, data, and use-case approval process operating. Pilot users show measurable improvement.

## Related

- [Program Charter Template](../program-charter-template.md) - the general-purpose charter this program's charter extends
- [Program Phases Playbook](../program-phases-playbook.md) - the phase model this follows
- [RAID Log Guide](../raid-log-guide.md) - risk operating discipline
- [ADR Template](../adr-template.md) - for the architecture decisions listed above
- [Enterprise RAG Security Playbook](https://github.com/ChefPlex/security-program-playbooks/tree/main/enterprise-rag-security) - the security workstream in full
