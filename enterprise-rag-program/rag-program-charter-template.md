# RAG Program Charter Template

Extends the general [Program Charter Template](../program-charter-template.md) with the sections a retrieval program needs and a normal program does not. Use both: this one does not repeat the stakeholder, budget, and governance sections the base charter already covers.

Fill every field. A blank in this document is a decision someone will make for you later, usually in week 19 and usually badly.

---

## 1. Program Name and Framing

**Program name:** _______________

**One-sentence definition.** Write the platform outcome, not the technology.

> Build an enterprise knowledge platform that securely connects authorized organizational data to AI models and returns measurable, grounded answers to _______________.

**Explicitly NOT this program:** "Implement RAG." If the charter says that, rewrite it.

## 2. Business Problem

What is broken today, in the words of the people it is broken for.

**Problem statement:** _______________

**Who feels it:** _______________

**What it costs today:** _______________

## 3. Sponsor and Ownership

| Role | Name | Accountable for |
|---|---|---|
| Executive sponsor | | Funding, air cover, tier 3/4 approval |
| Business owner | | Value realization, answer quality after launch |
| Program manager / TPM | | Delivery, risk, cross-workstream alignment |
| AI engineering lead | | Retrieval and generation quality |
| Data lead | | Source availability, freshness, permission fidelity |
| Security lead | | Trust boundary, injection posture, sign-off |
| Platform lead | | SLOs, cost, observability |

An unnamed row is an unowned workstream.

## 4. Initial Use Case

One. Not three.

**Use case:** _______________

**Users:** _______________

**Authoritative sources:** _______________

**Consequence of a wrong answer:** _______________

**Risk tier (1-4):** _______________

Risk tier is set by the consequence line above, not by technical complexity.

## 5. Baseline Metrics

Measured before build starts. If you cannot measure it, say so explicitly rather than leaving it blank.

| Metric | Current baseline | How measured | Date |
|---|---|---|---|
| Average time to find an answer | | | |
| Correct answer rate | | | |
| Escalation rate | | | |
| Volume of questions per week | | | |

## 6. Success Targets

These become the executive KPIs. Every one needs a number and an owner.

| Metric | Target | Owner |
|---|---|---|
| Time to answer | | |
| Answer correctness | | |
| Grounded response rate | | |
| Citation accuracy | | |
| Unauthorized retrieval events | **0** | Security lead |
| User satisfaction | | |

Unauthorized retrieval is zero, not a rate to optimize. If it is written as a percentage, the program will eventually negotiate about acceptable leakage.

## 7. Data Scope

**In scope, priority order:**

| Source | Owner | Sensitivity | Access model | Refresh need |
|---|---|---|---|---|
| | | | | |

**Explicitly out of scope for this phase:** _______________

Out-of-scope data sources are the most common source of scope creep here, because every stakeholder has one more system they want included.

## 8. Actions and Autonomy

Can the system do anything, or only answer?

- [ ] Answer only, read-only retrieval
- [ ] Answer plus suggest an action a human executes
- [ ] Answer plus execute a bounded, reversible action
- [ ] Answer plus execute a consequential action

Anything below the first box requires a documented human-approval path and moves the risk tier up.

## 9. Non-Goals

What this program is not doing, written down so it can be pointed at.

- _______________
- _______________

## 10. Key Architecture Decisions Pending

Each becomes an ADR. Reindexing cost is the reason the first two matter more than they look.

| Decision | Owner | Needed by | ADR |
|---|---|---|---|
| Chunking strategy | | | |
| Embedding model | | | |
| Vector store | | | |
| Reranking approach | | | |
| Model selection and routing | | | |
| Citation format | | | |

## 11. Definition of Done

Reference: [Definition of Done](rag-definition-of-done.md). Note any dimension this program is explicitly deferring, and who approved the deferral.

## 12. Approval

| Name | Role | Decision | Date |
|---|---|---|---|
| | Executive sponsor | | |
| | Security lead | | |
| | Data governance | | |
