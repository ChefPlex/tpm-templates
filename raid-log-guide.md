# The RAID Log: What It Is, Why It Matters, and How to Use It

If you're running a program and you don't have a RAID log, you're keeping all of that information in your head or in someone's inbox. That works fine until it doesn't - and it usually stops working at the worst possible moment.

A RAID log is not a bureaucratic checkbox. It is the operational memory of your program. Done right, it's the single place where anyone on the team can find out what risks are being watched, what is currently broken, what decisions have been made and why, and what the program is waiting on. That transparency is what keeps small problems from becoming expensive surprises.

---

## What RAID Stands For

| Letter | Category | The Question It Answers |
|--------|----------|------------------------|
| **R** | Risks | What could go wrong, and what are we doing about it? |
| **A** | Assumptions | What are we treating as true that we haven't verified? |
| **I** | Issues | What has already gone wrong and needs resolution? |
| **D** | Dependencies | What is this program waiting on from somewhere else? |

Some teams extend this to RAIDO or RAAID by adding Opportunities or Actions. Use whatever serves your program - the categories matter less than the habit of logging and reviewing.

---

## Risks

A risk is something that has not happened yet but could. The job is to catch it early, assess it honestly, and have a plan before it becomes an issue.

### Key Fields

| Field | What Goes Here |
|-------|---------------|
| Risk ID | Sequential identifier (R1, R2...) |
| Description | What could happen and what the impact would be |
| Category | Technical / Schedule / Budget / Operational / External |
| Probability | High / Medium / Low |
| Impact | High / Medium / Low |
| Risk Rating | Derived from probability x impact |
| Owner | One person - not a team, not "TBD" |
| Proximity | How soon it would land if it landed - This Sprint / This Quarter / Later |
| Strategy | Avoid / Mitigate / Transfer / Accept |
| Mitigation Plan | What we are doing to reduce probability or impact |
| Status | Open / In Progress / Mitigated / Closed |
| Date Raised | When it was logged |
| Target Close Date | When we expect to resolve or accept it |
| Date Closed | When it was actually resolved or accepted |
| Notes | Anything the other fields do not hold |

### Risk Categories

- **Technical** - Requirements gaps, technology choices, integration complexity, performance, quality
- **Schedule** - Estimation errors, resource availability, scope creep, external timelines
- **Budget** - Cost overruns, unplanned scope, vendor pricing changes
- **Operational** - Resource planning, roles and responsibilities, team communication, skill gaps
- **External** - Customer dependencies, vendor or partner reliability, legal and regulatory changes

### How to Rate Risks

Use a simple probability x impact matrix. A high-probability, high-impact risk is your top priority. A low-probability, low-impact risk goes on the log but doesn't need weekly attention.

```
             Impact
             Low    Med    High
Probability
High          4      7      9
Med           2      5      8
Low           1      3      6
```

Anything rated 7 or above gets active mitigation and regular review. Everything else gets monitored.

### Proximity: The Field That Sets Your Review Cadence

Rating tells you how much a risk matters. Proximity tells you when. A high-rated risk that can't land until next quarter and a medium-rated risk that could land this sprint need different attention this week, and a probability x impact matrix can't tell them apart. Log proximity as This Sprint, This Quarter, or Later, and let it drive which risks get airtime in the weekly review.

### Strategy: Decide Before You Plan

Before you write a mitigation plan, say which of the four things you are actually doing.

- **Avoid** - change the plan so the risk cannot occur
- **Mitigate** - reduce the probability or the impact
- **Transfer** - move the exposure to someone better placed to carry it, such as a vendor, an insurer, or a partner team
- **Accept** - decide to live with it, on the record, with a named owner

Most logs skip straight to a mitigation plan, which quietly assumes the strategy is always Mitigate. It is not. "We accepted this, and here is who signed up for it" is a legitimate entry, and writing it down is what stops the same risk being re-litigated every month.

### What Good Risk Management Looks Like

Risks get logged as soon as they're identified - not after they become issues. Every risk has a named owner and a mitigation plan that's actually being worked. The log gets reviewed at a regular cadence, not just when something goes wrong. When a risk is resolved or accepted, it gets closed with a note on how it was handled.

---

## Assumptions

An assumption is something you're treating as true without having confirmed it. Every program runs on assumptions. The ones that hurt are the ones nobody wrote down.

### Key Fields

| Field | What Goes Here |
|-------|---------------|
| Assumption ID | Sequential identifier (A1, A2...) |
| Description | What we are assuming to be true |
| Reason | Why we made this assumption |
| Validation Action | How we will confirm or disprove it |
| Impact if Wrong | What happens to the program if this assumption turns out to be false |
| Owner | Who is responsible for validating it |
| Status | Open / Validated / Invalidated / Closed |
| Date Raised | When it was logged |
| Date Closed | When it was validated, invalidated, or retired |
| Notes | Anything the other fields do not hold |

### Common Assumptions Worth Writing Down

- Required team members will be available at the planned allocations
- Partner teams have capacity to support this program in the expected timeframe
- The technical approach will work at the scale required
- Regulatory requirements will not change materially during the program
- Budget approval will be in place by a specific date

The test for whether something belongs in the Assumptions log: if it turned out to be wrong, would it change the plan? If yes, write it down.

---

## Issues

