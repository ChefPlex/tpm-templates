# Sample RAID Log Entry

The RAID log is only useful if the entries are specific enough for someone to act on. These examples show the difference. They come from the same platform encryption migration as the other examples: each service team integrates a client for the central certificate authority, and each integration is tracked as a dependency.

---

## Weak Entry

**Dependency with payments team may affect cutover.**

### Why This Fails

No owner. No date. No impact statement. No decision needed. No path to resolution. It documents anxiety without creating accountability. Someone will read this entry at the next steering committee and have no idea what to do with it.

---

## Better Entry

| Field | Entry |
|-------|-------|
| Type | Dependency |
| Status | Yellow |
| Owner | Sarah - Payments Engineering |
| Due Date | 2026-06-07 |
| Impact | Payments services cannot cut over to the central certificate authority until Payments commits a date for its rotation-client integration. Current cutover target of 2026-06-15 is at risk if the commitment does not arrive by end of this week. |
| Next Step | TPM to confirm the integration date with Sarah and Dev by Friday. If date is not committed, escalate to sponsor for priority call. |
| Escalation Trigger | No committed integration date by 2026-05-31. |

### Why This Works

The entry gives the team something to do. It names the owner, the date, the impact, the next step, and the escalation trigger. It converts a concern into a dependency with a clear resolution path. Anyone who reads it - including someone joining the program mid-flight - knows exactly where this stands and what happens next.

---

## The Pattern That Works

Every RAID log entry should be able to answer these questions:

- Who owns it?
- What happens if it is not resolved?
- What is the next concrete action?
- When does it escalate, and to whom?

If an entry cannot answer those four questions, it is not ready for the log. Document the gap separately and work to fill it - the log entry comes after you have something real to say.

---

## A Note on the Difference Between Risk and Issue

A **risk** is something that has not happened yet but could. It gets a probability and an impact rating, a mitigation plan, and a trigger that defines when the mitigation needs to execute.

An **issue** is something that has already happened and needs resolution. It gets an owner, a resolution plan, and a target date.

The most common RAID log mistake is logging active issues as risks because it feels less alarming. An issue that is not labeled as an issue does not get the attention it needs. Call it what it is.

---

*Part of the [tpm-templates](https://github.com/ChefPlex/tpm-templates) repo. See the [RAID Log Guide](../raid-log-guide.md) for the full framework.*
