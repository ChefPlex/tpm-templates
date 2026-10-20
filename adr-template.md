# Architecture Decision Record (ADR) Template

An Architecture Decision Record documents a significant architectural decision - what was decided, why, what alternatives were considered, and what the consequences are. It is a short document with a long shelf life.

Start with the decision log below: one table, one row per decision, short and easy to search. When a decision needs its context, alternatives and consequences written out in full, use the [alternate style](#alternate-style-the-full-record-on-one-page) at the bottom of this page and link to it from the log.

---

## The Decision Log

| ADR # | Title | Status | Date | Deciders | Decision | Revisit when | Watched by | Full record |
|:---|:---|:---|:---|:---|:---|:---|:---|:---|
| | | | | | | | | |
| | | | | | | | | |
| | | | | | | | | |

### What goes in each column

- **ADR #:** a sequential number, such as ADR-001.
- **Title:** what was decided and what it costs, such as "Centralize certificate issuance; accept the concentration risk".
- **Status:** Proposed, Accepted, Deprecated, or Superseded by ADR-[number].
- **Date:** the date the status last changed.
- **Deciders:** the names or roles of the people who made the decision.
- **Decision:** one or two sentences. If it needs more, write a full record.
- **Revisit when:** conditions anyone can see happen, such as "service count passes 500". Not "review annually".
- **Watched by:** the person who will notice when a revisit condition happens.
- **Full record:** a link to the long write-up, if there is one.

---

## How to Fill It In

Keep the log in the repository where the affected systems live, and commit each change. ADRs are version-controlled: update the status as a decision evolves, but do not rewrite history.

**Title.** Say what was decided and what it costs, so the part somebody will object to is on the page from day one.

**Revisit when, and Watched by.** Name conditions that can be observed, and the person who will notice them. A trigger nobody watches is a trigger nobody acts on.

**Context.** Include enough background that someone unfamiliar with the situation can understand why a decision was needed. Be specific about constraints - technical, organizational, regulatory, timeline. These are what made some options unavailable or unattractive.

> Example: "Most service-to-service communication in the platform uses TLS 1.2, but 12 legacy services still accept TLS 1.0/1.1. The IETF formally deprecated TLS 1.0 and 1.1 in RFC 8996 (March 2021), NIST SP 800-52 Rev. 2 (2019) already required TLS 1.2 for government systems, and our annual customer security review identified those 12 services as a finding. We need to establish a standard minimum TLS version for all new and existing services, with a remediation timeline for services that do not currently meet it."

**Decision.** Someone should be able to read it alone and know exactly what was decided.

> Example: "All services must support TLS 1.2 as the minimum version. TLS 1.3 is preferred for new services. TLS 1.0 and 1.1 must be disabled on all existing services by [date]. Services unable to meet this timeline must obtain a formal exemption with a documented remediation plan and interim compensating controls."

**Alternatives considered.** List the options that were seriously considered, and why each was not chosen. This is what stops the same alternatives from being argued again later. Be honest - if an option lost on cost or timeline rather than technical merit, say so.

**Consequences.** Every significant decision has trade-offs. Leaving the negative consequences out does not make them go away; it means future teams discover them without warning.

---

## What to Learn From

### Unknown vs Actionable

The title and the revisit trigger are where most ADRs go vague. The same decision, written two ways:

| | Title | Revisit when |
|:---|:---|:---|
| **Unknown** | Certificate management approach | Review annually |
| **Actionable** | Centralize certificate issuance; accept the concentration risk | Service count passes 500, or the CA vendor changes its rotation API |

The actionable title says what was decided and what it costs. The actionable trigger names conditions anyone can see happen; "review annually" is the review nobody does. The full worked example is in the [sample ADR](examples/sample-adr.md).

### Where This Breaks

- **Written after the build, to justify it.** Write the ADR while the alternatives are still real choices.
- **Alternatives that were never options.** A list of straw men tells the next reader nothing about what was actually weighed.
- **Nobody watches the trigger.** Name who will notice when the revisit condition happens.

### Why It Matters

The value of an ADR is the future conversation it prevents - the one where someone asks "why did we do it this way?" six months after the person who made the decision has moved on. A well-written ADR means that question has an answer that does not depend on anyone's memory.

---

## Reference

### When to Write One

Write an ADR when a decision would come up in a system design review, or when a new engineer joining tomorrow would need to understand it to work effectively in the system. ADRs are for decisions that are hard to change later, that affect multiple teams or systems, or that reflect a meaningful trade-off. If a decision is easily reversible or only affects one small component, a comment in the code or a note in the ticket is enough.

### ADR Status Lifecycle

| Status | Meaning |
|:---|:---|
| **Proposed** | Under discussion, not yet decided |
| **Accepted** | Decision made and in effect |
| **Deprecated** | Decision was valid but is no longer relevant - context has changed |
| **Superseded** | Replaced by a newer decision - link to the superseding ADR |

When a decision is superseded, update the status of the old ADR to "Superseded by ADR-[NUMBER]" and add a new ADR for the new decision. Do not edit the old one to reflect the new decision - the record of why the original decision was made is valuable.

---

## Alternate Style: The Full Record on One Page

Use this when a decision needs everything written out in one place. Copy the block into a new file, name it with its number and a short title (`ADR-001-tls-version-standard.md`), and link it from the log. It holds more detail than a log row, and it is harder to search across many decisions, so keep the log as the index.

```markdown
## ADR-[NUMBER]: [What was decided, and what it costs]

**Status:** Proposed / Accepted / Deprecated / Superseded by ADR-[NUMBER]
**Date:** [YYYY-MM-DD]
**Deciders:** [Names or roles of the people who made the decision]
**Technical Story:** [Optional - link to the ticket, RFC, or design doc that prompted it]
**Revisit when:** [Conditions anyone can see happen - not "review annually"]
**Watched by:** [Who will notice when a revisit condition happens]

### Context
[The situation that needs a decision: the problem, the constraints, and the forces at play.]

### Decision
[One paragraph, no hedging. What was decided.]

### Alternatives Considered

#### Alternative 1: [Name]
**Description:** [What this option would have involved]
**Why not chosen:** [The real reason, including cost or timeline if that was it]

#### Alternative 2: [Name]
**Description:** [What this option would have involved]
**Why not chosen:** [The real reason]

### Consequences

**Positive:**
- [What gets better]

**Negative:**
- [What gets harder, more expensive, or more constrained]

**Risks:**
- [What could go wrong, and what would trigger a revisit]

### Implementation Notes (optional)
- [Anything about how the decision has to be carried out]

### Related Decisions
- [ADR-XXX: title, and whether this depends on, supersedes, or affects it]

### References
- [RFCs, design docs, standards, or compliance requirements that informed it]
```

---

**Worked example:** [the same decision written twice](examples/sample-adr.md).

*Template version 1.1. Propose changes via pull request.*

*Part of the [ChefPlex TPM portfolio](PORTFOLIO-GUIDE.md). Maintained by [Eric White](https://www.linkedin.com/in/edwhite). Licensed under [CC BY 4.0](LICENSE).*
