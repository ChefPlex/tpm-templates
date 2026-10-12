# RACI Template - Agile

A responsibility matrix for sprint-based teams and programs. Waterfall RACIs map to phases; this one maps to the sprint and release cadence, where ownership shifts fast and the usual failure mode is nobody owning the release once dev is "done."

## When To Use This

- Standing up a new team or program and the Scrum roles don't map cleanly to who actually decides what
- Release readiness keeps surfacing gaps nobody thought they owned
- Multiple teams (or a SAFe train) need one shared view of who's accountable at each ceremony
- Onboarding new team members who don't yet know who to go to for what

Pair this with the [Program Swim Lanes Template](program-swim-lanes-template.md) for multi-team visibility and the [RAID Log Guide](raid-log-guide.md) for what surfaces mid-sprint.

## The Codes

| Code | Meaning |
|---|---|
| **R** - Responsible | Does the work to complete the task. Can be shared across roles. |
| **A** - Accountable | Owns the outcome and signs off. Never more than one per row; exactly one on any row with a real decision or sign-off. |
| **C** - Consulted | Two-way input sought before or during the work. |
| **I** - Informed | Kept updated on progress or outcome. One-way, no input expected. |

## Template

Roles are Scrum defaults - swap in Kanban or SAFe roles as needed (e.g. Release Train Engineer instead of Scrum Master, System Architect instead of Solution Architect). Rows are grouped by cadence; add or cut rows to match your actual ceremonies.

| Activity / Deliverable | Product Owner | Scrum Master | Dev Team | QA/Test | Solution Architect | Release Mgr | Security/Compliance | Stakeholders/Sponsor |
|---|---|---|---|---|---|---|---|---|
| **Program/Release Setup** | | | | | | | | |
| Vision & roadmap | A | C | I | | C | I | | R |
| Release/PI planning | A | R | C | C | C | C | C | C |
| Backlog prioritization | A | C | I | | I | | | C |
| **Sprint Cadence** | | | | | | | | |
| Backlog refinement/grooming | A | R | C | C | C | | | |
| Sprint planning | A | R | R | C | C | I | | |
| Daily standup | | R | R | I | | | | |
| Story/epic definition & acceptance criteria | A | C | R | C | C | | | |
| Development | | | R | I | C | | | |
| Code review | | | R | C | C | | C | |
| **Quality & Review** | | | | | | | | |
| Sprint testing/QA | C | | C | R | | | C | |
| Security scan/review | I | | C | C | C | | R | |
| Sprint review/demo | A | R | R | C | I | I | | C |
| Sprint retrospective | I | A | R | R | | | | |
| **Release** | | | | | | | | |
| Release readiness review | A | R | C | C | C | R | C | I |
| Deployment/release | I | C | C | C | C | A | C | I |
| Post-release monitoring | I | C | R | R | C | A | | I |

## Rules Of Thumb

- Never more than one A per row. Note the deliberate handoff in this template - Product Owner holds A from setup through the sprint review and the release readiness review, then Release Manager takes it for deployment and post-release monitoring. That's the transition teams most often lose track of.
- R can be shared. A cannot.
- Daily standup and development rows lean heavily R with almost no A - that's intentional, not a gap. Not every activity needs a formal accountable owner, only the ones with a real decision or sign-off attached.
- A blank cell is fine. Don't mark every role on every row.
- Revisit at the start of a new PI or when the team composition changes. A RACI built for a 5-person team doesn't survive a SAFe train unmodified.

## Where This Breaks

Agile teams that are already high-trust and co-located sometimes don't need this at all - the ceremonies themselves make ownership visible. Reach for this when the team is new, distributed, scaling past one team, or when release ownership has already caused a miss. Don't add process for its own sake.

**Worked example:** [five rows, weak against better](examples/sample-raci-rows.md), and the test that settles a row.
