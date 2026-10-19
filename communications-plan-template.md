# Communications Plan Template

A communications plan is not a formality. It is the answer to the question every stakeholder eventually asks: "why didn't anyone tell me about this?"

Start with the communications matrix below: one table, one row per communication, so anyone can see what goes out, to whom, how often, and who sends it. When the program needs the stakeholder map, the RACI and the document repository written out together, use the [alternate style](#alternate-style-the-whole-plan-on-one-page) at the bottom of this page.

---

## The Communications Matrix

| Communication Type | Audience | Frequency | Channel | Owner | Format / Notes |
|:---|:---|:---|:---|:---|:---|
| | | | | | |
| | | | | | |
| | | | | | |

For a program with several workstreams, add the columns you need: the workstream each line serves, and the next step or ask it carries.

### What goes in each column

- **Communication Type:** what goes out, such as "Weekly Status Report" or "Risk / Issue Escalation".
- **Audience:** who receives it. Name the groups, and keep the names of the people in the stakeholder map.
- **Frequency:** how often, or what triggers it: weekly, per sprint, at each milestone, as needed.
- **Channel:** where it arrives: email, a meeting, a deck, Slack, the intranet.
- **Owner:** who sends it. One name, not a team.
- **Format / Notes:** the template it follows, and anything the sender needs to remember, such as "bottom line up front, escalations flagged".

---

## How to Fill It In

Define the plan at the start, and keep it simple enough to actually maintain and specific enough to actually be useful.

**Start with the stakeholder map.** Before you plan communications, you need to know who you are communicating with and what they care about. These are not the same thing for every audience. List each group, its role, what it cares about, and how often it needs to hear from you. A starting set of groups is in [Reference](#common-stakeholder-groups). For a larger program, add the columns you need: a named contact for each group, how much influence they have over the outcome, and whether their support today is where you need it to be.

**Then fill in the matrix.** For each communication type, define what it is, who gets it, how often, through what channel, and who owns sending it. A starting set of rows is in [Reference](#common-communication-types); delete the ones the program does not need.

**Give each workstream its own line.** The program-wide status report is not enough when several teams own separate pieces. Each workstream gets a working session with the people who own it, and that session is where its next step and any resource ask come from.

**Decide who does what.** For each communication type, name who sends it, who owns it, who gives input, and who receives it (the RACI in [Reference](#who-does-what-raci-for-communications)). For an escalation, the TPM gets it out on time and the sponsor owns the decision it asks for.

**Pick the status report structure, and keep it.** The weekly status report is your most important recurring communication. Keep it consistent so people know where to look. Keep it honest so people know they can trust it. The recommended structure is in [Reference](#status-report-structure).

**Name one place where documents live.** Every program needs a single location where documents live. Define it at the start and stick to it. Communicate the repository location at kickoff. Put it in every status report header. People will not go looking for it if they do not know it exists.

---

## What to Learn From

### Unknown vs Actionable

The same matrix row, written two ways:

| | Communication Type | Audience | Frequency | Channel | Owner | Format / Notes |
|:---|:---|:---|:---|:---|:---|:---|
| **Unknown** | Status update | Stakeholders | Regularly | Email | TPM | |
| **Actionable** | Weekly Status Report | Executive sponsor, engineering leads, partner-team leads (names in the stakeholder map) | Fridays by 3 pm PT | Email, with a copy in the program repository | [TPM name] | Status color, path to green, decisions needed. So nobody has to ask for status |

The actionable row answers who receives it, what it is, when it goes out, where it lands, who sends it, why it exists and how it is structured. Anyone can check on a Friday afternoon whether it went out.

### Where This Breaks

- **The spreadsheet nobody reads after week two.** Done right, a comms plan means the right people have the right information at the right frequency. Done wrong, it is a plan written at kickoff and never opened again.
- **Answering the same status questions all week.** If you are spending half your week answering status questions, people do not know where to look. Fix the matrix and the repository, not the inbox.
- **Always Green until it suddenly fails.** Call things Yellow or Red when they are Yellow or Red. A program that is always Green until it suddenly fails is a program with a communications problem, not a delivery problem.
- **The escalation buried in the status report.** A risk that needs a decision goes to the person who makes it, directly.

### Principles

A few things that make the difference between a communications plan that works and one that does not.

**Communicate before people ask.** If stakeholders are coming to you for status, you are behind. The goal is that they already have what they need before the question forms.

**Bad news travels early.** A Yellow or Red status flagged early is a problem you can solve together. The same problem flagged late is a crisis. There is no upside to waiting.

**Earn the right to be trusted with bad news.** The habit above compounds. Stakeholders who hear about problems from you first, with a plan already forming, start asking you things before they ask anyone else. Stakeholders who hear about problems from another source start asking you less, and you find out about your own program secondhand.

**Tailor the message to the audience.** Engineers need technical detail and context. Executives need outcomes, risk, and decisions. The underlying facts are the same - how you present them should not be.

**Close the loop.** When a decision gets made, communicate it. When a risk gets resolved, communicate it. When a milestone lands, communicate it. Stakeholders who feel informed stay engaged. Stakeholders who feel out of the loop start asking questions at the wrong level.

**Keep it skimmable.** Nobody has time to read a novel in their inbox. Bottom line up front, detail below for those who need it.

*The reasoning behind several of these is in [TPM craft notes](https://github.com/ChefPlex/learning-notes/blob/main/tpm-craft-notes.md).*

---

## Reference

### Common Stakeholder Groups

| Stakeholder / Group | Role | What They Care About | Engagement Level | Notes |
|:---|:---|:---|:---|:---|
| Executive Sponsor | Decision authority, budget approval | Outcomes, risk, schedule | Low frequency / high signal | Escalation path for blockers |
| Engineering Lead(s) | Technical delivery | Technical direction, blockers, dependencies | High frequency | Day-to-day working partner |
| Product / Program Owner | Requirements and scope | Progress against Definition of Done, scope changes | High frequency | Co-owner of program |
| Partner Teams | Dependency owners | What you need from them and when | Medium frequency | Flag dependencies early |
| Compliance / Legal / Security | Risk and review | Milestone gates, regulatory exposure | At key milestones | Engage early, not at the end |
| End Users / Customers | Impacted by the change | What is changing, when, and what they need to do | Pre-launch and at launch | Coordinate with comms / change management team |

**Engagement Level Guide:**
- **High frequency** - Weekly or sprint cadence, actively involved in delivery
- **Medium frequency** - Bi-weekly or monthly, needs regular visibility
- **Low frequency / high signal** - Monthly or milestone-based, gets the summary not the detail
- **As needed** - Engaged at specific decision points or when something affects them

### Common Communication Types

| Communication Type | Audience | Frequency | Channel | Owner | Format / Notes |
|:---|:---|:---|:---|:---|:---|
| Weekly Status Report | Program stakeholders, leadership | Weekly | Email | TPM | See [status report structure](#status-report-structure) |
| Executive Steering Update | Executive sponsor, senior leadership | Monthly or at milestones | Deck / Meeting | TPM + PO | Bottom line up front, escalations flagged |
| Team Sync | Core delivery team | Weekly | Video / in person | TPM | Working session - blockers, dependencies, decisions |
| Workstream Working Session | The people who own that workstream | Weekly, daily when it is moving fast | Video / in person | TPM | One per workstream: the recommended action, where it stands, and the next step or resource ask |
| Sprint Review / Demo | Stakeholders, product team | Per sprint | Video / in person | Engineering Lead + TPM | Show the work, get feedback |
| Milestone Announcement | All stakeholders | At each milestone | Email | TPM | Celebrate progress, signal what is next |
| Risk / Issue Escalation | Executive sponsor, relevant leaders | As needed | Direct communication | TPM | Do not bury this in the status report |
| Launch / Go-Live Communication | End users, impacted teams | Pre-launch and at launch | Email / Slack / intranet | TPM + Comms | Coordinate with change management |
| Program Close-Out | All stakeholders | At program close | Email + close-out report | TPM | Thank the team, document outcomes |

### Who Does What: RACI for Communications

| Communication Type | Responsible (sends it) | Accountable (owns it) | Consulted (input) | Informed (receives it) |
|:---|:---|:---|:---|:---|
| Weekly Status Report | TPM | TPM | PO | All stakeholders |
| Executive Steering Update | TPM | Executive Sponsor | PO, Engineering Lead | Leadership |
| Team Sync | TPM | TPM | Core team | Core team |
| Risk / Issue Escalation | TPM | TPM (gets it out on time; the sponsor owns the decision it asks for) | Relevant leads | Executive Sponsor, affected parties |
| Launch Communication | TPM | PO | Comms, Legal | All impacted |

### Status Report Structure

```
PROGRAM: [Program Name]
WEEK ENDING: [Date]
STATUS: Green / Yellow / Red
PATH TO GREEN (if Yellow or Red): [what is being done, owner, date - or when you expect to have a date]

ONE-LINE SUMMARY
[What is the most important thing to know this week - one sentence]

THIS WEEK
- [What was completed or progressed]
- [Key decisions made]

NEXT TWO WEEKS
- [What is planned]
- [Key milestones coming up]

RISKS / ISSUES
- [Any active risks or issues requiring visibility - flag early, not late]

DECISIONS NEEDED
- [Any decisions you need from leadership or stakeholders]

DEPENDENCIES
- [Any dependencies at risk]
```

**On status color:**
- **Green** - On track. No action needed from leadership.
- **Yellow** - At risk. Specific issue identified, with a named owner running it down. Give a date to get back to green; if it is too early for a firm one, say when you expect to have it. Early dates are estimates and may move.
- **Red** - Off track. Leadership attention required. Come with the path back to green and what you need from leadership.

### Where Documents Live

| Document Type | Location | Owner | Access |
|:---|:---|:---|:---|
| Program Charter | [Link] | TPM | All stakeholders |
| RAID Log | [Link] | TPM | Core team |
| Status Reports | [Link] | TPM | All stakeholders |
| Technical Design Docs | [Link] | Engineering Lead | Core team + reviewers |
| Meeting Notes | [Link] | TPM | Core team |
| Launch / Release Plan | [Link] | TPM | All stakeholders |

---

## Alternate Style: The Whole Plan on One Page

Use this when the program needs the full plan in one document. Copy the block into a new file in the program repository and link it from the status report header.

```markdown
# Communications Plan: [Program Name]

| Field | Detail |
|:---|:---|
| Program Name | |
| TPM | |
| Version | 1.0 |
| Last Updated | |

## Stakeholder Map
| Stakeholder / Group | Role | What They Care About | Engagement Level | Notes |
|:---|:---|:---|:---|:---|
| | | | | |

## Communications Matrix
| Communication Type | Audience | Frequency | Channel | Owner | Format / Notes |
|:---|:---|:---|:---|:---|:---|
| | | | | | |

## RACI for Communications
| Communication Type | Responsible (sends it) | Accountable (owns it) | Consulted (input) | Informed (receives it) |
|:---|:---|:---|:---|:---|
| | | | | |

## Status Report Structure
[Paste the structure from Reference, or link to it]

## Document Repository
| Document Type | Location | Owner | Access |
|:---|:---|:---|:---|
| | | | |
```

---

*Template version 1.1. Propose changes via pull request.*
