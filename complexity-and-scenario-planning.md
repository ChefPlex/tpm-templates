# Complexity and Scenario Planning

Most complex programs do not fail on the plan. They fail on something the plan treated as fixed: a dependency, a date, a sponsor's idea of what success meant. This page is the short version of planning for that before it happens: agree what success means with the sponsor, map what the program depends on, and write two or three scenarios with a trigger for each.

**Why bother.** PMI's [Pulse of the Profession 2026](https://www.pmi.org/about/press-media/2026/pulse-why-complex-projects-fail-best-practices-are-not-enough-system-thinking) (Project Management Institute, May 2026) found that "projects that navigate complexity effectively are five times more likely to succeed", 88% against 14%. Its high performers agree success with the sponsor at initiation more often than low performers (39% against 30%), and only one practitioner in five uses scenario planning at all. That last number is the opening: most programs you work alongside have not done this.

---

## 1. Agree what success means, with the sponsor, before kickoff

Write the sponsor's definition of success in their own words, read it back to them, and get a yes before the kickoff meeting. Put it next to the Definition of Done in the [charter](program-charter-template.md).

- **Ask:** "If this program finishes and you are disappointed, what happened?" The answer names the success criterion they did not say out loud.
- **Check it against the Definition of Done.** If the sponsor's words and the Definition of Done disagree, fix it now. After kickoff it becomes a change request.
- **Date it.** "Agreed with the sponsor on `<date>`" is evidence. "We all know what success looks like" is not.

## 2. Map what the program depends on

List what the program needs from outside the team: other teams' deliverables, vendors, approvals, fixed external dates, systems being retired. For each one, name the deliverable, the owner on the other side, and the date you need it. The [RAID log](raid-log-guide.md) dependency fields work as they are.

Then mark the few that, if late, move the end date directly. Those are the ones the scenarios are built on.

## 3. Write two or three scenarios, each with a trigger

A scenario is a specific thing that could knock the program off course, written before it happens, with the sign that it is starting and the response already agreed. Two or three is enough. Ten is a list nobody reads.

| Scenario | Early sign (trigger) | Response, agreed in advance | Owner | Decision maker |
|:---|:---|:---|:---|:---|
| `<what goes wrong>` | `<what you would see first, and when you check>` | `<what you do: swap, defer, add capacity, cut scope>` | `<who watches the trigger>` | `<who approves the response>` |
| | | | | |
| | | | | |

- **The trigger is the useful part.** "Vendor slips" is not a trigger. "The vendor misses the interim test drop on `<date>`" is.
- **Agree the response while nothing is late.** A cut order or a fallback agreed in calm costs a meeting. The same decision made during a slip costs a week.
- **Put each trigger date in the schedule.** Then the review that checks it already exists.

## Worked example (fictional)

A company replaces its ticketing system. Go-live is set before the old system's contract ends.

| Scenario | Early sign (trigger) | Response, agreed in advance | Owner | Decision maker |
|:---|:---|:---|:---|:---|
| Data migration takes longer than planned | The trial migration in week 4 takes more than twice the planned time | Migrate the last two years of tickets at go-live; archive the rest read-only | Data lead | Sponsor |
| Identity team cannot deliver single sign-on in time | Single sign-on not working in test by week 6 | Go live with local accounts for two weeks behind a network allow-list | TPM | Security lead |
| The old system's contract end date does not move | Vendor declines an extension in week 8 | Freeze scope; any change after week 8 goes to the next release | TPM | Sponsor |

## Where this breaks

- **Scenarios nobody owns.** A scenario with no one watching the trigger is a wish. Every row gets a name.
- **Too many scenarios.** If every risk becomes a scenario, the table turns into a second RAID log. Keep the two or three that move the end date.
- **Responses that need a decision nobody can make.** If the response needs sign-off from someone who was not in the room, get that sign-off now or the response is not real.

---

*Related: [Program Charter Template](program-charter-template.md) · [Program Kickoff Checklist](program-kickoff-checklist.md) · [RAID Log Guide](raid-log-guide.md) · [What one more change costs](https://github.com/ChefPlex/tpm-lab/tree/main/change-impact) in tpm-lab.*

*Part of the [ChefPlex TPM portfolio](PORTFOLIO-GUIDE.md). Maintained by [Eric White](https://www.linkedin.com/in/edwhite). Licensed under [CC BY 4.0](LICENSE).*
