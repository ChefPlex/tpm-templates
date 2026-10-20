# Program Swim Lanes Template

When a program has multiple workstreams running in parallel, the first thing to get right is how the work is cut up: which lanes there are, what each one covers, who owns it, and where the lanes touch. This template defines the lanes. Write it during planning, and revisit it when the structure changes, not every week.

Start with the lane table below: one row per lane. When the program needs the lanes, the dependencies between them, the parked work and the owner changes in one document, use the [alternate style](#alternate-style-the-whole-structure-on-one-page) at the bottom of this page.

---

## Swim Lanes - [Program Name]

| # | Workstream | What it covers, and what it doesn't | Owner | Teams involved | Dependencies | Definition of Done | Date Completed |
|:---|:---|:---|:---|:---|:---|:---|:---|
| 1 | | | | | | | |
| 2 | | | | | | | |
| 3 | | | | | | | |

### What goes in each column

- **#:** the lane number. Action items in the tracker and sections of the status report use it, such as 1a, 1b.
- **Workstream:** the name of the lane.
- **What it covers, and what it doesn't:** the scope of the lane, and the nearby work that belongs to another lane or to nobody.
- **Owner:** the person who runs the lane and reports its status. A name, not a team.
- **Teams involved:** who does the work in this lane.
- **Dependencies:** other lanes, teams or decisions this lane is waiting on.
- **Definition of Done:** the DoD for the lane, its finish line, specific enough that anyone can tell whether it has been crossed.
- **Date Completed:** the date the Definition of Done was met. Blank until then.

---

## How to Fill It In

**Decide what a lane is.** A swim lane is a set of tasks grouped because they belong together: they share a theme, the same team is doing them, or they serve the same function. The project plan still holds every task. The lanes are how you summarize those groups in steering committee, in executive updates, and in your own weekly check on whether the program is holding together.

**Let the structure follow the work.** A security remediation program might organize by vulnerability category. An infrastructure modernization might organize by service or environment. A compliance program might organize by regulatory domain.

**Track the dependencies between lanes.** Dependencies that cut across workstreams are where multi-workstream programs most commonly get into trouble. Track them explicitly: what is needed, which lane provides it, which one needs it, by when, and who owns it.

**Park what is out of this priority.** Work that is real but not in the current priority goes in a separate parked list, not out of the program. It comes back when the priority changes.

**Report status somewhere else.** Status by lane belongs in the weekly [status report](https://github.com/ChefPlex/program-reporting-frameworks/blob/main/program-status-reporting-framework.md), using the lane numbers. Action items belong in the tracker, and milestones in the charter and project plan. This table changes only when the lanes do.

---

## What to Learn From

### Unknown vs Actionable

The same lane, defined two ways:

| | # | Workstream | What it covers, and what it doesn't | Owner | Teams involved | Dependencies | Definition of Done | Date Completed |
|:---|:---|:---|:---|:---|:---|:---|:---|:---|
| **Unknown** | 3 | Data migration | Migration work | Platform | | | Finished | |
| **Actionable** | 3 | Data migration | Moving the 18 services to the new cluster, so the old one can be retired. Not the payments ledger, which stays until year end | Dana Ruiz (Platform Eng) | Platform Eng, Payments, SRE | Lane 1 (new cluster built); a migration window agreed with Payments | All 18 services serving from the new cluster and the old cluster drained, by Fri, Nov 21 | |

The actionable row answers who owns it, what it covers and does not, when it should finish, where the work happens, why it exists and how anyone will know it is done. The unknown row could describe almost any migration.

### Where This Breaks

- **The same status in three documents.** If the lane table carries This Week and Next Week, it becomes a second status report that someone has to keep in step with the first. Keep status in the status report.
- **Lanes with no edges.** If "what it doesn't cover" is blank, work falls between lanes and nobody owns it.
- **Risk between the lanes.** Watch the space between lanes. The real risk often sits there, which is what the Dependencies column and the dependency table are for.
- **An owner who leaves with no handoff.** When a lane owner moves on, record who takes over and where the walkthrough or write-up lives.
- **Lanes that never change.** If the program has pivoted and the lanes have not, the structure is describing a program that no longer exists. Revisit it when the work changes shape.

---

## Alternate Style: The Whole Structure on One Page

Use this when the program needs the lanes, the dependencies between them, the parked work and the owner changes in one document. Copy the block into the program folder.

```markdown
# Program Swim Lanes: [Program Name]

| Field | Detail |
|:---|:---|
| Program Name | |
| TPM | |
| Executive Sponsor | |
| Last Updated | |

## Lanes

| # | Workstream | What it covers, and what it doesn't | Owner | Teams involved | Dependencies | Definition of Done | Date Completed |
|:---|:---|:---|:---|:---|:---|:---|:---|
| 1 | | | | | | | |
| 2 | | | | | | | |
| 3 | | | | | | | |

## Cross-Workstream Dependencies

| Dependency | From Workstream | To Workstream | Due Date | Status | Owner | Notes |
|:---|:---|:---|:---|:---|:---|:---|
| [What is needed] | [Who provides it] | [Who needs it] | | On Track / At Risk / Blocked | | |

## Parked - Not in This Priority

| Item | Lane | Why It Is Parked | Revisit When |
|:---|:---|:---|:---|
| | | | |

## Lane Owner Changes

| Lane | From | To | Date | Handoff (walkthrough or write-up) |
|:---|:---|:---|:---|:---|
| | | | | |
```

---

*Version 1.2. Propose changes via pull request.*

*Part of the [ChefPlex TPM portfolio](PORTFOLIO-GUIDE.md). Maintained by [Eric White](https://www.linkedin.com/in/edwhite). Licensed under [CC BY 4.0](LICENSE).*
