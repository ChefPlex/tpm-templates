# Building the TPM Function: Hiring Your First TPMs

**Bottom line:** hire your first technical program manager (TPM) when work that crosses teams keeps failing at the seams between them, not when a headcount slot appears. Write the role around a named problem, test candidates with a work sample instead of conversation, place them on a bounded program with one sponsor, and judge them at 90 days on what they surfaced and finished, not on how many updates they sent.

This guide is for the engineering leader who has never had a TPM and is about to hire one or two. It covers the signals that you need the role, what the role is and is not, how to write it, how to level it, how to interview for it, how to place and measure the first hires, and when to add the next one.

One honest caveat before the method. No public survey or study on TPM hiring turned up in research for this guide. Everything here comes from published career ladders (cited below, with dates) plus practitioner judgment: mine comes from leading a practice of 15+ consultant TPMs, and from setting up program management in a group that had none. Where a point is opinion, it is written as opinion.

---

## 1. Do you need a TPM yet?

A TPM coordinates and drives to completion work that spans several teams. If your work does not span teams, you do not need one yet.

### Signals that you do

- **Three or more teams share one deadline**, and nobody owns the combined plan.
- **Engineering managers are doing program work after hours.** They run the cross-team sync, chase other teams for dates, and write the status nobody asked them to own.
- **A launch slipped on a dependency nobody was tracking.** The work was done on time. The thing it waited on was not, and no one knew it was waiting.
- **Decisions get made twice.** The same question comes back every few weeks because nobody wrote down who decided it and why.
- **Status depends on who you ask.** Two managers give two different dates for the same release, and both believe theirs.

### Signals that you do not, yet

- One team owns the work end to end. A good engineering manager (EM) and a tracker are enough.
- The cross-team work is a single short project with a clear owner. Name the owner and move on.
- You want someone to take notes and book meetings. That is a real need, but it is not this role, and a TPM hired for it will either leave or turn into it.

The test: **if you cannot name two cross-team programs the hire would own in their first six months, you are not ready to write the role.**

---

## 2. What the role is, and what it is not

