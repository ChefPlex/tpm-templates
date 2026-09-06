# Sample RACI Rows

A RACI chart fails in a specific and predictable way. It gets filled in during a workshop, everybody agrees, and then nobody uses it, because it recorded who was in the room rather than who decides.

These rows are from a platform encryption migration, the same program the [RAID log examples](sample-raid-log-entry.md) draw on.

---

## Weak Rows

| Activity | Platform Eng | Security | Service Teams | TPM | Sponsor |
|---|---|---|---|---|---|
| Certificate rotation approach | R, A | R, A | C | C | I |
| Service migration | R | C | R | A | I |
| Go/no-go for production cutover | C | C | C | R | A, R |

### Why This Fails

**Two accountable owners on row one is the same as none.** When the rotation approach turns out to be wrong, Platform Engineering and Security will each reasonably believe the other one owned it. The chart does not resolve that argument, it created it.

**Row two makes the TPM accountable for work the TPM cannot do.** The program manager does not migrate services. Putting an A there means the person who cannot fix the problem is the person who has to answer for it, which is how a status report starts describing effort instead of progress.

**Row three is worse than blank.** The sponsor is marked both accountable and responsible, which reads as "the sponsor will handle it," and the five C's mean everyone has an opinion and nobody has a deadline. A go/no-go decision with five consulted parties and no named decider will be made by whoever is most senior in the room on the day, which is not a process.

Every row here would survive a workshop. People nod at charts like this because nothing in them is wrong, exactly. What they lack is a name attached to a consequence.

---

## Better Rows

| Activity | Platform Eng | Security | Service Teams | TPM | Sponsor |
|---|---|---|---|---|---|
| Define the certificate rotation approach | R | A | C | I | I |
| Migrate an individual service | R | C | A | I | I |
| Confirm a service meets the encryption standard | C | R, A | C | I | I |
| Maintain the integrated migration schedule | C | C | C | R, A | I |
| Go/no-go for production cutover | C | C | C | R | A |

### Why This Works

**One A per row, and the A is the person who carries it if it goes wrong.** Security is accountable for the rotation approach because Security owns the standard. Platform Engineering builds it. That is a real division and it survives contact with a failure.

**The service teams are accountable for their own migrations.** This is the row people resist and it is the one that matters. A central team can build the path, but it cannot adopt it on somebody else's behalf, and a chart that pretends otherwise sets the program up to be blamed for work it never controlled.

**The TPM is responsible and accountable for exactly one thing: the schedule.** That is the honest scope. The program manager owns the integrated view, the dependencies and the escalation path, and owns none of the engineering. Notice the TPM is `I` on almost everything else. A TPM marked `C` on every row is a TPM in every meeting.

**The sponsor is accountable for go/no-go and nothing else.** That is what a sponsor is for. Marking them `I` everywhere else is not a demotion, it is what makes their `A` mean something when it appears.

---

## The Test

Read one row and ask: **if this goes wrong, whose calendar does the meeting land on?**

If the answer is more than one person, the row is not finished. If the answer is nobody, the row is decoration. And if the answer is the TPM for an activity the TPM cannot perform, the chart has recorded a reporting line rather than an accountability.

One more, cheaper still: count the `C`s. Consulted is the field that expands quietly, because adding someone is polite and removing them is a conversation. Every `C` is a person who can slow a decision without being answerable for it.
