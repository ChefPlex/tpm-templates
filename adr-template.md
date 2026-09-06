# Architecture Decision Record (ADR) Template

An Architecture Decision Record documents a significant architectural decision - what was decided, why, what alternatives were considered, and what the consequences are. It is a short document with a long shelf life.

The value of an ADR is not in the document itself. It is in the future conversation it prevents - the one where someone asks "why did we do it this way?" six months after the person who made the decision has moved on. A well-written ADR means that question has an answer that does not depend on anyone's memory.

Write an ADR whenever a decision meets this test: if a new engineer joined the team tomorrow, would they need to understand this decision to work effectively in this codebase or system? If yes, write the ADR.

---

## How to Use This Template

Copy this template, rename the file with a sequential number and short title (`ADR-001-tls-version-standard.md`), fill in each section, and commit it to the repository where the affected system lives. ADRs are version-controlled documents - update the status as the decision evolves, but do not rewrite history.

---

## ADR-[NUMBER]: [Title]

**Status:** Proposed / Accepted / Deprecated / Superseded by ADR-[NUMBER]

**Date:** [YYYY-MM-DD]

**Deciders:** [Names or roles of people involved in making this decision]

**Technical Story:** [Optional - link to the ticket, RFC, or design doc that prompted this decision]

---

## Context

What is the situation that requires a decision? Describe the problem, the constraints, and the forces at play. Include enough background that someone unfamiliar with the situation can understand why a decision was needed.

Be specific about constraints - technical, organizational, regulatory, timeline. These are the things that made some options unavailable or unattractive.

> Example: "All service-to-service communication in the platform currently uses TLS 1.2. NIST deprecated TLS 1.0 and 1.1 in 2021, and our DSA compliance assessment identified the continued presence of TLS 1.0/1.1 in 12 legacy services as a finding. We need to establish a standard minimum TLS version for all new and existing services, with a remediation timeline for services that do not currently meet it."

---

## Decision

State the decision clearly and specifically. One paragraph, no hedging. Someone should be able to read this section alone and know exactly what was decided.

> Example: "All services must support TLS 1.2 as the minimum version. TLS 1.3 is preferred for new services. TLS 1.0 and 1.1 must be disabled on all existing services by [date]. Services unable to meet this timeline must obtain a formal exemption with a documented remediation plan and interim compensating controls."

---

## Alternatives Considered

List the other options that were seriously considered. For each one, explain why it was not chosen. This section is what prevents the same alternatives from being relitigated in future discussions.

### Alternative 1: [Name]

**Description:** What this option would have involved.

**Why not chosen:** The specific reason this option was rejected. Be honest - if it was rejected because of cost or timeline rather than technical merit, say so.

### Alternative 2: [Name]

**Description:** What this option would have involved.

**Why not chosen:** [Reason]

### Alternative 3: [Name] (if applicable)

**Description:** What this option would have involved.

**Why not chosen:** [Reason]

---

## Consequences

### Positive Consequences

What gets better as a result of this decision?

- [Positive consequence 1]
- [Positive consequence 2]
- [Positive consequence 3]

### Negative Consequences

What gets harder, more expensive, or more constrained as a result of this decision? Be honest - every significant decision has trade-offs. Omitting the negative consequences does not make them go away, it just means future teams discover them without warning.

- [Negative consequence 1]
- [Negative consequence 2]

### Risks

What could go wrong as a result of this decision? What would trigger a need to revisit it?

- [Risk 1 and what would trigger a revisit]
- [Risk 2]

---

## Implementation Notes

Optional section for decisions that have specific implementation requirements worth documenting alongside the decision itself.

- [Implementation note 1]
- [Implementation note 2]

---

## Related Decisions

List any ADRs that this decision depends on, supersedes, or is likely to affect.

- [ADR-XXX: Related decision title]
- [ADR-XXX: Superseded decision title, if applicable]

---

## References

Links to supporting material: RFCs, design docs, compliance requirements, external standards, or relevant context that informed the decision.

- [Reference 1]
- [Reference 2]

---

## ADR Status Lifecycle

| Status | Meaning |
|--------|---------|
| **Proposed** | Under discussion, not yet decided |
| **Accepted** | Decision made and in effect |
| **Deprecated** | Decision was valid but is no longer relevant - context has changed |
| **Superseded** | Replaced by a newer decision - link to the superseding ADR |

When a decision is superseded, update the status of the old ADR to "Superseded by ADR-[NUMBER]" and create a new ADR for the new decision. Do not edit the old ADR to reflect the new decision - the historical record of why the original decision was made is valuable.

---

## A Note on ADR Scope

ADRs are for significant architectural decisions - ones that are hard to change later, that affect multiple teams or systems, or that reflect a meaningful trade-off between alternatives. Not every technical decision needs an ADR.

A good test: would this decision come up in a system design review? Would a new team member need to understand it to make good decisions about the system? If yes, write the ADR. If the decision is easily reversible or only affects one small component, a comment in the code or a note in the ticket is enough.

---

**Worked example:** [the same decision written twice](examples/sample-adr.md), weak against better.

*Template version 1.0. Propose changes via pull request.*