The cleanest one-line split in a published source is in the open Engineering Ladders framework. An EM is the "role also known as dev manager, is responsible for the consistent delivery, career growth and level of happiness of the team." A TPM is "responsible for coordinating and driving to completion initiatives that span multiple teams." ([Engineering Ladders](https://github.com/jorgef/engineeringladders/blob/master/TechnicalProgramManager.md), as of October 2026.)

Put simply: **the EM owns a team. The TPM owns an initiative that crosses teams.**

The table below is opinion, built on that split. No company found in research for this guide publishes a side-by-side definition of all five roles.

| Role | Owns | Does not own | If it goes wrong, whose calendar gets the meeting? |
|:---|:---|:---|:---|
| **TPM** | The cross-team plan, sequencing, dependencies, risk, the decision record, status | Architecture, people management, product scope, the engineering itself | The TPM, for a missed dependency or a surprise |
| **Project manager** | One project's schedule, scope and budget | Usually the technical judgment about feasibility | The project manager, for that project's dates |
| **Product manager** | What to build and why, for the customer | How it is built and sequenced across teams | The product manager, for building the wrong thing |
| **Engineering manager** | A team's people, health and delivery | Work that lives in other teams | The EM, for their team's delivery |
| **Tech lead** | The technical design for a team or system | Cross-team schedule and people | The tech lead, for a design that does not hold |

Two lines in that table cause most of the trouble.

**The TPM does not own the engineering.** A TPM held accountable for work they cannot do is a TPM set up to fail. The [sample RACI rows](examples/sample-raci-rows.md) show exactly how that mistake looks on paper.

**The TPM is not a project manager with a technical title.** The difference is technical depth. A TPM can read a design document and ask what happens when the dependency is late, or when the migration hits the one service nobody has touched in three years. Dropbox's framework says this directly, even at its entry level: "I am expected to create leverage for myself via a technical skillset and not purely from process." ([Dropbox IC1 TPM](https://dropbox.github.io/dbx-career-framework/ic1_technical_program_manager.html), as of October 2026.)

If you need a domain-specific version of this split, the [Security TPM role guide](https://github.com/ChefPlex/security-program-playbooks/blob/main/security-tpm-role-guide.md) does it for security programs, with the same "owns / does not own" structure.

---

## 3. Write the role

Most TPM job descriptions are interchangeable. That is the problem. A description that could fit any company attracts candidates who could work anywhere and screens for nothing.

### Weak versus better

> **Weak:** "Drive cross-functional initiatives and ensure on-time delivery of key projects in a fast-paced environment."

> **Better:** "Own the migration of 40 services to the new auth library by Q3: the plan, the dependency map, the weekly risk review, and the call to stop at 90% if the last services have no path."

The better version names the program, the finish line, the artifacts, and a decision the TPM is expected to make. A candidate can read it and know whether they have done that before. So can your interviewers.

### Template: role definition

Fill this in before you write the public posting. The posting is a shorter version of this, not the other way around.

```
ROLE DEFINITION

Title and level:
Reports to:
Sponsor (the leader whose outcome this role serves):
Why this role exists (one sentence, tied to a named cross-team problem):

Programs in the first 6 months (2 to 3; for each: teams involved, finish line):
  1.
  2.
  3.

Owns:          plan, dependency map, RAID log, decision log, status,
               Definition of Done for each program
Does not own:  architecture, people management, product scope,
               engineering delivery

Decisions this role can make alone:
Decisions this role must escalate, and to whom:

Works most with (teams and roles):
Technical depth required (be specific, e.g. "can read a design doc and
  ask what happens when the dependency is late"):

Signals of success at 90 days:
Signals of success at 6 months:

What this role is not (one line, to stop scope creep):
```

RAID stands for Risks, Assumptions, Issues and Dependencies. The [RAID log guide](raid-log-guide.md) explains the log the first TPM will keep.

The "What this role is not" line matters more than it looks. Without it, the first TPM becomes the default owner of every orphaned task in the organization within a quarter.

---

## 4. Levels: start with three, not nine

Published ladders are long. GitLab's TPM individual contributor (IC) track runs from TPM Intern to Distinguished TPM, nine levels, with a separate management track from Manager to Vice President (VP) of TPM. Dropbox's TPM track runs IC1 to IC6. ([GitLab TPM job description library](https://handbook.gitlab.com/job-description-library/engineering/technical-program-management/) and [Dropbox Engineering Career Framework](https://dropbox.github.io/dbx-career-framework/ic1_technical_program_manager.html), both as of October 2026.)

You do not need nine levels for two people. You need enough levels to write an honest offer and a promotion path. Three is enough.

The usable idea in every ladder is the **scope ladder**: one team's project, then several teams, then a department, then the company. GitLab's matrix states it plainly:

- Associate TPM: "Owns a defined project within a single team. Bounded scope."
- TPM: "Programs spanning 1-2 teams at medium complexity."
- Senior TPM: "Multiple teams spanning departments. Influences senior leaders."

GitLab also ties level to ambiguity: "Junior TPMs typically work on well-defined tasks, while Senior and Principal TPMs are expected to 'bring order to chaos,' operating independently in environments where goals or technical paths are highly uncertain."

### A three-level starter ladder

| Your level | Scope | Ambiguity | Technical expectation | Nearest published anchor |
|:---|:---|:---|:---|:---|
| **TPM** | A program across 1 to 2 teams | Some ambiguity; works independently once the goal is clear | Evaluates feasibility; reads a design and finds the risk | GitLab "TPM"; Dropbox IC3 |
| **Senior TPM** | Several teams, often across departments | Sets the plan where the goal is clear but the path is not | Identifies technical risks and guides engineering decisions | GitLab "Senior TPM"; Dropbox IC4 |
| **Staff TPM** | A program tied to a company-level objective | Defines the program where the goal itself is still forming | Weighs trade-offs for the wider organization, not one program | GitLab "Staff TPM"; Dropbox IC5 |

Dropbox's Staff (IC5) language is a good test for that top row: "I have a holistic view of the engineering org and Dropbox's goals and use my experience and judgment to make decisions optimized for the wider org, rather than my local project alone."

### Which level to hire first

**Hire your first TPM at Senior.** The first one has no peers, no templates in use, and no one to ask. They will define what the role means in your organization whether you intend that or not. A junior hire in that seat gets well-defined tasks, which is exactly what you will not have.

Entry-level and career-changer candidates are a good second or third hire, once there is a senior TPM to learn from. The [career changers note](https://github.com/ChefPlex/teaching-notes/blob/main/project-management/pm-for-career-changers.md) is a useful read for that conversation.

**What to borrow and what to leave.** Borrow the scope and ambiguity rows. They are the part that transfers. Leave the org structure behind: GitLab's ladder was written for how GitLab is organized, and the reporting lines in it may not fit yours.

---

## 5. Interview for it

Conversational interviews reward the candidate who tells the best story about a program. The job is running the program. Test that.

### The loop

About four to five hours across five stages. Every interviewer scores independently, in writing, before the debrief.

| Stage | Format | What it tests | Pass signal |
|:---|:---|:---|:---|
| **1. Hiring manager screen** (30 min) | Conversation about one past program | Scope fit; honesty about their part in it | Can say what they owned versus what the EMs owned |
| **2. Work sample A: written plan** (90 min take-home, or 60 on site) | The brief below | Structure, risk sense, written clarity | Names owners, a Definition of Done, three real risks, one decision that needs escalation |
| **3. Work sample B: live review** (45 min) | Candidate walks through the plan; interviewers push back as skeptical EMs | Influence without authority; handling pushback | Concedes valid points, holds the line on the right ones, asks questions |
| **4. Technical depth** (45 min) | An engineer asks: "Walk me through a system you drove a program on." | Technical fluency | Asks what breaks, not only when it ships |
| **5. Stakeholder simulation** (30 min) | Role-play: a lead says their team cannot take the work this quarter | Negotiation; escalation judgment | Finds the real constraint, proposes an option, knows when to escalate |

Stage 3 is the one most loops skip, and it is the most predictive part of the job. A plan is only as good as the TPM's ability to defend it to the people who have to do the work. The [Stakeholder Engagement Playbook](stakeholder-engagement-playbook.md) describes what good looks like there.

### Template: work-sample brief

Give every candidate the same brief and the same fact sheet. Change the details for your domain; keep the structure.

```
WORK-SAMPLE BRIEF (fictional)

A mid-size software company must move 30 services off an old internal
authentication library before the library is retired in two quarters.
Seven teams own the services. Two of those teams say they have no
capacity this quarter. Security wants a firm date.

You have the attached one-page fact sheet: services, owning teams,
and known dependencies.

Produce:
  1. A one-page plan: scope, out of scope, owners, milestones,
     Definition of Done.
  2. A RAID starter with the three risks you would worry about most.
  3. The first message you would send to the two teams with no capacity.

Time: 90 minutes. Bullets are fine. We care about judgment, not polish.
```

**Plant two traps in the fact sheet.** For example: one service is owned by a team that was reorganized last month, so the listed owner is wrong. One "dependency" is actually an outside vendor, with its own timeline you do not control. Strong candidates notice at least one and ask about it. Weak candidates build a clean plan on top of both.

### Weak versus better questions

> **Weak:** "Tell me about a time you managed a difficult stakeholder."

> **Better:** "A team lead says your dates are fiction. The dates came from their own estimate. What do you do in the next 24 hours?"

The weak question invites a rehearsed story. The better one has no rehearsed answer, and it tests the thing you need: whether the candidate goes looking for what changed, or argues about whose number it was.

### Template: scorecard

Score each area 1 to 4 against the level you are hiring for. Write the evidence next to the score. "Seemed sharp" is not evidence.

```
CANDIDATE SCORECARD                    Level hired for: ________
Interviewer: ________   Stage: ________   Date: ________

                         Score   Evidence (what they said or wrote)
Structure                 [ ]
Risk judgment             [ ]
Technical fluency         [ ]
Influence                 [ ]
Written communication     [ ]
Ownership honesty         [ ]

Anchors (apply to every area):
  1  Missing. Did not show it, or showed the opposite.
  2  Partial. Showed it when prompted, not on their own.
  3  Solid for the level. Showed it unprompted, with specifics.
  4  Above the level. Would raise the bar for the team.

Hire / no hire, and the one piece of evidence that decided it:
```

**Ownership honesty** is the area most loops leave out. A strong TPM says "the EM made that call, I made sure it got made." A weak one claims the whole program. You want the first.

**Debrief rule:** each interviewer states evidence first, then the score. No one says "I liked them" before the evidence is on the table, because the first opinion in the room sets the anchor for everyone after it.

### Interview the interviewers

This comes from a consulting firm that ran its own technical interview for about fifteen years. When its recruiters and sales team were finally asked, they said the questions were out of date, which was expected. They also said a rating depended on who gave it, and they had quietly learned which interviewers to trust.

- **Calibrate before an interviewer scores alone.** A new interviewer shadows two loops, then runs two with an experienced interviewer scoring alongside. Compare the scores and talk about every gap of more than one point.
- **Send the role definition from section 3 with every loop.** Interviewers who know what the team needs ask better follow-up questions.
- **Ask about scale and production.** A candidate who has read about a large migration and one who has run one can give the same answer to "how would you approach it?" Ask how big it was, what broke in production, and what they would not do again.
- **Tell each interviewer how their hires are doing at 90 days.** An interviewer whose high scores keep washing out needs to know.
- **Change the work sample and the technical questions for each role.** Keep the stages. One fixed interview for every role drifts out of date as the work changes.

---

## 6. Place the first hires

Where you put the first TPM decides whether the role survives its first year.

- **Attach them to a program, not a team.** A TPM attached to one team becomes that team's project manager. A TPM attached to a program owns the seams between teams, which is the job.
- **Give them one sponsor.** The sponsor is the leader whose outcome the program serves and who will make the call when two teams disagree. Two sponsors is the same as none.
- **Make the first assignment bounded, with a visible finish.** A migration with a fixed end date and a countable number of services is ideal. Everyone can see whether it finished.
- **Do not hand a new TPM a rescue as their first job,** unless that is what you hired for and said so in the interview. A rescue tests a different skill and buries the new hire in someone else's history. If you do need one, [Rescuing Work That Is Off Track](rescuing-work-that-is-off-track.md) is the method.

### Who should they report to?

There are two common answers. Both work. Neither is free. This is opinion, not a published finding.

| Reporting line | Gains | Costs |
|:---|:---|:---|
| **A platform or infrastructure engineering leader** | Close to the technical work; credibility with engineers from day one | The TPM can drift into serving one org's priorities over the program's |
| **A central engineering leader (e.g. VP Engineering)** | Neutral across teams; easier to escalate | Further from the code; has to earn technical credibility the slow way |

For the first one or two hires, report to whoever sponsors the first program, as long as that person sits above every team the program touches. Revisit it when there are three.

### What to hand them on day one

The first TPM should not be inventing templates in week one. Give them the basics: a [program charter template](program-charter-template.md), a [RAID log](raid-log-guide.md), a [RACI template](raci-template-agile.md) and the [program phases playbook](program-phases-playbook.md). They will adapt them. That is fine.

---

## 7. Measure the first 90 days

Pick few measures, and tie each one to a program outcome. What you count is what you will get.

### Weak versus better measures

| Weak measure | Why it misleads | Better measure |
|:---|:---|:---|
| Status reports sent | Rewards writing, not progress | Programs finished against a written Definition of Done |
| Meetings run | Rewards calendar volume | Dependencies surfaced before they caused a slip |
| Risks logged | Rewards a long list | Risks with a named owner and an action that moved |
| "Stakeholders seem happy" | Nobody asked | EMs, asked directly: "Is this person making your team's job easier?" |
| Decisions discussed | Rewards talk | Decisions recorded with a named owner and a date |

The last row in the better column is the cheapest measure there is. Ask the engineering managers. They know within six weeks whether the TPM is removing work or adding it.

### Template: 30/60/90 check-in

```
30/60/90 CHECK-IN                      TPM: ________   Sponsor: ________

DAY 30
  [ ] Has met every team on the first program and its EM
  [ ] Written plan exists, with owners and a Definition of Done
  [ ] RAID log started and reviewed at least twice
  Sponsor's one-line read:

DAY 60
  [ ] At least one dependency surfaced before it slipped (name it)
  [ ] At least one decision recorded with owner and date (name it)
  [ ] Status matches what the EMs say, without the TPM in the room
  EMs asked "easier or harder?" Answers:

DAY 90
  [ ] First program at or near its finish, or re-planned on the record
  [ ] One thing the TPM stopped doing because it added overhead
  [ ] Sponsor would hire this person again: yes / no / why
  Next program (named, with a finish line):
```

The line "status matches what the EMs say, without the TPM in the room" is the real test. A TPM whose status only holds up when they present it has built a reporting habit, not a program.

---

## 8. How the function grows

### When to hire the second TPM

**Hire the second one when the first has a waiting list, not when headcount appears.** A waiting list means teams are asking for the TPM by name, and the TPM is turning work away. That is demand you can point to. Headcount without demand produces a TPM looking for something to coordinate.

### What to add as you grow

- **Shared artifacts.** Two TPMs using two different status formats is how leadership stops trusting either. Agree one charter, one RAID log format, one status format. The existing [tpm-templates](https://github.com/ChefPlex/tpm-templates) are a starting point.
- **A weekly TPM sync.** Thirty minutes. Cross-program dependencies, shared risks, and who is overloaded. Not a status meeting.
- **Interviewing as part of the job.** Dropbox puts hiring in every level's expectations, including IC1: "I am learning to interview and assess candidates..." Put your first TPM in the loop for the second hire, first as a shadow and then as the stage 3 interviewer.
- **A lead, when there are four or five.** Someone has to own the ladder, the loop and the shared artifacts. Before that, the hiring manager owns them.
- **Splitting by domain, later.** When programs cluster (platform, security, data), TPMs specialize. Do this when the clusters are real, not on an org chart in advance.

The [TPM craft notes](https://github.com/ChefPlex/learning-notes/blob/main/tpm-craft-notes.md) cover how TPMs earn credibility with engineering teams, which is what every new hire in a growing function has to do again from zero.

---

## Worked example: Tallowmere Systems

*Tallowmere Systems is fictional. Every person, number and date below is invented for illustration.*

Tallowmere has about 400 engineers and nine teams building on one shared platform.

### The trigger

Three launches in two quarters slipped on the same dependency: a shared identity service that each launch assumed someone else had scheduled. Nobody owned it. Two engineering managers spent most of a quarter running cross-team syncs on top of their own teams. The VP of Engineering decided to hire a TPM.

### The role definition

The first draft was copied from a job board: "fast-paced," "cross-functional," "drive alignment." The recruiter got 200 applicants and could not screen any of them out.

The rewrite used the template in section 3. The key lines:

- **Why this role exists:** "Three launches slipped on the identity service because no one owned the cross-team plan."
- **First program:** "Move 30 services to the new identity service before the old one is retired at the end of Q2. Seven teams. Finish line: zero calls to the old service."
- **Does not own:** "The identity service design (Platform team), or any team's migration work (each owning team)."
- **What this role is not:** "Not the release manager for every launch."

### The loop

The first loop was three conversational interviews. The panel liked one candidate a lot. He had a strong story about a large program. In the debrief, nobody could say what he personally owned in it.

The VP paused the search and rebuilt the loop from section 5. Two finalists did the work sample. Their scorecards, combined across interviewers:

| Area | Candidate A | Candidate B |
|:---|:---|:---|
| Structure | 4 | 3 |
| Risk judgment | 2: missed both traps | 4: caught the reorganized team; asked whether the "dependency" was internal |
| Technical fluency | 3 | 3 |
| Influence | 2: argued with every pushback in stage 3 | 3: conceded the timeline, held the Definition of Done |
| Written communication | 4 | 3 |
| Ownership honesty | 2 | 4 |

Candidate A wrote the cleaner plan. Candidate B found the problems in the fact sheet and was honest about her past role. Tallowmere hired B as a Senior TPM.

### Placement

B reported to the VP of Engineering, who also sponsored the migration. A second TPM requisition was approved but held until B's 60-day check-in.

### The 90 days

The sponsor first proposed tracking "weekly status sent on time" and "meetings run." B pushed back and suggested the better column from section 7 instead.

| Day | Weak measure (dropped) | Better measure (used) |
|:---|:---|:---|
| 30 | 4 status reports sent | Plan with owners and Definition of Done; 7 of 7 EMs met |
| 60 | 11 meetings run | 2 dependencies surfaced early, including a vendor certificate renewal due mid-migration; 5 decisions logged with owners |
| 90 | 12 status reports sent | 26 of 30 services migrated; the last 4 re-planned on the record with the sponsor's sign-off |

At day 60, the EMs were asked "easier or harder?" Six said easier. One said harder, because B's weekly review added a meeting. B cut the review to fifteen minutes and moved half of it to the written update.

### Month 9

Two other directors asked for B by name for their programs. That was the waiting list. Tallowmere opened the second requisition. B ran stage 3 of the loop. After two rounds, the panel made one change: they shortened the take-home to 60 minutes, because the 90-minute version was screening out strong candidates who had full-time jobs.

---

## Where this breaks

**When the real problem is not coordination.** If teams are late because they are understaffed, or because the architecture is wrong, a TPM will make the problem visible. That is useful, but it will not fix it. Be ready for the first TPM's first finding to be about something only you can change.

**When there is no sponsor with authority.** A TPM can drive a program across teams only if someone above those teams will make the call when they disagree. Without that, the TPM becomes a messenger between managers who outrank them.

**When the work sample becomes a ritual.** A brief reused for two years leaks. Candidates see it in advance, and the traps stop catching anyone. Rotate the scenario every few hiring rounds.

**When nobody checks the interviewers.** Two interviewers can apply the same anchors and land a full point apart, every time. Without calibration, the hire depends on who happened to be free that day.

**When the scorecard is filled in after the debrief.** Then it records the group's opinion, not each interviewer's evidence, and it gives you false confidence in a decision that was made by whoever spoke first.

**When the ladder is copied whole.** A nine-level ladder for a two-person function invents distinctions nobody can observe. Expand the ladder when you have people at the levels, not before.

**When the measures are gamed.** "Dependencies surfaced early" can be inflated by logging things that were never at risk. The EM question is the check on this: managers notice when the risk log is theater.

**When large-employer job postings are your template.** A posting written for a company with hundreds of TPMs reflects that company's scale, its ladder and its hiring volume. Its year counts and credential lists screen for its pipeline, not yours. Copy the shape of a requirement (works directly with engineering teams, reads technical designs), never the numbers.

---

## Common mistakes

- **Hiring a project manager and calling them a TPM.** The tell is in the loop: nobody tested technical fluency.
- **No sponsor.** The TPM spends the first quarter asking who decides.
- **TPM as note-taker.** If the TPM is in every meeting and owns no decision, you hired an expensive scribe.
- **Hiring the strongest engineer who hates coordination.** Technical depth is necessary. It is not the job.
- **First TPM inherits a fire.** They spend their first six months on someone else's history, and the organization learns that "TPM" means "late project."

---

## Sources

All accessed 2026-10-18. Facts are as of October 2026.

- GitLab, [Technical Program Management job description library](https://handbook.gitlab.com/job-description-library/engineering/technical-program-management/). Defines TPM competencies and levels "under the new structure rolled out during the job re-architecture in early 2026." Source of the scope, ambiguity and level quotes above.
- Dropbox, [Engineering Career Framework, TPM track](https://dropbox.github.io/dbx-career-framework/ic1_technical_program_manager.html) (IC1, [IC4](https://dropbox.github.io/dbx-career-framework/ic4_technical_program_manager.html), [IC5](https://dropbox.github.io/dbx-career-framework/ic5_staff_technical_program_manager.html), [IC6](https://dropbox.github.io/dbx-career-framework/ic6_principal_technical_program_manager.html)). Publication date not confirmed.
- Engineering Ladders, [Technical Program Manager](https://github.com/jorgef/engineeringladders/blob/master/TechnicalProgramManager.md). An individual's open framework, not a company ladder. Used here only for the one-line role definitions. In its [README](https://github.com/jorgef/engineeringladders/blob/master/README.md)'s own words: "every company is different. Please use the information provided as a baseline and feel free adjust it to your needs."
- No public survey or study specific to TPM hiring was found. The interview loop, placement advice and measures are practitioner judgment. The interviewer guidance in section 5 comes from a 2017 review of a consulting firm's long-running technical interview, in which recruiters, sales and practice leads gave their feedback on it.

---

## Related

- [Security TPM Role Guide](https://github.com/ChefPlex/security-program-playbooks/blob/main/security-tpm-role-guide.md): the domain-specific job description
- [Stakeholder Engagement Playbook](stakeholder-engagement-playbook.md): influence without authority, the signal stage 3 tests for
- [Sample RACI Rows](examples/sample-raci-rows.md): what it looks like when a TPM is held accountable for work they cannot do
- [Program Charter Template](program-charter-template.md) and [Program Phases Playbook](program-phases-playbook.md): what the first TPM uses on day one
- [The RAID Log guide](raid-log-guide.md)
- [Rescuing Work That Is Off Track](rescuing-work-that-is-off-track.md): for when the first assignment is a rescue after all
- [TPM Craft: Notes on Running Programs at Scale](https://github.com/ChefPlex/learning-notes/blob/main/tpm-craft-notes.md)
- [Introducing PM Concepts to Career Changers](https://github.com/ChefPlex/teaching-notes/blob/main/project-management/pm-for-career-changers.md)

---

*Part of the [ChefPlex TPM portfolio](PORTFOLIO-GUIDE.md). Maintained by [Eric White](https://www.linkedin.com/in/edwhite). Licensed under [CC BY 4.0](LICENSE).*
