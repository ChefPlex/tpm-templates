# Program Charter Template

A program charter is the founding document for any serious initiative. It exists to answer the questions every stakeholder is going to ask anyway - why are we doing this, what exactly are we doing, who is responsible, and how will we know when we are done. Getting this on paper at the start saves a lot of painful conversations later.

Fill in every section. If you cannot fill in a section, that is useful information - it means you are not ready to start yet.

---

## Document Control

| Field | Detail |
|-------|--------|
| Program Name | |
| Version | 1.0 |
| Status | Draft / In Review / Approved |
| Date | |
| TPM | |
| Product / Program Owner | |
| Executive Sponsor | |

### Approvals

| Role | Name | Date Approved |
|------|------|--------------|
| Executive Sponsor | | |
| Engineering Leader | | |
| Product / Program Owner | | |
| TPM Lead | | |

### Contributors

| Name | Role | Contribution |
|------|------|-------------|
| | | |

### Change Log

| Version | Date | Author | Change |
|---------|------|--------|--------|
| 1.0 | | | Initial draft |

---

## 1. Why Are We Doing This

### Problem Statement

What is the problem, gap, or risk this program addresses? Be specific. A vague problem statement produces a vague program.

> Example: "Our encryption coverage across platform services stands at 10%. Any service transmitting data without encryption in transit represents a direct customer trust risk and a compliance exposure. Left unaddressed, this gap grows as we add services."

### Strategic Alignment

How does this program connect to the organization's current priorities? What happens if we do not do it?

> Alignment: [Reference to annual plan, OKR, compliance deadline, or strategic initiative]
> Cost of inaction: [What gets worse, more expensive, or more risky if we delay]

---

## 2. What We Are Building

### Program Overview

Two to four sentences describing what this program does and how it addresses the problem above.

### Objectives

List 3-5 specific, measurable objectives. Avoid vague language like "improve" or "enhance" without a number attached.

1. [Objective 1 - specific and measurable]
2. [Objective 2 - specific and measurable]
3. [Objective 3 - specific and measurable]

### Definition of Done

This is the contract. What does "complete" mean for this program? Be precise enough that a reasonable person could look at the finished work and say yes or no.

| Success Criterion | Measurement | Target |
|------------------|-------------|--------|
| [Criterion 1] | [How measured] | [Target value or date] |
| [Criterion 2] | [How measured] | [Target value or date] |
| [Criterion 3] | [How measured] | [Target value or date] |

**Business Metrics:** What needle moves in the business as a result of this program succeeding?

---

## 3. Scope

### In Scope

List specifically what this program covers. Be concrete - vague scope is how programs expand without anyone noticing.

- [Scope item 1]
- [Scope item 2]
- [Scope item 3]

### Out of Scope

Just as important as in scope. List things that are related but explicitly not part of this program.

- [Out of scope item 1]
- [Out of scope item 2]
- Anything not explicitly listed in scope above

### Build vs. Buy Decision

| Decision | Rationale | Date Decided |
|----------|-----------|-------------|
| [Build / Buy / Hybrid] | | |

If buying: procurement and legal engagement required before work starts.

---

## 4. Approach and Milestones

### Delivery Approach

Agile / Waterfall / Hybrid - and why.

### High Level Milestones

| Milestone | Description | Target Date | Owner |
|-----------|-------------|-------------|-------|
| Program Kickoff | | | TPM |
| Requirements Complete | | | PO |
| Design Complete | | | Engineering Lead |
| [Key Milestone 1] | | | |
| [Key Milestone 2] | | | |
| User Acceptance Testing | | | TPM + PO |
| Go-Live / Launch | | | TPM |
| Program Close | | | TPM |

### Key Dates and Constraints

List any fixed deadlines (regulatory, contractual, product launch) that constrain the schedule.

| Date | Constraint | Impact if Missed |
|------|-----------|-----------------|
| | | |

---

## 5. Resources

### Team

| Role | Name | Allocation | Timeframe |
|------|------|-----------|-----------|
| Executive Sponsor | | Escalation only | Full program |
| Product / Program Owner | | [%] | |
| Technical Program Manager | | [%] | |
| Engineering Lead | | [%] | |
| Technical Architect | | [%] | |
| Engineer | | [%] | |
| [Other role] | | [%] | |

### Budget

| Category | Estimated Cost | Notes |
|----------|---------------|-------|
| Engineering headcount | | |
| Tooling / licensing | | |
| Vendor / contractor | | |
| Other | | |
| **Total** | | |

---

## 6. Stakeholders and Communications

### RACI

| Role | Responsible | Accountable | Consulted | Informed |
|------|------------|-------------|-----------|---------|
| Executive Sponsor | | X | | X |
| Product / Program Owner | X | | X | X |
| TPM | X | | X | X |
| Engineering Lead | X | | X | X |
| [Partner Team] | | | X | X |
| [Compliance / Legal] | | | X | |

### Stakeholder Map

| Stakeholder / Group | Interest | Engagement Level | Communication Method |
|--------------------|----------|-----------------|---------------------|
| Executive Sponsor | Program outcomes, budget | Low frequency, high signal | Monthly steering update |
| Engineering Teams | Technical direction, workload | High frequency | Weekly sync |
| [Partner Team] | Dependencies, integration | As needed | Bi-weekly |
| [End Users] | Launch readiness, training | Pre-launch | Comms plan |

---

## 7. Risks, Assumptions, and Dependencies

### Initial Risks

| Risk | Probability | Impact | Mitigation | Owner |
|------|------------|--------|-----------|-------|
| [Risk 1] | High / Med / Low | High / Med / Low | | |
| [Risk 2] | | | | |
| Resource contention from higher priority programs | Med | High | Escalation path defined with sponsor | TPM |

*Full RAID log maintained separately - see [link to RAID log].*

### Assumptions

List things you are assuming to be true that, if wrong, would change the plan.

1. [Assumption 1]
2. [Assumption 2]
3. Required team members will be available at the allocations listed above.

### Dependencies

| Dependency | Type | Owner | Status |
|-----------|------|-------|--------|
| [Dependency 1] | Internal / External | | |
| [Dependency 2] | | | |

---

## 8. Compliance and Reviews

List any compliance, security, legal, or architecture reviews required for this program. Initiate these early - late discoveries here are the most expensive kind.

| Review Type | Required? | Owner | Target Date | Status |
|------------|-----------|-------|-------------|--------|
| Security / Architecture Review | | | | |
| Compliance Assessment (HIPAA / PCI / SOX / other) | | | | |
| Legal / Privacy Review | | | | |
| Vendor / Procurement Review | | | | |
| Penetration Testing | | | | |

---

## 9. Operational Handoff

Who owns this after the program delivers? Define the support model before go-live, not after.

| Item | Detail |
|------|--------|
| Operational owner | |
| Support model | |
| Runbook location | |
| Escalation path | |
| Handoff date | |

---

## Notes on Using This Template

The charter is a living document through the Definition & Planning phase. Once approved, changes to scope, budget, or Definition of Done go through formal change control.

A one-page charter is fine for a small project. A complex multi-team program may need every section fully built out. Use judgment - the goal is shared understanding, not document volume.

If you cannot get executive sponsor sign-off on the charter, you do not have a real program yet. That is important information to have before you spend six months building something.

---

*Template version 1.0. Propose changes via pull request.*