An issue is a risk that happened. Something is wrong right now and needs to be resolved. Issues aren't the same as risks - they're active problems that need active owners and active resolution plans.

### Key Fields

| Field | What Goes Here |
|-------|---------------|
| Issue ID | Sequential identifier (I1, I2...) |
| Description | What happened and what the impact is |
| Category | Technical / Schedule / Budget / Operational / External |
| Priority | High / Medium / Low |
| Owner | One person responsible for driving resolution |
| Resolution Plan | Specific steps being taken to resolve it |
| Status | Open / In Progress / Resolved / Closed |
| Date Raised | When it was logged |
| Target Resolution Date | When we expect it to be resolved |
| Date Closed | When it was actually resolved |
| Linked Risk ID | The risk this issue came from, if you logged one |
| Notes | Anything the other fields do not hold |

### The Difference Between a Risk and an Issue

A risk is "our key engineering lead might leave the program." An issue is "our key engineering lead left the program last week." One requires monitoring and mitigation planning. The other requires a resolution plan right now.

Don't let issues sit in the risk column because it feels better. Call them what they are.

When you convert a risk into an issue, put the risk ID in the Linked Risk ID field. That one column is what lets you answer two questions at program close that are otherwise unanswerable: which risks we saw coming and failed to stop, and which issues arrived with no warning at all. The first list is a mitigation problem. The second is an identification problem. They have different fixes, and without the link you can't tell which one you have.

---

## Dependencies

A dependency is something this program needs from somewhere else - another team, a vendor, a regulatory body, an upstream system.

Dependencies are risks that have not activated yet. That's not a turn of phrase, it's the reason the log rates them the same way it rates risks: every dependency carries a likelihood that it slips and an impact if it does. Treat the dependency register as a risk register you happen to have named the owner of, and the escalation decisions get easier.

### Key Fields

| Field | What Goes Here |
|-------|---------------|
| Dependency ID | Sequential identifier (D1, D2...) |
| Description | What this program needs and from whom |
| Type | Internal (another team) / External (vendor, regulator, customer) |
| What We Need | The specific deliverable, not the team name |
| Owner | Who on your team is tracking this dependency |
| External Contact | Who owns it on the other side |
| Due Date | When you need it delivered to stay on schedule |
| Likelihood | High / Medium / Low - how likely it is to slip |
| Impact if Late | What happens to the program if this slips |
| Impact | High / Medium / Low - the rated version of the line above |
| Status | On Track / At Risk / Blocked / Complete |
| Notes | Anything the other fields do not hold |

### Managing Dependencies Well

Identify dependencies during planning, not during execution. Every dependency should have a named owner on your side and a named contact on the other side, and the What We Need field should name the deliverable rather than the team. "Waiting on Security" is not trackable. "Waiting on the signed threat model for the payments path" is, and the difference shows up the first time you have to escalate. Status gets reviewed regularly - "I haven't heard back" isn't the same as "on track." When a dependency is at risk, escalate early. Waiting for the other team to tell you they're behind isn't a dependency management strategy.

---

## How to Run the RAID Log

### Starting Out

Set up the log at the beginning of the program, during the Definition & Planning phase. Run a session with the core team to brainstorm an initial list of risks, call out the assumptions you're all working from, and map the dependencies. You won't catch everything in that first session - the goal is to build the habit and get the obvious ones on paper.

### Keeping It Current

Review the RAID log at a regular cadence - weekly for high-velocity programs, bi-weekly for steadier ones. The review does not need to be long. Ten minutes at the end of your weekly team sync is enough to check status, add new items, and close out anything resolved.

The RAID log dies when it stops getting reviewed. A stale RAID log is worse than no RAID log - it creates false confidence.

### Escalating From the Log

The RAID log is your early warning system. When a risk moves from medium to high, escalate before it becomes an issue. When an issue has no resolution in sight, escalate before it becomes a crisis. The log should make it easy to tell the difference between "we're watching this" and "we need leadership attention on this now."

### Closing Items

When a risk is resolved or accepted, close it with a note. When an issue is resolved, document how. When an assumption is validated or disproven, update the status and note the impact. A well-maintained RAID log at program close is a useful artifact for the lessons learned session and for the next TPM who runs a similar program.

---

## RAID Log in the Program Ecosystem

The RAID log does not exist in isolation. Risks that cross a threshold get called out in status reports. Dependencies that are at risk get flagged in steering committee updates. Decisions made to close out issues get logged in the Decisions register. The RAID log feeds everything else - treat it accordingly.

---

## A Note on Tools

The RAID log can live in a spreadsheet, a wiki, a project management tool, or any other system your team will actually use. The format matters less than the discipline. Pick something lightweight enough that people will update it without being asked, and structured enough that you can pull a meaningful status from it at any time.

A working RAID log spreadsheet template is in the [tpm-toolbox](https://github.com/ChefPlex/tpm-toolbox) repo, along with a [markdown version](https://github.com/ChefPlex/tpm-toolbox/blob/main/raid-log-template.md) for teams that keep their program docs in a wiki or a git repo. Both carry the same fields as this guide.

The spreadsheet opens on a Summary tab that reads across the four logs. It's the view to put on the screen in a steering committee, because it answers "what is the state of this program" without anyone scrolling through a hundred rows.

---

*Version 1.0. Propose changes via pull request.*
