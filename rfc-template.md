# Request for Comments (RFC) Template

An RFC is a proposal document. Its job is to describe a change you want to make, make the case for it, explain the alternatives, and invite feedback before work begins. It is the right tool when a decision is significant enough to warrant structured discussion but not yet far enough along to be an ADR.

The difference between an RFC and an ADR: an RFC is written before the decision is made, to build alignment. An ADR is written after the decision is made, to document it. An RFC often turns into an ADR once the proposal is accepted.

The discipline of writing an RFC - even when you are fairly sure you know the right answer - is valuable. It forces clear thinking, surfaces objections early, and creates a record of the reasoning that can outlast the people who made the decision.

---

## How to Use This Template

Copy this template, give the file a descriptive name (`rfc-tls-minimum-version-standard.md`), fill in each section, share it with the relevant stakeholders for comment, and update the status as the proposal moves through review. Set a comment deadline and honor it - an RFC that never closes is not useful.

---

# RFC: [Title]

**RFC Number:** [Sequential number if your org tracks these]

**Author(s):** [Name(s)]

**Status:** Draft / In Review / Accepted / Rejected / Withdrawn

**Created:** [YYYY-MM-DD]

**Comment Deadline:** [YYYY-MM-DD]

**Decision Date:** [YYYY-MM-DD - fill in when decision is made]

**Stakeholders:** [Teams and individuals whose input is needed or who will be affected]

---

## Summary

One paragraph. What are you proposing and why? Write this as if it is the only section someone will read - because for many stakeholders, it will be.

> Example: "This RFC proposes establishing TLS 1.2 as the minimum version for all service-to-service communication in the platform, with TLS 1.3 preferred for new services. The proposal includes a 90-day remediation timeline for the 12 legacy services currently running TLS 1.0 or 1.1, and a formal exemption process for services that cannot meet the timeline."

---

## Motivation

Why does this change need to happen? What problem does it solve? What happens if it is not addressed?

Be specific about the driver - regulatory requirement, security risk, technical debt, operational problem, strategic direction. The motivation section is what converts a proposal from a preference into a priority.

Include:
- The current state and why it is insufficient
- The risk or cost of not making this change
- Any external forcing functions (compliance deadline, audit finding, product dependency)

---

## Detailed Proposal

Describe the proposed change in enough detail that an engineer could implement it and a stakeholder could evaluate it. This section should answer:

- What exactly is being changed?
- Who is affected and how?
- What does the implementation sequence look like?
- What are the success criteria - how will we know this worked?

### Proposed Changes

[Describe the specific changes being proposed]

### Implementation Approach

[How will the changes be made? Phased rollout, big bang, migration path, etc.]

### Success Criteria

| Criterion | Measurement | Target |
|-----------|-------------|--------|
| [Criterion 1] | [How measured] | [Target] |
| [Criterion 2] | [How measured] | [Target] |

### Timeline

| Phase | Description | Target Date |
|-------|-------------|-------------|
| Phase 1 | [Description] | |
| Phase 2 | [Description] | |
| Phase 3 | [Description] | |

---

## Alternatives Considered

What other approaches were considered and why were they not chosen? This section prevents the same alternatives from being raised repeatedly in the comment period.

### Alternative 1: [Name]

**Description:** What this would involve.

**Trade-offs:** Why this was not the proposed approach.

### Alternative 2: [Name]

**Description:** What this would involve.

**Trade-offs:** Why this was not the proposed approach.

### Do Nothing

**Description:** Leave the current state unchanged.

**Trade-offs:** [Why this is not acceptable, or under what conditions it might be revisited]

---

## Impact and Dependencies

### Teams Impacted

| Team | Impact | Action Required | Contact |
|------|--------|----------------|---------|
| [Team 1] | [Description] | [What they need to do] | |
| [Team 2] | | | |

### Systems Impacted

| System | Impact | Owner | Notes |
|--------|--------|-------|-------|
| [System 1] | | | |
| [System 2] | | | |

### Dependencies

What does this proposal depend on that is outside the control of this team?

| Dependency | Owner | Status | Risk if Unavailable |
|-----------|-------|--------|---------------------|
| [Dependency 1] | | | |

---

## Risks and Mitigations

| Risk | Probability | Impact | Mitigation |
|------|------------|--------|-----------|
| [Risk 1] | High / Med / Low | High / Med / Low | |
| [Risk 2] | | | |

---

## Open Questions

Questions that need to be resolved before this proposal can be finalized. Assign an owner and a deadline for each.

| Question | Owner | Deadline | Resolution |
|---------|-------|---------|-----------|
| [Question 1] | | | |
| [Question 2] | | | |

---

## Out of Scope

List explicitly what this RFC does not address. This prevents scope creep during the comment period.

- [Out of scope item 1]
- [Out of scope item 2]

---

## Comment Guidelines

This RFC is open for comment until [date]. To provide feedback:

- **Agree with the proposal:** Note your support and any implementation concerns.
- **Disagree with the proposal:** State your objection clearly and propose an alternative.
- **Have a question:** Ask it as a specific question, not a general concern.
- **Identify a risk:** Name the risk, assess the likelihood and impact, and suggest a mitigation.

Comments that propose changes should be specific - "I think X should be Y because Z" is a useful comment. "This seems risky" is not.

---

## Decision

*[Fill in after comment period closes]*

**Decision:** Accepted / Rejected / Withdrawn / Revised and re-submitted

**Decision Rationale:** [Why the decision was made, including how key objections were addressed or overruled]

**Key Changes from Original Proposal:** [If the proposal was modified based on feedback]

**Decision Maker(s):** [Who made the final call]

**Next Steps:** [What happens now - ADR to be written, implementation to begin, etc.]

---

## References

- [Reference 1]
- [Reference 2]

---

*Template version 1.0. Propose changes via pull request.*
