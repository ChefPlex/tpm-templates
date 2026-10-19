# Program Swim Lanes Template

When a program has multiple workstreams running in parallel, a swim lane view is one of the clearest ways to show what is happening, who owns it, and where things stand - all at the same time. It gives leadership a single view across the program without requiring them to dig through individual workstream status reports.

A swim lane is a set of tasks grouped because they belong together: they share a theme, the same team is doing them, or they serve the same function. The project plan still holds every task. The swim lane view summarizes those groups, and it is the view you use in steering committee, in executive updates, and in your own weekly check on whether the program is holding together.

---

## How to Use This Template

Each row is a workstream or major initiative within the program. Each column represents a time period, milestone, or status category depending on how you structure it. The intersection shows what is happening in that workstream at that point.

Customize the columns for your program. A security remediation program might organize by vulnerability category. An infrastructure modernization might organize by service or environment. A compliance program might organize by regulatory domain. The structure follows the work.

---

## Part 1: Program Summary

| Field | Detail |
|-------|--------|
| Program Name | |
| TPM | |
| Executive Sponsor | |
| Reporting Period | |
| Overall Status | Green / Yellow / Red |
| Last Updated | |

**Overall Program Status Summary:**
[Two to three sentences on where the program stands, what the key risks are, and what decisions or support are needed from leadership. This is what gets read first.]

---

## Part 2: Swim Lane Status View

Use this view for executive updates and steering committee. Each workstream gets a row. Status is current - update it before every use.

| # | Workstream | Owner | Status | This Period | Next Period | Key Risks / Blockers | Notes |
|---|-----------|-------|--------|-------------|-------------|---------------------|-------|
| 1 | [Workstream name] | | Green / Yellow / Red | [What happened] | [What is next] | | |
| 2 | [Workstream name] | | | | | | |
| 3 | [Workstream name] | | | | | | |
| 4 | [Workstream name] | | | | | | |
| 5 | [Workstream name] | | | | | | |
| 6 | [Workstream name] | | | | | | |

**Status Key:**
- **Green** - On track against plan
- **Yellow** - At risk, with a named owner running it down and a date (or an expected date) to get back to green. One Yellow lane makes the whole program Yellow.
- **Red** - Off track, leadership attention needed, with the path back to green

### Unknown vs Actionable

Here is the same row of the Swim Lane Status View filled in two ways. The first is how it often arrives; the second is what it should say.

| | Workstream | Owner | Status | This Period | Next Period | Key Risks / Blockers | Notes |
|:---|:---|:---|:---|:---|:---|:---|:---|
| **Unknown** | Data migration | Platform | Yellow | Working on it | Continue | Some delays | |
| **Actionable** | Data migration | Dana Ruiz (Platform Eng) | Yellow | 14 of 18 services moved to the new cluster | Last 4 services from Mon, Nov 3, after the change freeze lifts | Payments has no migration window agreed. Path to green: Dana and the Payments lead agree one by Fri, Oct 30 | Program stays Yellow until then |

The actionable row answers who, what, when, where, why and how. A reader knows who owns it, how far along it is, what happens next and when, what is blocking it, and what turns it back to Green. The unknown row tells the reader nothing they can act on.

---

## Part 3: Detailed Workstream Tracker

For each workstream, track the individual action items, owners, and completion status. This is the working-level view - more detail than the swim lane, less detail than the full project plan.

### Workstream 1: [Name]

**Owner:** [Name]
**Status:** Green / Yellow / Red
**Summary:** [One sentence on where this workstream stands]

| # | Action Item | Owner | Status | Target Date | Completion Date | Notes |
|---|------------|-------|--------|-------------|----------------|-------|
| 1a | | | Not Started / In Progress / Complete / Blocked | | | |
| 1b | | | | | | |
| 1c | | | | | | |

### Workstream 2: [Name]

**Owner:** [Name]
**Status:** Green / Yellow / Red
**Summary:** [One sentence on where this workstream stands]

| # | Action Item | Owner | Status | Target Date | Completion Date | Notes |
|---|------------|-------|--------|-------------|----------------|-------|
| 2a | | | | | | |
| 2b | | | | | | |
| 2c | | | | | | |

*[Repeat for each workstream]*

---

## Part 4: Cross-Workstream Dependencies

Dependencies that cut across workstreams are where multi-workstream programs most commonly get into trouble. Track them explicitly.

| Dependency | From Workstream | To Workstream | Due Date | Status | Owner | Notes |
|-----------|----------------|--------------|----------|--------|-------|-------|
| [What is needed] | [Who provides it] | [Who needs it] | | On Track / At Risk / Blocked | | |
| | | | | | | |
| | | | | | | |

---

## Part 5: Milestone Summary

Key milestones across all workstreams in one view. Update status at each reporting period.

| Milestone | Workstream | Owner | Target Date | Status | Actual Date | Notes |
|-----------|-----------|-------|-------------|--------|------------|-------|
| Program Kickoff | All | TPM | | Complete | | |
| [Milestone 1] | | | | | | |
| [Milestone 2] | | | | | | |
| [Milestone 3] | | | | | | |
| Go-Live / Launch | All | TPM | | | | |
| Program Close | All | TPM | | | | |

For a larger program, add the columns you need: what each milestone depends on, the preparation window before it, and how confident the owner is in the date.

---

## A Note on Maintaining This

The swim lane is only useful if it is current. Stale status is worse than no status - it creates false confidence and erodes trust in the reporting.

The right cadence: workstream owners push status to you weekly. You update the master view before each steering committee or executive touchpoint. If an owner is not sending you updates, that is the conversation to have - not a reason to leave the swim lane blank.

The goal is that any stakeholder can look at the swim lane at any point and get an honest picture of where the program stands. If you would not feel comfortable showing it to your executive sponsor right now, update it before you do.

Watch the space between lanes. The real risk often sits there, which is what Part 4, Cross-Workstream Dependencies, is for.

---

*Version 1.0. Propose changes via pull request.*
