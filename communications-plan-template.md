# Communications Plan Template

A communications plan is not a formality. It is the answer to the question every stakeholder eventually asks: "why didn't anyone tell me about this?"

Done right, a comms plan means the right people have the right information at the right frequency - and you are not spending half your week answering the same status questions because nobody knew where to look. Done wrong, it is a spreadsheet that nobody reads after week two.

The goal is a plan that is simple enough to actually maintain and specific enough to actually be useful.

---

## Document Control

| Field | Detail |
|-------|--------|
| Program Name | |
| TPM | |
| Version | 1.0 |
| Last Updated | |

---

## Part 1: Stakeholder Map

Before you plan communications, you need to know who you are communicating with and what they care about. These are not the same thing for every audience.

| Stakeholder / Group | Role | What They Care About | Engagement Level | Notes |
|--------------------|------|---------------------|-----------------|-------|
| Executive Sponsor | Decision authority, budget approval | Outcomes, risk, schedule | Low frequency / high signal | Escalation path for blockers |
| Engineering Lead(s) | Technical delivery | Technical direction, blockers, dependencies | High frequency | Day-to-day working partner |
| Product / Program Owner | Requirements and scope | Progress against Definition of Done, scope changes | High frequency | Co-owner of program |
| Partner Teams | Dependency owners | What you need from them and when | As needed | Flag dependencies early |
| Compliance / Legal / Security | Risk and review | Milestone gates, regulatory exposure | At key milestones | Engage early, not at the end |
| End Users / Customers | Impacted by the change | What is changing, when, and what they need to do | Pre-launch and at launch | Coordinate with comms / change management team |
| [Add rows as needed] | | | | |

**Engagement Level Guide:**
- **High frequency** - Weekly or sprint cadence, actively involved in delivery
- **Medium frequency** - Bi-weekly or monthly, needs regular visibility
- **Low frequency / high signal** - Monthly or milestone-based, gets the summary not the detail
- **As needed** - Engaged at specific decision points or when something affects them

---

## Part 2: Communications Matrix

The core of the plan. For each communication type, define what it is, who gets it, how often, through what channel, and who owns sending it.

| Communication Type | Audience | Frequency | Channel | Owner | Format / Notes |
|-------------------|----------|-----------|---------|-------|---------------|
| Weekly Status Report | Program stakeholders, leadership | Weekly | Email | TPM | See status report template |
| Executive Steering Update | Executive sponsor, senior leadership | Monthly or at milestones | Deck / Meeting | TPM + PO | Bottom line up front, escalations flagged |
| Team Sync | Core delivery team | Weekly | Video / in person | TPM | Working session - blockers, dependencies, decisions |
| Sprint Review / Demo | Stakeholders, product team | Per sprint | Video / in person | Engineering Lead + TPM | Show the work, get feedback |
| Milestone Announcement | All stakeholders | At each milestone | Email | TPM | Celebrate progress, signal what is next |
| Risk / Issue Escalation | Executive sponsor, relevant leaders | As needed | Direct communication | TPM | Do not bury this in the status report |
| Launch / Go-Live Communication | End users, impacted teams | Pre-launch and at launch | Email / Slack / intranet | TPM + Comms | Coordinate with change management |
| Program Close-Out | All stakeholders | At program close | Email + close-out report | TPM | Thank the team, document outcomes |
| [Add rows as needed] | | | | | |

---

## Part 3: RACI for Communications

Who is responsible for each communication type.

| Communication Type | Responsible (sends it) | Accountable (owns it) | Consulted (input) | Informed (receives it) |
|-------------------|----------------------|----------------------|------------------|----------------------|
| Weekly Status Report | TPM | TPM | PO | All stakeholders |
| Executive Steering Update | TPM | Executive Sponsor | PO, Engineering Lead | Leadership |
| Team Sync | TPM | TPM | Core team | Core team |
| Risk / Issue Escalation | TPM | Executive Sponsor | Relevant leads | Affected parties |
| Launch Communication | TPM | PO | Comms, Legal | All impacted |

---

## Part 4: Status Report Structure

The weekly status report is your most important recurring communication. Keep it consistent so people know where to look. Keep it honest so people know they can trust it.

**Recommended structure:**

```
PROGRAM: [Program Name]
WEEK ENDING: [Date]
STATUS: Green / Yellow / Red

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
- **Yellow** - At risk. Specific issue identified, mitigation in progress, may need support.
- **Red** - Off track. Leadership attention required. Come with a plan, not just the problem.

Call things Yellow or Red when they are Yellow or Red. A program that is always Green until it suddenly fails is a program with a communications problem, not a delivery problem.

---

## Part 5: Document Repository

Every program needs a single location where documents live. Define it at the start and stick to it.

| Document Type | Location | Owner | Access |
|--------------|----------|-------|--------|
| Program Charter | [Link] | TPM | All stakeholders |
| RAID Log | [Link] | TPM | Core team |
| Status Reports | [Link] | TPM | All stakeholders |
| Technical Design Docs | [Link] | Engineering Lead | Core team + reviewers |
| Meeting Notes | [Link] | TPM | Core team |
| Launch / Release Plan | [Link] | TPM | All stakeholders |

Communicate the repository location at kickoff. Put it in every status report header. People will not go looking for it if they do not know it exists.

---

## Part 6: Communication Principles

A few things that make the difference between a communications plan that works and one that does not.

**Communicate before people ask.** If stakeholders are coming to you for status, you are behind. The goal is that they already have what they need before the question forms.

**Bad news travels early.** A Yellow or Red status flagged early is a problem you can solve together. The same problem flagged late is a crisis. There is no upside to waiting.

**Tailor the message to the audience.** Engineers need technical detail and context. Executives need outcomes, risk, and decisions. The underlying facts are the same - how you present them should not be.

**Close the loop.** When a decision gets made, communicate it. When a risk gets resolved, communicate it. When a milestone lands, communicate it. Stakeholders who feel informed stay engaged. Stakeholders who feel out of the loop start asking questions at the wrong level.

**Keep it skimmable.** Nobody has time to read a novel in their inbox. Bottom line up front, detail below for those who need it.

---

*Version 1.0. Propose changes via pull request.*
