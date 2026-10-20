# tpm-templates

Every document a program produces, start to finish, and the guides for running one.

These are not meant to be perfect corporate artifacts. They're working templates for getting alignment, exposing risk, clarifying ownership, and helping teams move.

This repo is the workbench, not the policy binder.

## Who This Is For

This repo is for TPMs, engineering leaders, security program owners, and project leads who need practical structure without turning every program into process theater.

Use it when you need to:

- Start a program with clearer scope and ownership
- Turn ambiguity into an operating plan
- Track risks, assumptions, issues, and dependencies
- Clarify who owns what, who's consulted, and who just needs to know
- Communicate status without hiding the hard parts
- Create enough structure for teams to move with confidence

**This repo is the documents**, including the checklists and trackers. Working tools with code are
in [tpm-toolbox](https://github.com/ChefPlex/tpm-toolbox). Status reports and steering decks are in
[program-reporting-frameworks](https://github.com/ChefPlex/program-reporting-frameworks).

---

## Start Here

### If you're early in the work

Four documents, in this order. They're the spine; everything below is situational.

1. **[Program Charter Template](program-charter-template.md)** - the founding conversation. Do this before anything else, because everything after it is execution.
2. **[Program Kickoff Checklist](program-kickoff-checklist.md)** - turns the charter into a room full of people who agree.
3. **[Meeting Notes + Action Item Tracker](meeting-notes-action-tracker.md)** - the habit that stops things getting dropped.
4. **[RAID Log Guide](raid-log-guide.md)** - how to run a risk register people actually trust, with the [RAID Log Template](raid-log-template.md) to fill in.

Read the [worked examples](examples/) alongside them. Each one shows an unknown version next to a
useful one, which is faster than any amount of instruction. They all draw on the same company, most
of them on one platform encryption migration, so the artifacts connect to each other rather than standing alone.

### If you're running several programs at once

- [Program Phases Playbook](program-phases-playbook.md) - orienting a team on where the work actually is
- [Program Swim Lanes](program-swim-lanes-template.md) - defining the workstreams, their owners and where they touch
- [Communications Plan](communications-plan-template.md) - status that scales past what you can carry in your head
- [RACI - Waterfall](raci-template-waterfall.md) and [RACI - Agile](raci-template-agile.md) - settling who owns what. Two matrices rather than one with a toggle, because phase gates and sprint cadence break down differently. Fillable spreadsheet version: [RACI_Templates.xlsx](RACI_Templates.xlsx)
- [RFC](rfc-template.md) and [ADR](adr-template.md) - proposals before a decision, records after one

### If the hard part is people, or the problem is novel

- [Stakeholder Engagement Playbook](stakeholder-engagement-playbook.md) - influence without authority, which is most of the senior job
- [Close-Out Report](program-close-out-report-template.md) and [Lessons Learned Facilitation Guide](lessons-learned-facilitation-guide.md) - giving a program a real ending instead of a quiet drift into operations

### Or start from the problem in front of you

| Situation | Start Here |
|:---|:---|
| New cross-functional program | [Program Charter Template](program-charter-template.md) |
| Getting ready to kick off | [Program Kickoff Checklist](program-kickoff-checklist.md) |
| Program feels vague or stuck | [Program Phases Playbook](program-phases-playbook.md) |
| You inherited work that is already late and already an argument | [Rescuing Work That Is Off Track](rescuing-work-that-is-off-track.md) |
| Risks are scattered across meetings and memory | [RAID Log Guide](raid-log-guide.md) and [RAID Log Template](raid-log-template.md) |
| Decisions and actions get lost after meetings | [Meeting Notes + Action Item Tracker](meeting-notes-action-tracker.md) |
| Too many people are asking for status in different ways | [Communications Plan Template](communications-plan-template.md) |
| Stakeholders are misaligned, skeptical, or resisting, and you cannot just order them | [Stakeholder Engagement Playbook](stakeholder-engagement-playbook.md) |
| Several workstreams and nobody is sure where one ends and the next begins | [Program Swim Lanes Template](program-swim-lanes-template.md) |
| Nobody can say who actually owns a decision - phase-gated program | [RACI Template - Waterfall](raci-template-waterfall.md) |
| Nobody can say who actually owns a decision - sprint-based team | [RACI Template - Agile](raci-template-agile.md) |
| Engineering proposal needs structured review | [RFC Template](rfc-template.md) |
| Decision was made and needs to be remembered | [ADR Template](adr-template.md) |
| Program is ending or moving to operations | [Program Close-Out Report Template](program-close-out-report-template.md) |
| The program is over and the team needs to learn from it | [Lessons Learned Facilitation Guide](lessons-learned-facilitation-guide.md) |
| Your organization needs its first TPM and you have never hired one | [Building the TPM Function](building-the-tpm-function.md) |
| A vendor is doing the work and the statement of work is vague | [Vendor and SOW Management](vendor-and-sow-management.md) |

Looking for something that used to be here? The cyber incident playbook is in
[security-program-playbooks](https://github.com/ChefPlex/security-program-playbooks/blob/main/cyber-incident-playbook.md),
no manual changes in production is in
[infrastructure-program-playbooks](https://github.com/ChefPlex/infrastructure-program-playbooks/blob/main/no-manual-changes-program.md),
the enterprise RAG and agentic AI programs are in
[ai-automations](https://github.com/ChefPlex/ai-automations/tree/main/ai-programs), and the
Thanksgiving teaching deck is in
[teaching-notes](https://github.com/ChefPlex/teaching-notes/tree/main/project-management).

---

## What Is Here

### Program Lifecycle

| Template | What It Is |
|:---|:---|
| [Program Phases Playbook](program-phases-playbook.md) | Every step from first idea to close-out in one table: what happens, what it needs, what it produces, who owns it, and how much it matters. |
| [Program Charter Template](program-charter-template.md) | The founding document for a serious initiative. Captures problem, goals, scope, non-goals, stakeholders, risks, decisions, and success criteria. |
| [Program Kickoff Checklist](program-kickoff-checklist.md) | What to have ready before the kickoff, what to settle in it, and what to set up in the 48 hours after, each with an owner and a level. |
| [Program Close-Out Report Template](program-close-out-report-template.md) | A practical close-out format for outcomes, schedule and budget summary, risks, handoff, lessons learned, and recommendations. |
| [Lessons Learned Facilitation Guide](lessons-learned-facilitation-guide.md) | How to run a retrospective that produces something the next program can use. |
| [Rescuing Work That Is Off Track](rescuing-work-that-is-off-track.md) | What to do when you are handed something already moving, already late, and already the subject of an argument. Diagnosis, baselining with real throughput data, renegotiating the commitment, and the day 1 / 30 / 90 / 180 shape of the recovery. |

### Operations and Tracking

| Template | What It Is |
|:---|:---|
| [RAID Log Guide](raid-log-guide.md) | A guide for running a Risks, Assumptions, Issues, and Dependencies log as a living program tool, not a spreadsheet nobody trusts. |
| [RAID Log Template](raid-log-template.md) | The log itself, in markdown, with a [spreadsheet version](raid-log-template.xlsx) that sorts, filters and calculates. |
| [Meeting Notes and Action Item Tracker](meeting-notes-action-tracker.md) | Decisions, actions, open questions and risks from a meeting in one table, with a running tracker for recurring meetings. |
| [Communications Plan Template](communications-plan-template.md) | A stakeholder and communications planning template for status reports, updates, document locations, meeting cadence, and escalation paths. |
| [Stakeholder Engagement Playbook](stakeholder-engagement-playbook.md) | The strategy layer above the comms plan: how to identify the stakeholders who matter, map power and interest, and move skeptics and resource owners you do not command - influence without authority across the program lifecycle. |
| [Program Swim Lanes Template](program-swim-lanes-template.md) | Defines the workstreams of a multi-track program: what each lane covers and does not, its owner, its dependencies and its Definition of Done. Status by lane goes in the status report. |
| [RACI Template - Waterfall](raci-template-waterfall.md) | A phase-gated responsibility matrix for settling who's responsible, accountable, consulted, and informed across initiation through closure. |
| [RACI Template - Agile](raci-template-agile.md) | A sprint- and release-cadence responsibility matrix for Scrum, Kanban, or SAFe teams, including the ownership handoff at release. |
| [Vendor and SOW Management](vendor-and-sow-management.md) | Running work a vendor delivers: choosing SOW, PWS or SOO, writing deliverables that can be accepted or rejected, paying on acceptance rather than the calendar, change control, SLOs versus SLAs, third-party risk, key-person and subcontractor risk, and exit. With a SOW review checklist, a vendor scorecard, and a worked example. |

### Building the Function

| Guide | What It Is |
|:---|:---|
| [Building the TPM Function: Hiring Your First TPMs](building-the-tpm-function.md) | For the engineering leader hiring a first technical program manager: the signals you need one, what the role is and is not, a role-definition template, a three-level starter ladder, an interview loop built on a work sample with planted traps, a scorecard, how to calibrate the interviewers, placement, and 30/60/90-day measures. With a worked example. |

### Engineering Collaboration

| Template | What It Is |
|:---|:---|
| [RFC Template](rfc-template.md) | A Request for Comments template for proposals that need structured review before a decision is made. Covers context, motivation, proposal, risks, alternatives, and decision path. |
| [ADR Template](adr-template.md) | An Architecture Decision Record template for documenting important decisions after they are made. Captures context, decision, alternatives, consequences, and status. |

### Examples

| File | What It Shows |
|:---|:---|
| [Sample RAID Log Entry](examples/sample-raid-log-entry.md) | A concrete example of an unknown dependency entry versus an actionable one, with field-by-field explanation of why specificity matters. |
| [Sample Program Charter Excerpt](examples/sample-program-charter-excerpt.md) | A worked excerpt of a charter's core (Why / What / Scope) - a weak, directional version vs. one with a baseline, measurable Definition of Done, and an out-of-scope list that defends the scope. |
| [Sample RACI Rows](examples/sample-raci-rows.md) | Five rows from a real migration, unknown against actionable. Two accountable owners, a TPM held accountable for work it cannot do, and the test that settles a row: if this goes wrong, whose calendar does the meeting land on? |
| [Sample Architecture Decision Record](examples/sample-adr.md) | The same decision written twice. The unknown one records what was chosen; the actionable one records what was rejected, what it cost, and the two conditions that would reopen it. |

## Maturity

This table covers the core templates. The stakeholder playbook, the rescue guide, the vendor and SOW guide, the guide to building the TPM function, and the lessons learned guide are not rated here yet.

| Area | Status | Notes |
|:---|:---|:---|
| Program charter | Ready | Good starting point for new programs, especially when scope and ownership are still fuzzy. |
| Program phases playbook | Ready | Useful for orienting a team around lifecycle, gates, artifacts, and decision points. |
| Kickoff checklist | Ready | One table in work order, with a level on every row. |
| RAID log guide and template | Ready | Strong enough to use directly. Pair it with the sample entry. |
| Meeting notes tracker | Ready | Decisions first, then actions, questions and risks. |
| Communications plan | Ready | Useful for stakeholder mapping, status cadence, and escalation planning. |
| Program swim lanes | Ready | Lane definitions for multi-workstream programs. |
| RACI templates (waterfall & agile) | Ready | Two separate matrices, not one template with a toggle - the phase structure and the sprint cadence break down differently and forcing them into one format hides the real handoff points. |
| RFC and ADR templates | Ready | Good base formats for engineering alignment and decision records. |
| Close-out report | Ready | Useful when a program needs a real ending, not just a quiet drift into operations. |
| Examples | Working | More examples will make this repo easier to adopt. For a steering decision, see the [sample steering committee decision](https://github.com/ChefPlex/program-reporting-frameworks/blob/main/examples/sample-steering-committee-decision.md) in program-reporting-frameworks. |

## How to Use This Repo

### Starting a new program

Start with the [Program Charter Template](program-charter-template.md), then the [Program Kickoff Checklist](program-kickoff-checklist.md).

The charter forces the conversations that need to happen before execution starts:

- What problem are we solving?
- What is in scope?
- What is explicitly out of scope?
- Who owns the work?
- Who makes decisions?
- What does done mean?
- What risks are already visible?
- What constraints are real?

If you cannot fill in the charter, that is the signal. Do not paper over it. Use the blank sections to drive the next conversation.

### Running an active program

Use the [RAID Log Guide](raid-log-guide.md) with the [RAID Log Template](raid-log-template.md), the [Meeting Notes + Action Item Tracker](meeting-notes-action-tracker.md), and the [Communications Plan Template](communications-plan-template.md).

The RAID log is the program memory. The communications plan is how you keep people informed without spending the whole week answering the same status questions. The [swim lanes](program-swim-lanes-template.md) say how the parallel workstreams are cut up and who owns each one.

When ownership itself is the thing in question - not status, not risk, but who's actually on the hook for a decision - use the [RACI Template - Waterfall](raci-template-waterfall.md) or [RACI Template - Agile](raci-template-agile.md), depending on how the program runs. Waterfall maps ownership to phases and gates. Agile maps it to the sprint and release cadence, where the handoff usually gets lost between "dev is done" and "it's actually live."

### Reporting to leadership

Status reports, steering decks and portfolio roll-ups are in [program-reporting-frameworks](https://github.com/ChefPlex/program-reporting-frameworks). The [Communications Plan Template](communications-plan-template.md) here sets the audience, cadence, and message discipline they follow.

Good reporting doesn't make a program look better than it is. It makes the actual state of the program easier to understand.

### Joining a program already in motion

Start with the [Program Phases Playbook](program-phases-playbook.md).

Figure out where the program actually is, not where people say it is. Then look for the missing artifacts that should exist at that phase.

A program in execution with no clear charter is probably carrying hidden alignment debt. A program near launch with no risk log is probably relying on memory and heroics. A program closing without lessons learned is probably going to repeat the same mistakes. A program where every status update reads "on track" but nobody can say who owns the next decision probably needs a RACI more than it needs another status meeting.

### Building technical consensus

Use the [RFC Template](rfc-template.md) before a decision is made.

Use the [ADR Template](adr-template.md) after a decision is made.

The RFC is for structured debate. The ADR is for memory and accountability. Mixing those up creates confusion. If a team is still debating options, write an RFC. If the decision has been made and people need to understand it later, write an ADR.

## Using These Templates With AI

These templates work well with AI as a drafting and critique partner.

Good uses:

- Turn messy notes into a first-pass charter
- Ask for risks, assumptions, issues, and dependencies you may have missed
- Rewrite a status update for a specific audience
- Check whether a decision ask is clear
- Convert meeting notes into owners, actions, due dates, and open questions
- Draft a first-pass RACI from a kickoff conversation, then correct it against what the room actually agreed to
- Pressure-test whether a program is actually ready for kickoff or launch

Bad uses:

- Pasting confidential company data into a public model
- Letting AI invent facts, owners, dates, or commitments
- Publishing AI-generated artifacts without review
- Treating a polished draft as an aligned plan
- Using the template to avoid a hard conversation

AI can help with structure and speed. It doesn't own the facts, the judgment, the tradeoffs, or the final artifact.

## Where This Breaks

This repo is too much process for a small effort that can be solved in two conversations.

It's not enough process for a regulated, multi-year program with legal review, audit evidence, customer commitments, and multiple executive sponsors.

That is fine. Templates are not laws. They are forcing functions.

Use them to expose the conversation you need to have. Do not use them as paperwork for its own sake.

## A Few Things Worth Saying Up Front

These templates are starting points, not prescriptions.

A small three-person project doesn't need every field in the charter. A large security or infrastructure program may need more detail than what is here. Use judgment.

Fill them in or do not use them.

A half-filled charter is worse than no charter if it creates the illusion of alignment. If a section does not apply, say that. If a field is unknown, say who owns finding out. Blank space is not harmless when people mistake it for agreement. The same goes for a RACI matrix with every cell filled in - a grid where every role touches every row isn't more thorough, it's a sign nobody actually worked out who owns what.

The artifact is not the work.

The work is getting the right people aligned on the right problem, with clear ownership, visible risk, and a shared understanding of what happens next.

## Related Repos

- [program-reporting-frameworks](https://github.com/ChefPlex/program-reporting-frameworks) - How to write a status report an executive can act on, and a steering deck that forces a decision.
- [security-program-playbooks](https://github.com/ChefPlex/security-program-playbooks) - Running a security program, incidents included.
- [infrastructure-program-playbooks](https://github.com/ChefPlex/infrastructure-program-playbooks) - Running a data center, migration, directory, network or no-manual-changes program.
- [ai-automations](https://github.com/ChefPlex/ai-automations) - Using AI in program work, and the enterprise RAG and agentic AI program kits.
- [tpm-toolbox](https://github.com/ChefPlex/tpm-toolbox) - Working tools with code, including the Slack status tooling.
- [learning-notes](https://github.com/ChefPlex/learning-notes) - A public notebook on security, systems design and program practice. Some of it will turn out to be wrong.
- [teaching-notes](https://github.com/ChefPlex/teaching-notes) - Teaching material, including the Thanksgiving deck and the career-changer course.

## Contributing

These templates get better when they are used.

If a section doesn't hold up in real work, change it. If a template creates confusion, simplify it. If an example would make the tool easier to adopt, add it.

The bar is practical usefulness, not completeness.

## Maintainer

Built from experience running platform security, infrastructure, compliance, and enterprise execution programs.

Maintained by [Eric White](https://github.com/ChefPlex).

## License

Copyright (c) 2026 Eric White. Licensed under [CC BY 4.0](LICENSE): use it, adapt it, put it to
work in your own program. Credit is the only condition.

---

**Part of the ChefPlex TPM portfolio** | Status: Active | [I need to… find the right document across all the repositories](https://github.com/ChefPlex/tpm-templates/blob/main/PORTFOLIO-GUIDE.md) | [All repositories](https://github.com/ChefPlex)
