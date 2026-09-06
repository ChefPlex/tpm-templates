# Program Phases Playbook

A practical guide to running programs and projects from first idea to final close-out. This playbook defines the phases, the artifacts that should come out of each one, and who owns what. It's intended for Technical Program Managers but is useful for anyone leading a complex cross-functional initiative.

This is a living document. The phases are sequential but reality isn't always - use judgment about what applies to your program's scope and complexity.

---

## Phases at a Glance

| Phase | What Happens |
|-------|-------------|
| 1. Conception & Initiation | Idea gets structured, scoped, and approved |
| 2. Definition & Planning | Requirements get translated into a real plan |
| 3. Launch & Execution | Work gets done, tracked, and reported |
| 4. Performance & Control | Plan stays valid, risks stay managed |
| 5. Program Closure | Work gets wrapped up, lessons get captured |

---

## Phase 1: Conception & Initiation

**What happens here:** The product or program owner structures the idea, makes the case for investment, and gets leadership alignment to proceed.

**Artifacts:**

| Artifact | Owner | Required? | Notes |
|----------|-------|-----------|-------|
| Program/Project Charter (1-pager) | Product/Program Owner | Required | Pitch the idea, the value, and the ask |
| Business Requirements Document | Product/Program Owner | Required | What problem are we solving and for whom |
| Definition of Done (initial) | Product/Program Owner | Required | What does success actually look like |
| TPM intake request | Product/Program Owner | Recommended | Engage TPM resources early |
| Program record in project tracking system | TPM (if assigned) or PO | Required | Get it in the system before work starts |

**Key questions to answer before moving on:**
- Do we have leadership approval to invest resources?
- Is the Definition of Done clear enough to build a plan against?
- Do we know who the executive sponsor is?
- Have we made a preliminary build vs. buy decision?

**Ceremonies:** Review idea with executive sponsor and initial stakeholders before moving forward.

---

## Phase 2: Definition & Planning

**What happens here:** Business requirements get translated into functional requirements, a real plan, and the working structures the team will use throughout the program.

**Artifacts:**

| Artifact | Owner | Required? | Notes |
|----------|-------|-----------|-------|
| Functional / Non-Functional Requirements | Product/Program Owner + Engineering | Required | Translate business needs into technical scope |
| High Level Design (HLD) | Engineering Manager + Architect | Required | How are we going to build this |
| Low Level Design (LLD) | Engineers / Architects | Recommended | Details per component as needed |
| RAID Log (Risks, Assumptions, Issues, Dependencies) | TPM | Required | Start it now, do not wait |
| Communications Plan | TPM | Recommended | RACI, stakeholder map, cadence |
| Resource Plan | Engineering Manager + TPM | Recommended | Headcount, budget, timeline |
| Program Roadmap | Product/Program Owner + TPM | Recommended | Deliverables mapped across releases or sprints |
| Dependency Map | TPM | Recommended | Internal and external dependencies logged |
| Program Kickoff Deck | TPM | Recommended | Charter overview, RACI review, HLD review, team agreement |
| Work Breakdown / Sprint Release Plan | TPM + Engineering | Recommended | Level of detail scales with program complexity |
| Buy vs. Build Decision Record | Product/Program Owner + Engineering | Required if buying | Document the decision and the rationale |
| Compliance Assessment | TPM / GRC equivalent | Required if applicable | Determine regulatory scope early - surprises here are expensive |
| Security / Architecture Review | TPM + Engineering | Required if applicable | Get the right eyes on the design before you build it |
| Vendor SOW / MSA | Product/Program Owner + Legal + Procurement | Required if buying | Do not start vendor work without this |

**Key questions to answer before moving on:**
- Does the team agree on the Definition of Done at the milestone and epic level?
- Are risks logged and owned?
- Is the plan realistic given the resources we actually have?
- Have compliance and security reviews been initiated where required?

**Ceremonies:** Program kickoff (record it - new team members will thank you later). Dependency review with partner teams.

---

## Phase 3: Launch & Execution

**What happens here:** The work gets done. The TPM's job shifts from planning to tracking, communicating, and clearing blockers.

**Artifacts:**

