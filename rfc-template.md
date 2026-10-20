# Request for Comments (RFC) Template

An RFC is a proposal document. Its job is to describe a change you want to make, make the case for it, explain the alternatives, and invite feedback before work begins. It is the right tool when a decision is significant enough to warrant structured discussion but not yet far enough along to be an ADR.

Start with the RFC log below: one table, one row per proposal, so everyone can see what is open for comment and what has been decided. When a proposal needs its motivation, alternatives and impact written out in full, use the [alternate style](#alternate-style-the-full-proposal-on-one-page) at the bottom of this page and link to it from the log.

---

## The RFC Log

| RFC # | Title | Author | Status | Stakeholders | Comment deadline | Decision | Decided by | Full proposal |
|:---|:---|:---|:---|:---|:---|:---|:---|:---|
| | | | | | | | | |
| | | | | | | | | |
| | | | | | | | | |

### What goes in each column

- **RFC #:** a sequential number, if your organization tracks them.
- **Title:** the change being proposed, in one line, such as "TLS 1.2 minimum for all service-to-service traffic".
- **Author:** who wrote it and will answer the comments.
- **Status:** Draft, In Review, Accepted, Rejected, or Withdrawn.
- **Stakeholders:** the teams and people whose input is needed or who will be affected.
- **Comment deadline:** the date comments close. Set it, and honor it.
- **Decision:** what was decided, in a sentence, once the comment period closes.
- **Decided by:** who made the final call.
- **Full proposal:** a link to the long write-up, if there is one.

---

## How to Fill It In

Give each full proposal a descriptive file name (`rfc-tls-minimum-version-standard.md`), share it with the stakeholders for comment, and update the status in the log as it moves through review.

**Summary.** One paragraph: what you are proposing and why. Write it as if it is the only section someone will read, because for many stakeholders it will be.

> Example: "This RFC proposes establishing TLS 1.2 as the minimum version for all service-to-service communication in the platform, with TLS 1.3 preferred for new services. The proposal includes a 90-day remediation timeline for the 12 legacy services currently running TLS 1.0 or 1.1, and a formal exemption process for services that cannot meet the timeline."

**Motivation.** Be specific about the driver: a regulatory requirement, a security risk, technical debt, an operational problem, a strategic direction. Say what the current state costs and what happens if nothing changes. This is what turns a preference into a priority.

**Detailed proposal.** Enough detail that an engineer could build it and a stakeholder could judge it: what changes, who is affected, the order of the work, and how you will know it worked.

**Alternatives considered.** Include "do nothing". Listing the alternatives up front stops the same ones being raised again during the comment period.

**Out of scope.** Say what the RFC does not cover. It keeps the comment period from growing the proposal.

**Comments.** Ask commenters to be specific. "I think X should be Y because Z" helps. "This seems risky" does not. A question should be a question, and a risk should come with its likelihood, impact and a suggested mitigation.

---

## What to Learn From

### Unknown vs Actionable

The same RFC, logged two ways:

| | Title | Comment deadline | Decision |
|:---|:---|:---|:---|
| **Unknown** | TLS changes | Open | TBD |
| **Actionable** | TLS 1.2 minimum for all service-to-service traffic | Fri, Nov 7 | Accepted Nov 12: TLS 1.2 minimum, 90-day remediation for 12 legacy services; ADR-014 written |

The actionable row says what is proposed, when comments close, and what was decided. Anyone can tell from the log whether they still need to weigh in.

### Where This Breaks

- **The deadline that never closes.** An RFC with no end date stays open for months and decides nothing. Set the date and make the call when it arrives.
- **The loudest commenter wins.** Volume is not agreement. Weigh comments on their substance, and record in the decision how the main objections were handled.
- **Written after the decision.** If the work has already started, the RFC is theater. Write it while the alternatives are still open, or write an ADR instead.

---

## Reference

### RFC or ADR?

An RFC is written before the decision, to build alignment. An ADR is written after the decision, to record it. An accepted RFC often becomes an ADR. Writing an RFC is worth it even when you are fairly sure of the answer: it forces clear thinking, brings objections up early, and leaves a record of the reasoning that outlasts the people who made it.

### RFC Status Lifecycle

| Status | Meaning |
|:---|:---|
| **Draft** | Being written, not yet shared for comment |
| **In Review** | Open for comment until the deadline |
| **Accepted** | Approved, usually followed by an ADR and implementation |
| **Rejected** | Not going ahead, with the reason recorded |
| **Withdrawn** | Pulled by the author |

---

## Alternate Style: The Full Proposal on One Page

Use this when a proposal needs everything written out in one place. Copy the block into a new file and link it from the log. It holds more detail than a log row, and it is harder to search across many proposals, so keep the log as the index.

```markdown
# RFC: [The change being proposed]

**RFC Number:** [Sequential number if your org tracks these]
**Author(s):** [Name(s)]
**Status:** Draft / In Review / Accepted / Rejected / Withdrawn
**Created:** [YYYY-MM-DD]
**Comment Deadline:** [YYYY-MM-DD]
**Decision Date:** [YYYY-MM-DD - fill in when decided]
**Stakeholders:** [Teams and individuals whose input is needed or who will be affected]

## Summary
[One paragraph: what you are proposing and why.]

## Motivation
- Current state, and why it is not enough: [ ]
- Risk or cost of not changing: [ ]
- External forcing functions (compliance deadline, audit finding, product dependency): [ ]

## Detailed Proposal

### Proposed Changes
[The specific changes]

### Implementation Approach
[Phased rollout, big bang, migration path]

### Success Criteria
| Criterion | Measurement | Target |
|:---|:---|:---|
| | | |

### Timeline
| Phase | Description | Target Date |
|:---|:---|:---|
| Phase 1 | | |
| Phase 2 | | |

## Alternatives Considered

### Alternative 1: [Name]
**Description:** [What this would involve]
**Trade-offs:** [Why it is not the proposed approach]

### Do Nothing
**Description:** Leave the current state unchanged.
**Trade-offs:** [Why this is not acceptable, or when it might be revisited]

## Impact and Dependencies

### Teams Impacted
| Team | Impact | Action Required | Contact |
|:---|:---|:---|:---|
| | | | |

### Systems Impacted
| System | Impact | Owner | Notes |
|:---|:---|:---|:---|
| | | | |

### Dependencies
| Dependency | Owner | Status | Risk if Unavailable |
|:---|:---|:---|:---|
| | | | |

## Risks and Mitigations
| Risk | Probability | Impact | Mitigation |
|:---|:---|:---|:---|
| | High / Med / Low | High / Med / Low | |

## Open Questions
| Question | Owner | Deadline | Resolution |
|:---|:---|:---|:---|
| | | | |

## Out of Scope
- [What this RFC does not address]

## Decision
*[Fill in after the comment period closes]*
**Decision:** Accepted / Rejected / Withdrawn / Revised and re-submitted
**Rationale:** [Why, including how key objections were handled]
**Changes from the original proposal:** [If any]
**Decision maker(s):** [Who made the final call]
**Next steps:** [ADR to be written, implementation to begin, etc.]

## References
- [Supporting material]
```

---

*Template version 1.1. Propose changes via pull request.*

*Part of the [ChefPlex TPM portfolio](PORTFOLIO-GUIDE.md). Maintained by [Eric White](https://www.linkedin.com/in/edwhite). Licensed under [CC BY 4.0](LICENSE).*
