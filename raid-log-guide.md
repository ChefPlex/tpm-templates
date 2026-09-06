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
| Mitigation Plan | What we are doing to reduce probability or impact |
| Status | Open / Mitigated / Closed |
| Date Raised | When it was logged |
| Target Close Date | When we expect to resolve or accept it |

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

### The Difference Between a Risk and an Issue

A risk is "our key engineering lead might leave the program." An issue is "our key engineering lead left the program last week." One requires monitoring and mitigation planning. The other requires a resolution plan right now.

Don't let issues sit in the risk column because it feels better. Call them what they are.

---

## Dependencies

A dependency is something this program needs from somewhere else - another team, a vendor, a regulatory body, an upstream system. Dependencies are not risks yet, but unmanaged dependencies become risks fast.

### Key Fields

| Field | What Goes Here |
|-------|---------------|
| Dependency ID | Sequential identifier (D1, D2...) |
| Description | What this program needs and from whom |
| Type | Internal (another team) / External (vendor, regulator, customer) |
| Owner | Who on your team is tracking this dependency |
| External Contact | Who owns it on the other side |
| Due Date | When you need it delivered to stay on schedule |
| Impact if Late | What happens to the program if this slips |
| Status | On Track / At Risk / Blocked / Complete |

### Managing Dependencies Well

Identify dependencies during planning, not during execution. Every dependency should have a named owner on your side and a named contact on the other side. Status gets reviewed regularly - "I haven't heard back" isn't the same as "on track." When a dependency is at risk, escalate early. Waiting for the other team to tell you they're behind isn't a dependency management strategy.

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

A link to a working RAID log spreadsheet template is available in the [tpm-toolbox](https://github.com/ChefPlex/tpm-toolbox) repo.

---

*Version 1.0. Propose changes via pull request.*
