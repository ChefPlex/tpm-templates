# tpm-templates

Reusable templates and lightweight operating tools for technical program management.

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
- Teach core program management ideas to people who are new to the work

## What Is Here

### Program Lifecycle

| Template | What It Is |
|---|---|
| [Program Phases Playbook](program-phases-playbook.md) | A phase-based view of how programs move from first idea through planning, execution, launch, and close-out. Useful for orienting a team around where the work actually is. |
| [Program Charter Template](program-charter-template.md) | The founding document for a serious initiative. Captures problem, goals, scope, non-goals, stakeholders, risks, decisions, and success criteria. |
| [Program Close-Out Report Template](program-close-out-report-template.md) | A practical close-out format for outcomes, schedule and budget summary, risks, handoff, lessons learned, and recommendations. |

### Operations and Tracking

| Template | What It Is |
|---|---|
| [RAID Log Guide](raid-log-guide.md) | A guide for running a Risks, Assumptions, Issues, and Dependencies log as a living program tool, not a spreadsheet nobody trusts. |
| [Communications Plan Template](communications-plan-template.md) | A stakeholder and communications planning template for status reports, updates, document locations, meeting cadence, and escalation paths. |
| [Stakeholder Engagement Playbook](stakeholder-engagement-playbook.md) | The strategy layer above the comms plan: how to identify the stakeholders who matter, map power and interest, and move skeptics and resource owners you do not command - influence without authority across the program lifecycle. |
| [Program Swim Lanes Template](program-swim-lanes-template.md) | A multi-workstream view for programs with parallel tracks, owners, milestones, risks, and executive summary needs. |
| [RACI Template - Waterfall](raci-template-waterfall.md) | A phase-gated responsibility matrix for settling who's responsible, accountable, consulted, and informed across initiation through closure. |
| [RACI Template - Agile](raci-template-agile.md) | A sprint- and release-cadence responsibility matrix for Scrum, Kanban, or SAFe teams, including the ownership handoff at release. |

### Incident Management

| Template | What It Is |
|---|---|
| [Cyber Incident Management Playbook](incident-management/cyber-incident-playbook.md) | An Incident Commander playbook grounded in the LDR553/CIMTK framework. Covers first-hour actions from detection through the first exec briefing, plus the full six-phase incident lifecycle from detect and classify through sustain and exercise. |

### AI and RAG Programs

