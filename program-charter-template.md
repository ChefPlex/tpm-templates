# Program Charter Template

A program charter is the founding document for any serious initiative. It exists to answer the questions every stakeholder is going to ask anyway - why are we doing this, what exactly are we doing, who is responsible, and how will we know when we are done. Getting this on paper at the start saves a lot of painful conversations later.

Start with the charter summary below: one table, with the program name in its title, short enough to be the one-pager. When the program needs every section written out, use the [alternate style](#alternate-style-the-full-charter-on-one-page) at the bottom of this page and link to it from the summary.

---

## The Charter Summary - [Program Name]

| Problem | Definition of Done | Scope | Executive Sponsor | TPM | Target date | Status | Full charter |
|:---|:---|:---|:---|:---|:---|:---|:---|
| | | | | | | | |
| | | | | | | | |
| | | | | | | | |

For a larger program, add the columns you need: the product or program owner, the objectives, the budget, and the delivery approach.

### What goes in each column

- **Problem:** the problem, gap or risk, and what it costs to do nothing, in one or two sentences.
- **Definition of Done:** what "complete" means, precise enough that a reasonable person could look at the finished work and say yes or no.
- **Scope:** what is in, and the related things that are explicitly out.
- **Executive Sponsor:** the person who approves the charter and the baseline, and takes escalations.
- **TPM:** the person running the program day to day.
- **Target date:** when the Definition of Done should be met, or when you expect to have a date.
- **Status:** Draft, In Review, or Approved, with the date it changed.
- **Full charter:** a link to the full charter, if there is one.

---

## How to Fill It In

Fill in every section. If you cannot fill in a section, that is useful information - it means you are not ready to start yet.

A one-page charter is fine for a small project. A complex multi-team program may need every section fully built out. Use judgment - the goal is shared understanding, not document volume.

The charter is a living document through the Definition & Planning phase. Once approved, changes to scope, budget, or Definition of Done go through formal change control.

**Check the six questions.** Before it goes for approval, read the charter as someone new to the program would, and make sure it answers who, what, when, where, why and how. A gap in any one is a question somebody will ask later.

**Background.** How the program came about: the assessment, incident, audit or decision that started it, with links to those documents. A new team member should be able to read it and understand why this exists now.

**Problem statement.** What is the problem, gap, or risk this program addresses? Be specific. A vague problem statement produces a vague program.

> Example: "Our encryption coverage across platform services stands at 35%. Any service transmitting data without encryption in transit represents a direct customer trust risk and a compliance exposure. Left unaddressed, this gap grows as we add services."

**Strategic alignment.** How does this program connect to the organization's current priorities? What happens if we do not do it? Reference the annual plan, OKR, compliance deadline, or strategic initiative, and say what gets worse, more expensive, or more risky if we delay.

**Program overview.** Two to four sentences describing what this program does and how it addresses the problem above.

**Objectives.** List 3-5 specific, measurable objectives. Avoid vague language like "improve" or "enhance" without a number attached. A useful test is SMART: specific, measurable, achievable with the people and skills you have, relevant to the organization's goals, and time-bound.

**Deliverables.** List what the program will hand over: the systems, documents, policies or services that exist when it is done.

**How the work was prioritized.** If the program addresses several problems, say how they were ranked, for example by likelihood and impact, and what each one means here. It tells the reader why the work is in this order.

**Definition of Done.** This is the contract. What does "complete" mean for this program? Be precise enough that a reasonable person could look at the finished work and say yes or no. Add the business metrics: what needle moves in the business as a result of this program succeeding?

**In scope and out of scope.** List specifically what this program covers. Be concrete - vague scope is how programs expand without anyone noticing. Out of scope is just as important as in scope: list things that are related but explicitly not part of this program. If other teams will own the work after the program, put their ramp-up and the handoff in scope.

**Workstreams and initial steps.** For each workstream, name the recommended action, the owner, and the next step or resource request. It is the first version of the [swim lanes](program-swim-lanes-template.md).

**Build vs. buy.** Record the decision, the rationale and the date. If buying: procurement and legal engagement required before work starts.

**Delivery approach.** Agile / Waterfall / Hybrid - and why.

### Tailoring Decisions

List anything from the [Program Phases Playbook](program-phases-playbook.md) you chose to leave out, and why. Revisit it as the program learns more.

**High level milestones.** Some milestones need preparation finished before their work can start, such as hardware, circuits, access or a site survey. Estimate how long it takes and add a buffer (if it should take three weeks, plan four), then work back to when it has to begin. For a larger program, add the columns you need: what each milestone depends on, the preparation window before it, and its current status.

**Key dates and constraints.** List any fixed deadlines (regulatory, contractual, product launch) that constrain the schedule, and the impact if each is missed.

**Resources.** Name the team, each person's allocation and timeframe, and the estimated budget by category.

### RACI

List the decisions the charter commits to, not the roles. Each row gets exactly one A. Leave a cell blank when the role has no part in that decision. For a full matrix, use the [waterfall](raci-template-waterfall.md) or [agile](raci-template-agile.md) RACI template.

| Decision | Executive Sponsor | Product / Program Owner | TPM | Engineering Lead | [Partner Team] | [Compliance / Legal] |
|:---|:---|:---|:---|:---|:---|:---|
| Approve charter and baseline | A | R | R | C | I | C |
| Scope change within the baseline | C | A | R | C | I | |
| Scope change that moves the date, budget or baseline | A | C | R | C | I | |
| Budget change | A | C | R | | | |
| Go / no-go at launch | A | R | R | C | I | C |
| Definition of Done sign-off | I | A | R | C | | |
| [Decision] | | | | | | |

**Stakeholder map.** For each stakeholder or group, note what they care about, how often they need to hear from you, and how. The [communications plan](communications-plan-template.md) builds on it.

**Risks.** For a larger program, add the columns you need: how soon each risk could land, and a rough exposure in days or dollars for the top ones. Keep the full RAID log separately and link to it.

**Assumptions and limitations.** List things you are assuming to be true that, if wrong, would change the plan. List the limitations too: the constraints the program has to work within, such as a fixed team, a frozen system or a hard date.

**Dependencies.** For a larger program, add the columns you need: the date it is needed by, and what slips if it is late.

**Compliance and reviews.** List any compliance, security, legal, or architecture reviews required for this program. Initiate these early - late discoveries here are the most expensive kind.

**Operational handoff.** Who owns this after the program delivers? Define the support model before go-live, not after.

---

## What to Learn From

### Unknown vs Actionable

The same summary row, written two ways:

For a program called Encryption in Transit:

| | Problem | Definition of Done | Scope | Executive Sponsor | TPM | Target date | Status |
|:---|:---|:---|:---|:---|:---|:---|:---|
| **Unknown** | Improve encryption | Services encrypted | Platform | | TPM | Q3 | In progress |
| **Actionable** | 35% of platform services encrypt data in transit; a customer trust risk and a compliance exposure that grows with every new service | Every in-scope service accepts only TLS 1.2 or higher, confirmed by scan, signed off by the product owner | In: platform services listed in the charter. Out: third-party SaaS, internal batch jobs | [Sponsor name] | [TPM name] | [Date], or the date we will have one | Approved, [date] |

The actionable row answers who sponsors and runs it, what done looks like, when it is due, where the boundary is, why it is worth doing and how completion is proven. The unknown row could describe almost any encryption effort, which is why nobody can say yes or no to it. A longer worked example is in the [sample charter excerpt](examples/sample-program-charter-excerpt.md).

### Where This Breaks

- **No sponsor sign-off.** If you cannot get executive sponsor sign-off on the charter, you do not have a real program yet. That is important information to have before you spend six months building something.
- **A vague problem statement.** A vague problem statement produces a vague program.
- **Scope with no edges.** Vague scope is how programs expand without anyone noticing. Out of scope is just as important as in scope.
- **Compliance found late.** Late discoveries here are the most expensive kind.
- **Support decided after go-live.** Define the support model before go-live, not after.
- **Document volume as the goal.** The goal is shared understanding, not document volume.

---

## Reference

### Charter Status

| Status | Meaning |
|:---|:---|
| **Draft** | Being written |
| **In Review** | With the approvers |
| **Approved** | Signed off; changes to scope, budget, or Definition of Done go through change control |

### Related Templates

- [Program Phases Playbook](program-phases-playbook.md) - the artifacts the charter's tailoring decisions refer to.
- [Communications Plan](communications-plan-template.md) - built from the stakeholder map.
- [RACI, waterfall](raci-template-waterfall.md) and [RACI, agile](raci-template-agile.md) - the full matrix.
- [RAID Log Guide](raid-log-guide.md) - where the risks, assumptions and dependencies live once the charter is approved.

---

## Alternate Style: The Full Charter on One Page

Use this when the program needs every section written out. Copy the block into a new file, name it for the program, and link it from the summary. It holds far more than a summary row, and it is harder to compare across programs, so keep the summary as the index.

```markdown
# Program Charter: [Program Name]

## Document Control

| Field | Detail |
|:---|:---|
| Program Name | |
| Version | 1.0 |
| Status | Draft / In Review / Approved |
| Date | |
| TPM | |
| Product / Program Owner | |
| Executive Sponsor | |

### Approvals

| Role | Name | Date Approved |
|:---|:---|:---|
| Executive Sponsor | | |
| Engineering Leader | | |
| Product / Program Owner | | |
| TPM Lead | | |

### Contributors

| Name | Role | Contribution |
|:---|:---|:---|
| | | |

### Change Log

| Version | Date | Author | Change |
|:---|:---|:---|:---|
| 1.0 | | | Initial draft |

## 1. Why Are We Doing This

### Background
[How the program came about, with links to the assessments or decisions that started it.]

### Problem Statement
[The problem, gap, or risk. Be specific.]

### Strategic Alignment
> Alignment: [Reference to annual plan, OKR, compliance deadline, or strategic initiative]
> Cost of inaction: [What gets worse, more expensive, or more risky if we delay]

## 2. What We Are Building

### Program Overview
[Two to four sentences.]

### Objectives
1. [Objective 1 - specific and measurable]
2. [Objective 2 - specific and measurable]
3. [Objective 3 - specific and measurable]

### Deliverables
- [Deliverable 1]
- [Deliverable 2]

### How the Work Was Prioritized
[For example: likelihood x impact, and what each means here.]

### Definition of Done

| Success Criterion | Measurement | Target |
|:---|:---|:---|
| [Criterion 1] | [How measured] | [Target value or date] |
| [Criterion 2] | [How measured] | [Target value or date] |
| [Criterion 3] | [How measured] | [Target value or date] |

**Business Metrics:** [What needle moves in the business]

## 3. Scope

### In Scope
- [Scope item 1]
- [Scope item 2]
- [Scope item 3]

### Out of Scope
- [Out of scope item 1]
- [Out of scope item 2]
- Anything not explicitly listed in scope above

### Build vs. Buy Decision

| Decision | Rationale | Date Decided |
|:---|:---|:---|
| [Build / Buy / Hybrid] | | |

## 4. Approach and Milestones

### Delivery Approach
[Agile / Waterfall / Hybrid - and why.]

### Tailoring Decisions
[What you left out of the Program Phases Playbook, and why.]

### Workstreams and Initial Steps

| Workstream | Recommended Action | Owner | Next Step / Resource Request |
|:---|:---|:---|:---|
| | | | |

### High Level Milestones

| Milestone | Description | Target Date | Owner |
|:---|:---|:---|:---|
| Program Kickoff | | | TPM |
| Requirements Complete | | | PO |
| Design Complete | | | Engineering Lead |
| [Key Milestone 1] | | | |
| [Key Milestone 2] | | | |
| User Acceptance Testing | | | TPM + PO |
| Go-Live / Launch | | | TPM |
| Program Close | | | TPM |

### Key Dates and Constraints

| Date | Constraint | Impact if Missed |
|:---|:---|:---|
| | | |

## 5. Resources

### Team

| Role | Name | Allocation | Timeframe |
|:---|:---|:---|:---|
| Executive Sponsor | | Escalation only | Full program |
| Product / Program Owner | | [%] | |
| Technical Program Manager | | [%] | |
| Engineering Lead | | [%] | |
| Technical Architect | | [%] | |
| Engineer | | [%] | |
| [Other role] | | [%] | |

### Budget

| Category | Estimated Cost | Notes |
|:---|:---|:---|
| Engineering headcount | | |
| Tooling / licensing | | |
| Vendor / contractor | | |
| Other | | |
| **Total** | | |

## 6. Stakeholders and Communications

### RACI

| Decision | Executive Sponsor | Product / Program Owner | TPM | Engineering Lead | [Partner Team] | [Compliance / Legal] |
|:---|:---|:---|:---|:---|:---|:---|
| Approve charter and baseline | A | R | R | C | I | C |
| Scope change within the baseline | C | A | R | C | I | |
| Scope change that moves the date, budget or baseline | A | C | R | C | I | |
| Budget change | A | C | R | | | |
| Go / no-go at launch | A | R | R | C | I | C |
| Definition of Done sign-off | I | A | R | C | | |
| [Decision] | | | | | | |

### Stakeholder Map

| Stakeholder / Group | Interest | Engagement Level | Communication Method |
|:---|:---|:---|:---|
| Executive Sponsor | Program outcomes, budget | Low frequency, high signal | Monthly steering update |
| Engineering Teams | Technical direction, workload | High frequency | Weekly sync |
| [Partner Team] | Dependencies, integration | As needed | Bi-weekly |
| [End Users] | Launch readiness, training | Pre-launch | Comms plan |

## 7. Risks, Assumptions, and Dependencies

### Initial Risks

| Risk | Probability | Impact | Mitigation | Owner |
|:---|:---|:---|:---|:---|
| [Risk 1] | High / Med / Low | High / Med / Low | | |
| [Risk 2] | | | | |
| Resource contention from higher priority programs | Med | High | Escalation path defined with sponsor | TPM |

*Full RAID log maintained separately - see [link to RAID log].*

### Assumptions
1. [Assumption 1]
2. [Assumption 2]
3. Required team members will be available at the allocations listed above.

### Limitations
- [Constraints the program has to work within]

### Dependencies

| Dependency | Type | Owner | Status |
|:---|:---|:---|:---|
| [Dependency 1] | Internal / External | | |
| [Dependency 2] | | | |

## 8. Compliance and Reviews

| Review Type | Required? | Owner | Target Date | Status |
|:---|:---|:---|:---|:---|
| Security / Architecture Review | | | | |
| Compliance Assessment (HIPAA / PCI / SOX / other) | | | | |
| Legal / Privacy Review | | | | |
| Vendor / Procurement Review | | | | |
| Penetration Testing | | | | |

## 9. Operational Handoff

| Item | Detail |
|:---|:---|
| Operational owner | |
| Support model | |
| Runbook location | |
| Escalation path | |
| Handoff date | |
```

---

*Template version 1.1. Propose changes via pull request.*
