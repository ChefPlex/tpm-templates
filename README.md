# tpm-templates

A collection of templates, frameworks, and reference docs built from real program experience. These are not theoretical - they come from running programs at enterprise scale across security, infrastructure, and compliance domains.

The goal is simple: if you are starting a new program, you should not have to build these from scratch. Take what is useful, adapt it to your context, and make it your own.

---

## What Is Here

### Program Lifecycle

| Template | What It Is |
|----------|-----------|
| [Program Phases Playbook](program-phases-playbook.md) | End-to-end framework covering all five program phases - from first idea through close-out. Artifacts, owners, and key questions at each gate. |
| [Program Charter](program-charter-template.md) | The founding document for any serious initiative. Scope, objectives, Definition of Done, resources, stakeholders, risks, and compliance requirements in one place. |

### Operations and Tracking

| Template | What It Is |
|----------|-----------|
| [RAID Log Guide](raid-log-guide.md) | How to structure and run a Risks, Assumptions, Issues, and Dependencies log. Field definitions, rating guidance, and how to make it a living tool rather than a one-time exercise. See [tpm-toolbox](https://github.com/ChefPlex/tpm-toolbox) for the working spreadsheet. |
| [Communications Plan](communications-plan-template.md) | Stakeholder map, communications matrix, status report structure, and document repository setup. Everything needed to keep the right people informed at the right frequency. |
| [Program Swim Lanes](program-swim-lanes-template.md) | Multi-workstream tracking view for programs running parallel initiatives. Executive-ready summary layer with workstream-level detail underneath. |

### Program Execution

| Template | What It Is |
|----------|-----------|
| [Program Kickoff Checklist](program-kickoff-checklist.md) | Pre-kickoff checklist, recommended agenda with timing, section-by-section facilitation guide, and post-kickoff follow-up checklist. |
| [Meeting Notes and Action Item Tracker](meeting-notes-action-tracker.md) | Template for capturing decisions, actions, open questions, and risks in a meeting. Includes a running tracker for recurring meetings and facilitation tips. |

### Engineering Collaboration

| Template | What It Is |
|----------|-----------|
| [RFC Template](rfc-template.md) | Request for Comments template for significant proposals. Covers summary, motivation, detailed proposal, alternatives considered, impact, dependencies, risks, and decision record. |
| [ADR Template](adr-template.md) | Architecture Decision Record template for documenting significant architectural decisions after they are made. Covers context, decision, alternatives, consequences, and status lifecycle. |

### Program Close

| Template | What It Is |
|----------|-----------|
| [Program Close-Out Report](program-close-out-report-template.md) | Full close-out report covering objectives vs. results, schedule and budget summary, risk disposition, operational handoff, lessons learned, team recognition, and recommendations. |

### Teaching Materials

| File | What It Is |
|------|-----------|
| [PM: A Thanksgiving Story](PM_Thanksgiving_Story.pptx) | A 13-slide presentation that teaches core project management concepts - scope, planning, critical path, risk, stakeholders, dependencies, and retrospectives - using Thanksgiving dinner as the running example. Built for a non-practitioner audience. Includes a class exercise. Originally developed for Year Up. |

---

## How to Use These

**Starting a new program:** Begin with the Charter. It forces the conversations you need to have before work starts - scope, Definition of Done, resources, risks, and who is accountable for what. If you cannot fill it in, you are not ready to start yet.

**Running an active program:** The RAID Log and Communications Plan are your operational tools. The RAID Log is the program's memory. The Communications Plan is how you keep stakeholders informed without spending your whole week answering status questions.

**Reporting to leadership:** The Swim Lanes template gives you an executive-ready view across multiple workstreams. Pair it with the status report structure in the Communications Plan.

**New to a program that is already running:** Start with the Playbook to orient yourself to where things stand in the lifecycle, then look for gaps in the artifacts that should exist at this phase.

**Building technical consensus:** Use the RFC template before a decision is made to drive structured discussion, and the ADR template after to document what was decided and why.

**Teaching PM concepts to a non-practitioner audience:** The Thanksgiving deck is the place to start. The concepts are not simplified - they are translated. There is a difference.

---

## A Few Things Worth Saying Up Front

**These templates are starting points, not prescriptions.** A small three-person project does not need every field in the charter. A massive multi-year program probably needs more than what is here. Use judgment.

**Fill them in or do not use them.** A half-filled charter is worse than no charter - it creates the illusion of alignment without the substance. If a section is not relevant to your program, say so explicitly rather than leaving it blank.

**The artifacts exist to support shared understanding, not to satisfy a process.** The reason to write a charter is so that your team and your stakeholders are aligned on what you are building and why. The reason to maintain a RAID log is so that problems do not become surprises. Keep that in mind when the templates feel like overhead.

---

## What Is Coming

- Stakeholder engagement playbook
- Program retrospective facilitation guide (see learning-notes for a standalone version)

---

## Contributing

These templates improve with use. If you find a gap, an improvement, or a section that does not hold up in practice, open an issue or submit a pull request. Real-world feedback is how these get better.

---

## Related Repos

- [learning-notes](https://github.com/ChefPlex/learning-notes) - Technical concepts, TPM craft notes, and a guide to introducing PM concepts to career changers
- [tpm-toolbox](https://github.com/ChefPlex/tpm-toolbox) - Tools and trackers, including a fully formatted RAID Log spreadsheet
- [security-program-playbooks](https://github.com/ChefPlex/security-program-playbooks) - Frameworks and guides for TPMs running security programs

---

*Built from experience running platform security, infrastructure, and compliance programs at enterprise scale. Maintained by [Eric White](https://www.linkedin.com/in/edwhite) | [ChefPlex](https://github.com/ChefPlex)*