| Artifact | Owner | Required? | Notes |
|----------|-------|-----------|-------|
| Weekly/Bi-weekly Status Reports | TPM | Required | On time, every time - this is how trust gets built |
| Leadership / Executive Updates | TPM + PO | Required | Cadence depends on program criticality |
| RAID Log (ongoing) | TPM | Required | Living document - reviewed regularly, not just when something goes wrong |
| Milestone / Schedule Maintenance | TPM | Required | Plan reflects reality, not wishful thinking |
| Change Management Plan | TPM | Recommended | How will impacted teams and users be prepared |
| Change Control Log | TPM | Recommended | Scope changes get documented and approved, not just absorbed |
| User Acceptance Testing (UAT) plan | TPM + Engineering | Recommended if applicable | Define acceptance criteria before testing starts |
| Production Release / Cutover Plan | TPM + Engineering | Recommended | Especially important for customer-facing or infrastructure changes |
| Operational / Support Model | TPM + Engineering | Recommended | Who owns this after launch - answer this before go-live, not after |
| Launch Coordination Checklist | TPM | Recommended | Nothing gets missed on go-live day |

**Key questions to ask regularly:**
- Is the plan still realistic?
- Are any risks trending toward issues?
- Do stakeholders have what they need to make decisions?
- Is the team blocked on anything I can clear?

**Ceremonies:** Weekly team sync. Steering committee (monthly or as needed for escalations). Sprint reviews / demos for agile programs.

---

## Phase 4: Performance & Control

**What happens here:** Ongoing review of whether the plan, the risks, and the metrics are still valid given how the program has evolved.

**Activities:**

| Activity | Owner | Required? | Notes |
|----------|-------|-----------|-------|
| Regular plan review and update | TPM | Required | Assumptions made in planning may no longer hold |
| Risk and issue review | TPM | Required | Not just tracking - are mitigations actually working |
| Dashboard / metrics review | TPM + PO | Recommended | Are the metrics still measuring the right things |
| Dependency review | TPM | Recommended | External dependencies shift - stay on top of them |
| Resource estimate review | Engineering Manager + TPM | Recommended | People get pulled, timelines slip - reforecast regularly |
| Budget review | Finance + PO | Required | Spend tracked against forecast |
| Compliance / audit follow-up | TPM | Required if applicable | Close out open items from compliance reviews |
| Transition to BAU planning | TPM + Engineering | Recommended | Start planning the handoff before you need it |

**The right question here isn't "are we on track" - it's "is our picture of the program still accurate."** A plan that nobody trusts isn't a plan.

---

## Phase 5: Program Closure

**What happens here:** Work gets formally closed. Lessons get documented. Resources get released. The team gets recognized.

**Artifacts:**

| Artifact | Owner | Required? | Notes |
|----------|-------|-----------|-------|
| Lessons Learned | TPM | Recommended | Run a retrospective - make it a real conversation, not a checkbox |
| Project Close-Out Report | TPM | Recommended | Did we achieve what we set out to do? If not, why not? |
| Operational / Support Model (signed off) | Engineering Manager | Required | The team that built it does not own it forever |
| Final budget close-out | Finance + PO | Required | Close all financial records |
| Resource release | Engineering Manager | Required | People need to know they are off the program |
| Program record closed | TPM | Required | Keep the system of record accurate |
| Executive / stakeholder notification | TPM | Recommended | Close the loop with everyone who had a stake in this |
| Team celebration | TPM | Required | Not optional. Programs are hard. Recognize the work. |

**The close-out report goes to the program sponsor and key stakeholders when completed.** It should include the lessons learned output and an honest assessment of whether the program achieved its objectives. If it didn't, the report explains why and what was done about it.

---

## Glossary

| Term | Definition |
|------|-----------|
| Portfolio | A collection of programs and projects grouped to meet strategic objectives. Examples: Identity & Access Management, Platform Security, Data Infrastructure. |
| Program | A group of related projects managed together to produce outcomes not achievable from managing them individually. Often maps to a strategic goal or annual priority. |
| Project | A temporary effort with a defined start, end, and deliverable. |
| Milestone | A significant planned event in the project schedule - often a major deliverable or phase gate. |
| RAID Log | Tracker for Risks, Assumptions, Issues, and Dependencies. The TPM's most important operational tool. |
| Definition of Done | Agreed, measurable criteria that define what "complete" means for a milestone, epic, or project. |
| HLD | High Level Design - architectural overview of how a solution will be built. |
| LLD | Low Level Design - detailed component-level design, typically owned by engineering. |
| RACI | Responsibility matrix: Responsible, Accountable, Consulted, Informed. |
| BAU | Business As Usual - the operational state after a program delivers and transitions to support. |
| Change Control | Formal process for evaluating and approving changes to program scope, schedule, or budget. |

---

## A Note on Required vs. Recommended

"Required" means the program shouldn't advance past this phase without it. "Recommended" means it's the right practice for most programs - use judgment on smaller or lower-risk efforts.

The goal is not artifact production. The goal is shared understanding, clean decisions, and programs that deliver. The artifacts exist to support that, not the other way around.

---

*This playbook is version 1.0. Propose edits via pull request or open an issue with your suggested change and the reasoning behind it.*
