# RACI Template — Waterfall

A responsibility matrix for phase-gated programs. Use it to settle who does the work, who owns the outcome, who gets consulted, and who just needs to know — before the ambiguity turns into a missed handoff.

## When To Use This

- Kicking off a phase-gated program and ownership across phases isn't settled yet
- Sign-off keeps stalling because nobody agrees who the actual approver is
- A phase transition (design to build, build to test, test to deploy) has caused rework before
- Leadership or audit needs a documented ownership record, not just a verbal understanding

Pair this with the [Program Charter Template](program-charter-template.md) at kickoff and the [RAID Log Guide](raid-log-guide.md) during execution.

## The Codes

| Code | Meaning |
|---|---|
| **R** — Responsible | Does the work to complete the task. Can be shared across roles. |
| **A** — Accountable | Owns the outcome and signs off. Exactly one per row, no exceptions. |
| **C** — Consulted | Two-way input sought before or during the work. |
| **I** — Informed | Kept updated on progress or outcome. One-way, no input expected. |

## Template

Roles across the top are a starting set — rename or add columns to match your program. Rows are grouped by phase; add or cut rows to match your actual gates.

| Activity / Deliverable | Sponsor | Program/Project Mgr | Business Analyst | Solution Architect | Dev Lead | QA Lead | Security/Compliance | Change Mgmt | End Users/Stakeholders |
|---|---|---|---|---|---|---|---|---|---|
| **Initiation** | | | | | | | | | |
| Business case & charter | A | R | C | I | I | I | C | I | C |
| Stakeholder identification | I | R | C | I | I | I | I | C | A |
| Budget & resource approval | A | R | C | C | I | I | I | I | I |
| **Requirements** | | | | | | | | | |
| Requirements gathering | I | A | R | C | C | C | C | I | R |
| Requirements sign-off | A | R | R | C | I | I | C | I | C |
| Scope baseline | A | R | C | C | C | I | I | I | I |
| **Design** | | | | | | | | | |
| Solution/technical design | I | A | C | R | C | C | C | I | I |
| Design review & approval | A | R | C | R | C | C | C | I | I |
| Security/architecture review | I | A | I | C | C | C | R | I | I |
| **Development** | | | | | | | | | |
| Build/development | I | A | I | C | R | I | I | I | I |
| Code review | I | I | I | C | R | C | C | I | I |
| Unit testing | I | A | I | I | R | C | I | I | I |
| **Testing** | | | | | | | | | |
| Test plan development | I | A | C | C | C | R | C | I | I |
| System integration testing | I | A | C | C | C | R | C | I | I |
| UAT execution & sign-off | A | R | C | I | I | C | I | I | R |
| Defect resolution | I | A | I | C | R | R | I | I | I |
| **Deployment** | | | | | | | | | |
| Deployment/release plan | A | R | I | C | C | C | C | R | I |
| Go-live execution | A | R | I | C | R | C | C | C | I |
| Post-launch support/hypercare | I | A | I | C | R | R | I | C | I |
| **Closure** | | | | | | | | | |
| Lessons learned | I | A | R | R | R | R | C | C | I |
| Project closure & sign-off | A | R | C | I | I | I | I | I | I |

## Rules Of Thumb

- One A per row. If two roles both think they're accountable, that's the conversation to have before the program starts, not after something slips.
- R can be shared. A cannot.
- A blank cell is fine. Don't mark every role on every row just to fill the grid — that's the fastest way to make the matrix meaningless.
- If a row has zero A's or more than one, fix it before you circulate the matrix. It's not a formatting issue, it's an unresolved ownership question.
- Revisit this at each phase gate, not just at kickoff. Roles that made sense in Design often don't hold in Deployment.

## Where This Breaks

A RACI doesn't replace the conversation, it documents the outcome of one. If people are filling this in without talking to each other, you'll get a grid that looks aligned and isn't. Use it to force the conversation, not to skip it.
