# Sample Architecture Decision Record

An ADR fails when it records what was decided and not what was given up. Six months later the person reading it does not need to know that you chose the thing you chose. They need to know what you rejected, and whether the reason still holds.

This one is from a platform encryption migration, the same program the [RAID log examples](sample-raid-log-entry.md) draw on.

---

## Weak ADR

> **ADR-011: Certificate management**
>
> **Status:** Accepted
>
> **Decision:** We will use a centralized certificate authority with automated rotation.
>
> **Rationale:** This is the industry best practice and gives us better security and easier management at scale.

### Why This Fails

**"Industry best practice" is not a reason, it is a way of not giving one.** It tells the next reader nothing about this program, this estate, or the constraints that were actually in the room.

**Nothing was rejected, so nothing was decided.** If no alternative is recorded, a reader has to assume none was considered, and the first person who prefers a different approach will reopen the question from scratch. An ADR that lists no options is a note, not a record.

**There are no consequences, so the ADR cannot age.** In eighteen months somebody will hit the thing this decision made harder. With no consequences written down they will read this as a mistake rather than as a trade that was made deliberately.

**"Better security and easier management" is unfalsifiable.** Better than what, measured how? A rationale nobody can check is a rationale nobody can revisit.

---

## Better ADR

> **ADR-011: Centralize certificate issuance, accept the concentration risk**
>
> **Status:** Accepted, 2026-04-18. Supersedes nothing. Revisit if service count passes 500 or if the CA vendor changes its rotation API.
>
> ### Context
>
> 300+ services manage their own certificates today. Expiry is the single largest cause of production incidents in this estate: 11 of the last 30 incidents traced to an expired or mismatched certificate, and every one of them was preventable. Service teams have no shared tooling and no shared standard, so each of the 300 has solved the problem badly in its own way.
>
> ### Options considered
>
> **1. Centralized issuance with automated rotation.** One CA, one rotation path, service teams integrate a client.
> **2. Federated issuance, central standard.** Teams keep their own issuance but must meet a published standard and report compliance.
> **3. Do nothing structural, fix expiry monitoring.** Alert earlier and let teams keep their current approach.
>
> ### Decision
>
> Option 1. The deciding factor was not security, it was **adoption cost per team**. Option 2 requires 300 teams to each do work; option 1 requires the platform team to do work once and each service team to integrate a client. Option 3 makes the symptom quieter without reducing the number of things that can expire.
>
> ### Consequences
>
> **We accept a concentration risk we did not have before.** A CA outage now affects every service rather than one. This is a real cost and it is the reason option 2 was genuinely competitive. Mitigation: a documented break-glass path for manual issuance, tested quarterly, owned by Platform Engineering.
>
> **The platform team takes on permanent operational load.** Rotation becomes their pager, not the service teams'. This was agreed with their manager before the decision, not after.
>
> **We become dependent on one vendor's rotation API.** If it changes materially, this ADR is the thing to reopen. That is written into the status line above rather than left to memory.
>
> **Migration is not free for service teams.** Each one integrates a client. That work is tracked as a dependency per service, not assumed.

### Why This Works

**The title says what it costs.** "Centralize certificate issuance, accept the concentration risk" is the whole decision in one line, including the part somebody will object to.

**The context carries a number that can be checked.** 11 of 30 incidents is a fact. It also tells a future reader what would have to change for the decision to change: if certificate expiry stops being the top cause, the argument weakens.

**The rejected options are recorded with what made them competitive**, so reopening the question requires a new argument rather than a fresh opinion. Option 2 is not dismissed. It is beaten, narrowly, on a stated criterion.

**The deciding factor is named and it is not the obvious one.** Adoption cost per team, not security. That is the sentence a reader will remember, and it is the one that teaches how this program thinks.

**The consequences include the bad ones.** The concentration risk, the permanent load on the platform team, the vendor dependency. An ADR that lists only benefits was written to justify a decision rather than to record it, and the next reader can tell.

**The revisit trigger is specific.** Not "review annually," which nobody does. Two named conditions, either of which is observable.

---

## The Test

Hand the ADR to somebody who was not in the room and ask them to argue the other side.

If they can do it from the document alone, it is a record. If they have to go and find the people who were there, it is a note, and by the time somebody needs it those people will have moved on. That is not a hypothetical: the reason you are writing this down is that you will not be the one reading it.