| Template | What It Is |
|---|---|
| [Enterprise RAG Program](enterprise-rag-program/) | Running Retrieval-Augmented Generation as a program rather than an AI experiment. Playbook with phases, seven workstreams, governance and risk tiers, plus templates for the charter, use case catalog, data source inventory, evaluation plan, RAID starter, milestone exit criteria, and definition of done. The security workstream lives in [security-program-playbooks](https://github.com/ChefPlex/security-program-playbooks/tree/main/enterprise-rag-security). |

### Program Execution

| Template | What It Is |
|---|---|
| [Program Kickoff Checklist](https://github.com/ChefPlex/tpm-toolbox/blob/main/program-kickoff-checklist.md) | A lightweight checklist for aligning scope, stakeholders, risks, dependencies, decisions, and operating rhythm before a program starts. Lives in `tpm-toolbox`. |
| [Meeting Notes and Action Item Tracker](https://github.com/ChefPlex/tpm-toolbox/blob/main/meeting-notes-action-tracker.md) | A simple structure for capturing decisions, owners, due dates, open questions, and follow-ups. Lives in `tpm-toolbox`. |

### Engineering Collaboration

| Template | What It Is |
|---|---|
| [RFC Template](rfc-template.md) | A Request for Comments template for proposals that need structured review before a decision is made. Covers context, motivation, proposal, risks, alternatives, and decision path. |
| [ADR Template](adr-template.md) | An Architecture Decision Record template for documenting important decisions after they are made. Captures context, decision, alternatives, consequences, and status. |

### Examples

| File | What It Shows |
|---|---|
| [Sample RAID Log Entry](examples/sample-raid-log-entry.md) | A concrete example of a weak risk entry versus a useful one, with field-by-field explanation of why specificity matters. |
| [Sample Program Charter Excerpt](examples/sample-program-charter-excerpt.md) | A worked excerpt of a charter's core (Why / What / Scope) - a weak, directional version vs. one with a baseline, measurable Definition of Done, and an out-of-scope list that defends the scope. |

### Teaching Materials

| File | What It Is |
|---|---|
| [PM: A Thanksgiving Story](PM_Thanksgiving_Story.pptx) | A short presentation that teaches core project management concepts using Thanksgiving dinner as the running example. Built for a non-practitioner audience. Originally developed for Year Up. |

## Maturity

| Area | Status | Notes |
|---|---|---|
| Program charter | Ready | Good starting point for new programs, especially when scope and ownership are still fuzzy. |
| Program phases playbook | Ready | Useful for orienting a team around lifecycle, gates, artifacts, and decision points. |
| RAID log guide | Ready | Strong enough to use directly. Pair it with the sample entry. |
| Communications plan | Ready | Useful for stakeholder mapping, status cadence, and escalation planning. |
| Program swim lanes | Ready | Good for multi-workstream programs that need an executive summary layer. |
| RACI templates (waterfall & agile) | Ready | Two separate matrices, not one template with a toggle - the phase structure and the sprint cadence break down differently and forcing them into one format hides the real handoff points. |
| RFC and ADR templates | Ready | Good base formats for engineering alignment and decision records. |
| Close-out report | Ready | Useful when a program needs a real ending, not just a quiet drift into operations. |
| Cyber incident playbook | Ready | Grounded in LDR553/CIMTK. Use as-is for first-hour response and the six-phase lifecycle; adapt battle rhythm timing to your org. |
| Examples | Working | More examples will make this repo easier to adopt. The next useful additions are a sample charter excerpt and a steering decision example. |

## How to Use This Repo

### Starting a new program

Start with the [Program Charter Template](program-charter-template.md).

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

Use the [RAID Log Guide](raid-log-guide.md), [Communications Plan Template](communications-plan-template.md), and [Program Swim Lanes Template](program-swim-lanes-template.md).

The RAID log is the program memory. The communications plan is how you keep people informed without spending the whole week answering the same status questions. The swim lanes view helps leadership understand how parallel workstreams fit together.

When ownership itself is the thing in question - not status, not risk, but who's actually on the hook for a decision - use the [RACI Template - Waterfall](raci-template-waterfall.md) or [RACI Template - Agile](raci-template-agile.md), depending on how the program runs. Waterfall maps ownership to phases and gates. Agile maps it to the sprint and release cadence, where the handoff usually gets lost between "dev is done" and "it's actually live."

### Responding to a security incident

Use the [Cyber Incident Management Playbook](incident-management/cyber-incident-playbook.md).

Part 1 covers the first hour: triage, command, scope, intent, battle rhythm, and the first exec brief. Part 2 covers the full lifecycle from detection through post-incident review. Use it as the incident commander's field reference, not a document to write from scratch mid-incident.

### Reporting to leadership

Use the [Program Swim Lanes Template](program-swim-lanes-template.md) for cross-workstream visibility and the [Communications Plan Template](communications-plan-template.md) for audience, cadence, and message discipline.

Good reporting doesn't make a program look better than it's. It makes the actual state of the program easier to understand.

### Joining a program already in motion

Start with the [Program Phases Playbook](program-phases-playbook.md).

Figure out where the program actually is, not where people say it's. Then look for the missing artifacts that should exist at that phase.

A program in execution with no clear charter is probably carrying hidden alignment debt. A program near launch with no risk log is probably relying on memory and heroics. A program closing without lessons learned is probably going to repeat the same mistakes. A program where every status update reads "on track" but nobody can say who owns the next decision probably needs a RACI more than it needs another status meeting.

### Building technical consensus

Use the [RFC Template](rfc-template.md) before a decision is made.

Use the [ADR Template](adr-template.md) after a decision is made.

The RFC is for structured debate. The ADR is for memory and accountability. Mixing those up creates confusion. If a team is still debating options, write an RFC. If the decision has been made and people need to understand it later, write an ADR.

### Teaching program management concepts

Use [PM: A Thanksgiving Story](PM_Thanksgiving_Story.pptx) when you need to explain program management to people who don't live in TPM language.

The concepts are not simplified. They are translated. There is a difference.

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

## Recommended Starting Points

| Situation | Start Here |
|---|---|
| New cross-functional program | [Program Charter Template](program-charter-template.md) |
| Program feels vague or stuck | [Program Phases Playbook](program-phases-playbook.md) |
| Risks are scattered across meetings and memory | [RAID Log Guide](raid-log-guide.md) |
| Too many people are asking for status in different ways | [Communications Plan Template](communications-plan-template.md) |
| Stakeholders are misaligned, skeptical, or resisting, and you cannot just order them | [Stakeholder Engagement Playbook](stakeholder-engagement-playbook.md) |
| Multiple workstreams need one leadership view | [Program Swim Lanes Template](program-swim-lanes-template.md) |
| Nobody can say who actually owns a decision - phase-gated program | [RACI Template - Waterfall](raci-template-waterfall.md) |
| Nobody can say who actually owns a decision - sprint-based team | [RACI Template - Agile](raci-template-agile.md) |
| Engineering proposal needs structured review | [RFC Template](rfc-template.md) |
| Decision was made and needs to be remembered | [ADR Template](adr-template.md) |
| Program is ending or moving to operations | [Program Close-Out Report Template](program-close-out-report-template.md) |
| A security incident is unfolding and you need command structure now | [Cyber Incident Management Playbook](incident-management/cyber-incident-playbook.md) |
| Someone handed you "we want AI over our own documents" | [Enterprise RAG Program](enterprise-rag-program/) |
| Someone needs to learn PM basics without jargon | [PM: A Thanksgiving Story](PM_Thanksgiving_Story.pptx) |

## What Is Coming

No giant roadmap - the goal is to add examples and templates useful enough to stand on their own. Nothing queued right now; contributions welcome (see Contributing).

## Related Repos

- [tpm-toolbox](https://github.com/ChefPlex/tpm-toolbox) - The things I kept using after the program ended, including kickoff and meeting templates.
- [program-reporting-frameworks](https://github.com/ChefPlex/program-reporting-frameworks) - How to write a status report an executive can act on, and a steering deck that forces a decision.
- [security-program-playbooks](https://github.com/ChefPlex/security-program-playbooks) - What I'd hand a TPM taking over an encryption or compliance program in their first week.
- [ai-automations](https://github.com/ChefPlex/ai-automations) - Prompts I actually use, and the frameworks for deciding how much AI belongs in a piece of work at all.
- [learning-notes](https://github.com/ChefPlex/learning-notes) - A public notebook on security, systems design and program practice. Some of it will turn out to be wrong.

## Contributing

These templates get better when they are used.

If a section doesn't hold up in real work, change it. If a template creates confusion, simplify it. If an example would make the tool easier to adopt, add it.

The bar is practical usefulness, not completeness.

## Maintainer

Built from experience running platform security, infrastructure, compliance, and enterprise execution programs.

Maintained by [Eric White](https://github.com/ChefPlex).
