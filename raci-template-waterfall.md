# RACI Template - Waterfall

A responsibility matrix for phase-gated programs. Use it to settle who does the work, who owns the outcome, who gets consulted, and who just needs to know - before the ambiguity turns into a missed handoff.

## When To Use This

- Kicking off a phase-gated program and ownership across phases isn't settled yet
- Sign-off keeps stalling because nobody agrees who the actual approver is
- A phase transition (design to build, build to test, test to deploy) has caused rework before
- Leadership or audit needs a documented ownership record, not just a verbal understanding

Pair this with the [Program Charter Template](program-charter-template.md) at kickoff and the [RAID Log Guide](raid-log-guide.md) during execution.

The assignments below are a starting point. Who is accountable depends on the organization: on one program the product manager owns requirements, on another the business analyst does. Change the cells to match who actually decides.

## The Codes

| Code | Meaning |
|---|---|
| **R** - Responsible | Does the work to complete the task. Can be shared across roles. |
| **A** - Accountable | Owns the outcome and signs off. Never more than one per row; exactly one on any row with a real decision or sign-off. |
| **C** - Consulted | Two-way input sought before or during the work. |
| **I** - Informed | Kept updated on progress or outcome. One-way, no input expected. |

## Template

Roles across the top are a starting set - rename or add columns to match your program. Rows are grouped by phase; add or cut rows to match your actual gates.

| Activity / Deliverable | Sponsor | Program/Project Mgr | Business Analyst | Solution Architect | Dev Lead | QA Lead | Security/Compliance | Change Mgmt | End Users/Stakeholders |
|---|---|---|---|---|---|---|---|---|---|
| **Initiation** | | | | | | | | | |
| Business case & charter | A | R | C | I | | | C | | C |
| Stakeholder identification | I | A/R | C | | | | | C | C |
| Budget & resource approval | A | R | C | C | I | I | | | |
| **Requirements** | | | | | | | | | |
| Requirements gathering | | C | A/R | C | C | C | C | I | R |
| Requirements sign-off | C | R | A/R | C | I | I | C | I | C |
| Scope baseline | A | R | C | C | C | I | | I | I |
| **Design** | | | | | | | | | |
| Solution/technical design | | C | C | A/R | C | C | C | | |
| Design review & approval | I | R | C | A/R | C | C | C | | |
| Security/architecture review | | C | | C | C | C | A/R | | |
| **Development** | | | | | | | | | |
| Build/development | | I | | C | A/R | I | | | |
| Code review | | | | C | A/R | C | C | | |
| Unit testing | | | | | A/R | C | | | |
| **Testing** | | | | | | | | | |
| Test plan development | | C | C | C | C | A/R | C | | |
| System integration testing | | I | C | C | C | A/R | C | | |
| UAT execution & sign-off | I | R | C | | I | C | | I | A/R |
| Defect resolution | | I | | C | A/R | R | | | |
| **Deployment** | | | | | | | | | |
| Deployment/release plan | I | A/R | I | C | C | C | C | R | I |
| Go/no-go decision | A | R | I | C | C | C | C | C | I |
| Go-live execution | I | A | I | C | R | C | C | C | I |
| Post-launch support/hypercare | I | C | | C | A/R | R | | C | I |
| **Closure** | | | | | | | | | |
| Lessons learned | I | A | R | R | R | R | C | C | |
| Project closure & sign-off | A | R | C | I | I | I | | | I |

## Rules Of Thumb

- Never more than one A per row. If two roles both think they're accountable, that's the conversation to have before the program starts, not after something slips.
- R can be shared. A cannot. Where one role both does the work and owns it, write A/R.
- The sponsor holds A only where money, scope or the go/no-go is decided: business case, budget, scope baseline, go/no-go and closure. Everywhere else the sponsor is I or C, which is what makes the A mean something ([worked example](examples/sample-raci-rows.md)).
- The PM is accountable for the schedule, the gates, and the decisions that cross teams, not for the work itself. Build, test, and design are owned by the people who can actually do them.
- A blank cell is fine. Don't mark every role on every row just to fill the grid - that's the fastest way to make the matrix meaningless.
- If a row has zero A's or more than one, fix it before you circulate the matrix. A row like that is an unresolved ownership question.
- Revisit this at each phase gate, not just at kickoff. Roles that made sense in Design often don't hold in Deployment.

## Where This Breaks

A RACI doesn't replace the conversation, it documents the outcome of one. If people are filling this in without talking to each other, you'll get a grid that looks aligned and isn't. Use it to force the conversation, not to skip it.

**Worked example:** [five rows, unknown against actionable](examples/sample-raci-rows.md), and the test that settles a row.
