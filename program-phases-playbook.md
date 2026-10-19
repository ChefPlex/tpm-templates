# Program Phases Playbook

A practical guide to running programs and projects from first idea to final close-out. It lists what happens in each phase, what each step produces, and who owns it. It's intended for Technical Program Managers but is useful for anyone leading a complex cross-functional initiative.

The table below is the whole playbook, in the order the work happens, one phase after another. Each row says what happens, what it produces, who owns it and how much it matters. The questions to answer before leaving each phase, and the details behind several rows, are in [Reference](#reference).

---

## Program Phases - [Program Name]

| What happens | Artifact / outcome | Owner | Level | Status | Notes |
|:---|:---|:---|:---|:---|:---|
| **1. Conception & Initiation** | | | | | |
| Pitch the idea, the value and the ask | Program / project charter (1-pager), or a PRFAQ | Product / program owner | Must | | |
| Get leadership approval for resources and budget to proceed | Approval names and date on the charter | Executive sponsor | Should | | Agreement from the engineering, product and TPM leads, approval from the executive who funds it |
| Start the stakeholder register with whoever handed you the work | Stakeholder register (started) | Product / program owner + TPM | Must | | It fills in during discovery. See the [Stakeholder Engagement Playbook](stakeholder-engagement-playbook.md) |
| Collect the business requirements: what problem, and for whom | Business requirements document | Product / program owner | Must | | |
| Propose what success looks like | Definition of Done (initial) | Product / program owner | Must | | If the goal is to move a metric, record the baseline, or a to-do to get one |
| Request TPM support early | TPM intake request | Product / program owner | Should | | |
| Put the program in the tracking system before work starts | Program record | TPM, or PO if no TPM yet | Must | | |
| Review the idea with the executive sponsor and initial stakeholders | Go-ahead to plan | Product / program owner | Should | | |
| **2. Definition & Planning** | | | | | |
| Translate business needs into technical scope | Functional / non-functional requirements | Product / program owner + engineering | Must | | |
| Link each requirement to the design that covers it, the test that proves it, and who accepted it | Requirements traceability | Product / program owner + engineering + QA | Should | | Close to a Must for regulated, audited or contract work. A spreadsheet is enough |
| Decide how it will be built | High Level Design (HLD) | Engineering manager + architect | Must | | Enterprise-wide changes go to an architecture review board. Consider the chargeback model and BCDR |
| Detail each component as needed | Low Level Design (LLD) | Engineers / architects | Should | | |
| Start logging risks, assumptions, issues and dependencies now | RAID log | TPM | Must | | Do not wait |
| Plan who hears what, how often | Communications plan | TPM | Should | | RACI and cadence, built from the stakeholder register |
| Estimate the work | Estimates | Engineering manager | Should | | See [T-shirt sizing](#t-shirt-sizing) |
| Project headcount, budget and timeline | Resource plan | Engineering manager + TPM | Should | | |
| Map deliverables across releases or sprints | Program roadmap | Product / program owner + TPM | Should | | |
| Log internal and external dependencies | Dependency map | TPM | Should | | Include standards and government deadlines |
| Break the work down to the level the program needs | Work breakdown / sprint release plan | TPM + engineering | Should | | Detail scales with complexity. Add success metrics per milestone |
| Lock down the Definition of Done at the milestone and epic level, with what is in and out of scope | Definition of Done (agreed) | TPM + product / program owner | Must | | Each one measurable, with the metric that measures it |
| Decide build or buy | Buy vs. build decision record | Product / program owner + engineering | As needed | | When buying is on the table. See [buying](#when-buying-is-on-the-table) |
| Select the vendor | Vendor selection | Product / program owner + procurement | As needed | | When buying |
| Contract the vendor | Vendor SOW / MSA | Product / program owner + legal + procurement | As needed | | Do not start vendor work without this |
| Determine regulatory scope early | Compliance assessment | TPM / GRC | As needed | | Surprises here are expensive |
| Threat-model the design and get the security requirements | Security / architecture review | TPM + engineering | As needed | | A pen test may follow if the service is internet-facing |
| Check the privacy and legal exposure | Legal / privacy review | TPM + product / program owner | As needed | | See [when it is needed](#when-a-legal--privacy-review-is-needed) |
| Prepare the kickoff | Kickoff deck | TPM | Should | | Charter, RACI, HLD, team agreement. See the [Program Kickoff Checklist](https://github.com/ChefPlex/tpm-toolbox/blob/main/program-kickoff-checklist.md) |
| Run the program kickoff, and record it | Kickoff held, recording | TPM | Must | | New team members will thank you later |
| Review dependencies with partner teams | Dependency review | TPM | Should | | |
| **3. Launch & Execution** | | | | | |
| Report status on time, every time | Weekly / bi-weekly status reports | TPM | Must | | This is how trust gets built |
| Update leadership | Leadership / executive updates | TPM + product / program owner | Must | | Cadence depends on how critical the program is |
| Keep the RAID log current | RAID log (ongoing) | TPM | Must | | Reviewed regularly, not just when something goes wrong |
| Keep the plan matching reality | Milestone / schedule maintenance | TPM | Must | | Not wishful thinking |
| Prepare impacted teams and users | Change management plan | TPM | Should | | |
| Document and approve scope changes | Change control log | TPM | Should | | Not just absorbed |
| Define acceptance criteria before testing starts | UAT plan | TPM + engineering | As needed | | |
| Run the penetration test the security review asked for | Pen test results | Engineering + security | As needed | | |
| Plan the release or cutover | Production release / cutover plan | TPM + engineering | Should | | Especially for customer-facing or infrastructure changes |
| Decide who owns it after launch | Operational / support model, runbook | TPM + engineering | Should | | Answer this before go-live, not after. Other teams may have to accept it |
| Make sure nothing gets missed on go-live day | Launch coordination checklist | TPM | Should | | |
| Hold the weekly team sync | Team sync | TPM | Must | | |
| Hold the steering committee | Steering committee | TPM | As needed | | Monthly, or as needed for escalations |
| Run sprint reviews and demos | Sprint reviews | Engineering + scrum lead | As needed | | For agile programs |
| **4. Performance & Control (runs alongside Phase 3)** | | | | | |
| Review and update the plan | Updated plan | TPM | Must | | Assumptions made in planning may no longer hold |
| Review risks and issues | Risk and issue review | TPM | Must | | Not just tracking - are the mitigations working? |
| Review the dashboards and metrics | Metrics review | TPM + product / program owner | Should | | Are they still measuring the right things? |
| Review dependencies | Dependency review | TPM | Should | | External dependencies shift |
| Review resource estimates | Reforecast | Engineering manager + TPM | Should | | People get pulled, timelines slip |
| Check the system of record still reflects the program | Accurate program record | TPM | Should | | Teams, systems and owners as they are now |
| Track spend against forecast, and against any promised savings | Budget review | Finance + product / program owner | Must | | |
| Close out open items from compliance or security reviews | Review follow-up | TPM | As needed | | Including any sign-off still owed |
| Start planning the handoff before you need it | Transition to BAU plan | TPM + engineering | Should | | |
| **5. Program Closure** | | | | | |
| Run a retrospective | Lessons learned | TPM | Should | | A real conversation, not a checkbox |
| Report what was achieved | [Close-out report](program-close-out-report-template.md) | TPM | Should | | Did we achieve what we set out to do? If not, why not? |
| Transfer knowledge to the team taking over | Knowledge transfer sessions | TPM + engineering | As needed | | |
| Hand over and sign off support | Operational / support model (signed off) | Engineering manager | Must | | The team that built it does not own it forever |
| Close the financials | Final budget close-out | Finance + product / program owner | Must | | |
| Release the people | Resource release | Engineering manager | Must | | People need to know they are off the program |
| Close the program record | Program record closed | TPM | Must | | Keep the system of record accurate |
| Close the loop with everyone who had a stake | Executive / stakeholder notification | TPM | Should | | |
| Celebrate the team | Team celebration | TPM | Must | | Programs are hard. Recognize the work |

### What goes in each column

- **What happens:** the activity, in the order the work usually happens. Bold rows mark the five phases.
- **Artifact / outcome:** what exists when the activity is done.
- **Owner:** the person who produces it. Write a name once you know it. Who approves it is in the charter's [RACI](program-charter-template.md#raci).
- **Level:** **Must** - nearly every program needs it. **Should** - the right practice for most programs. **As needed** - add it when the program calls for it.
- **Status:** done, in progress, not started, or skipped, with the date it changed.
- **Notes:** a link to the artifact, what is still open, or why it was skipped.

---

## How to Fill It In

This is a living document. The phases are sequential but reality isn't always - use judgment about what applies to your program's scope and complexity.

**Look it over before the program starts, and again along the way.** The phases follow the PMI (Project Management Institute) process model. It is a good standard to start from, and your plan may end up looking quite different. Look it over before the program starts, and again along the way, to make sure nothing was forgotten.

**Keep the rows that fit.** Treat the table as prompts: use what fits, skip what does not, and note in the [charter](program-charter-template.md#tailoring-decisions) anything you chose to leave out. When an "As needed" row applies to your program, treat it as a Must. Add rows your program needs, in the place they happen.

**Use the questions at each phase.** Each phase has [questions to answer before moving on](#questions-before-moving-on). They are the real test of whether a phase is finished, more than the artifact count.

---

## What to Learn From

### Unknown vs Actionable

The same row, written two ways, and a skipped row written well:

| | What happens | Artifact / outcome | Owner | Level | Status | Notes |
|:---|:---|:---|:---|:---|:---|:---|
| **Unknown** | RAID | RAID log | TPM | Must | In progress | |
| **Actionable** | Start logging risks, assumptions, issues and dependencies now | RAID log [link to the program folder] | [TPM name] | Must | In progress since Oct 6; reviewed at the Tuesday team sync | Started before the HLD, so design risks land in it from day one |
| **Actionable, skipped** | Detail each component as needed | Low Level Design | [Engineering lead name] | Should | Skipped, Oct 8 | One component; the HLD covers it. Recorded in the charter's tailoring decisions [link] |

The actionable rows answer who owns it, what it is, when it changed, where it lives, why it exists or was skipped, and how it is kept current. A skipped row with a reason is a decision; a missing row is a gap nobody can see.

### Where This Breaks

- **Artifact production as the goal.** The goal is not artifact production. The goal is shared understanding, clean decisions, and programs that deliver. The artifacts exist to support that, not the other way around.
- **A plan nobody trusts.** The right question in Performance & Control isn't "are we on track" - it's "is our picture of the program still accurate." A plan that nobody trusts isn't a plan.
- **The RAID log opened only when something goes wrong.** It is a living document - reviewed regularly, not just when something goes wrong.
- **Scope changes absorbed, not documented.** Scope changes get documented and approved, not just absorbed.
- **Support ownership decided after go-live.** Who owns this after launch - answer this before go-live, not after. The team that built it does not own it forever.
- **Lessons learned as a checkbox.** Run a retrospective - make it a real conversation, not a checkbox.

---

## Reference

### Phases at a Glance

| Phase | What Happens |
|:---|:---|
| 1. Conception & Initiation | Idea gets structured, scoped, and approved |
| 2. Definition & Planning | Requirements get translated into a real plan |
| 3. Launch & Execution | Work gets done, tracked, and reported |
| 4. Performance & Control (runs alongside Phase 3) | Plan stays valid, risks stay managed |
| 5. Program Closure | Work gets wrapped up, lessons get captured |

### Questions Before Moving On

**1. Conception & Initiation**
- Do we have leadership approval to invest resources?
- Is the Definition of Done clear enough to build a plan against?
- Do we know who the executive sponsor is?
- Have we made a preliminary build vs. buy decision?

**2. Definition & Planning**
- Does the team agree on the Definition of Done at the milestone and epic level?
- Are risks logged and owned?
- Is the plan realistic given the resources we actually have?
- Have compliance and security reviews been initiated where required?

**3. Launch & Execution** (ask regularly)
- Is the plan still realistic?
- Are any risks trending toward issues?
- Do stakeholders have what they need to make decisions?
- Is the team blocked on anything I can clear?

**4. Performance & Control**
- The right question here isn't "are we on track" - it's "is our picture of the program still accurate." A plan that nobody trusts isn't a plan.

**5. Program Closure**
- Did we achieve what we set out to do? If not, why not, and what was done about it?

The close-out report goes to the program sponsor and key stakeholders when completed. It should include the lessons learned output and an honest assessment of whether the program achieved its objectives. If it didn't, the report explains why and what was done about it.

### When a Legal / Privacy Review Is Needed

Ask for one when the program includes any of these:
- New products, including mobile apps, SDKs or downloadable components
- New features, or material changes to existing ones, that add third-party integrations or APIs
- Collecting, using or accessing customer data
- Anything involving AI or machine learning
- Changes to infrastructure or to where data is stored
- Pilots and betas

### When Buying Is on the Table

Bring in procurement early, especially for a large purchase. Running a competitive process, where there is more than one possible supplier, also sets up:
1. The security reviews that apply
2. A master agreement
3. An order form, based on the expected usage and the tools required
4. Service definitions, for support or managed services
5. The budget

| Vendor selection step | Owner |
|:---|:---|
| 1. Identify the vendors | Product / program owner |
| 2. Set the evaluation criteria | Product / program owner + engineering |
| 3. Run the RFx (request for proposal, quote or information) | Product / program owner + procurement |
| 4. Score and select | Product / program owner + engineering |
| 5. Audit the vendor | Procurement |
| 6. Onboard, and sign the master services agreement (MSA) | Procurement + legal |
| 7. Sign the statement of work (SOW) | Product / program owner + procurement + legal |

### T-Shirt Sizing

A quick way to estimate work in the planning phase:

| Size | Effort |
|:---|:---|
| N/A | No work required |
| XS | Less than 1 sprint |
| S | 1 sprint |
| M | 1-2 sprints |
| L | 2-4 sprints |
| XL | 4-8 sprints |

### Glossary

| Term | Definition |
|:---|:---|
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
| BCDR | Business Continuity and Disaster Recovery. |
| PRFAQ | A press release and FAQ written before the work starts, describing the finished result as if it had launched. |
| Change Control | Formal process for evaluating and approving changes to program scope, schedule, or budget. |

---

## Alternate Style: A Plain Checklist

Use this when you would rather tick boxes than fill in a table. Copy the block into the program folder.

```markdown
# Program Phases: [Program Name]

## 1. Conception & Initiation
- [ ] (Must) Charter (1-pager) or PRFAQ
- [ ] (Should) Leadership approval for resources and budget, names and date on the charter
- [ ] (Must) Stakeholder register started
- [ ] (Must) Business requirements document
- [ ] (Must) Definition of Done (initial), with baselines
- [ ] (Should) TPM intake request
- [ ] (Must) Program record in the tracking system
- [ ] (Should) Idea reviewed with the executive sponsor and initial stakeholders

## 2. Definition & Planning
- [ ] (Must) Functional / non-functional requirements
- [ ] (Should) Requirements traceability
- [ ] (Must) High Level Design
- [ ] (Should) Low Level Design
- [ ] (Must) RAID log started
- [ ] (Should) Communications plan
- [ ] (Should) Estimates
- [ ] (Should) Resource plan
- [ ] (Should) Program roadmap
- [ ] (Should) Dependency map
- [ ] (Should) Work breakdown / sprint release plan
- [ ] (Must) Definition of Done agreed at milestone and epic level, scope in and out
- [ ] (As needed) Buy vs. build decision record
- [ ] (As needed) Vendor selection
- [ ] (As needed) Vendor SOW / MSA
- [ ] (As needed) Compliance assessment
- [ ] (As needed) Security / architecture review
- [ ] (As needed) Legal / privacy review
- [ ] (Should) Kickoff deck
- [ ] (Must) Kickoff held and recorded
- [ ] (Should) Dependency review with partner teams

## 3. Launch & Execution
- [ ] (Must) Status reports
- [ ] (Must) Leadership / executive updates
- [ ] (Must) RAID log kept current
- [ ] (Must) Milestone / schedule maintenance
- [ ] (Should) Change management plan
- [ ] (Should) Change control log
- [ ] (As needed) UAT plan
- [ ] (As needed) Penetration test
- [ ] (Should) Production release / cutover plan
- [ ] (Should) Operational / support model, runbook
- [ ] (Should) Launch coordination checklist
- [ ] (Must) Weekly team sync
- [ ] (As needed) Steering committee
- [ ] (As needed) Sprint reviews / demos

## 4. Performance & Control
- [ ] (Must) Plan reviewed and updated
- [ ] (Must) Risk and issue review
- [ ] (Should) Metrics review
- [ ] (Should) Dependency review
- [ ] (Should) Resource reforecast
- [ ] (Should) System of record checked
- [ ] (Must) Budget review, against forecast and promised savings
- [ ] (As needed) Compliance / security review follow-up
- [ ] (Should) Transition to BAU plan

## 5. Program Closure
- [ ] (Should) Lessons learned
- [ ] (Should) Close-out report
- [ ] (As needed) Knowledge transfer sessions
- [ ] (Must) Operational / support model signed off
- [ ] (Must) Final budget close-out
- [ ] (Must) Resource release
- [ ] (Must) Program record closed
- [ ] (Should) Executive / stakeholder notification
- [ ] (Must) Team celebration
```

---

*This playbook is version 1.2. Propose edits via pull request or open an issue with your suggested change and the reasoning behind it.*
