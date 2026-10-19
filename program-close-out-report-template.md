# Program Close-Out Report Template

A close-out report is the last thing a program produces and the first thing the next program team reads. It closes the loop with stakeholders, documents what the program actually achieved, captures what the team learned, and hands off whatever the program built to whoever owns it next.

Start with the objectives and results below: one table, one row per objective from the charter, so anyone can see what was promised and what was delivered. When the report needs the schedule, budget, risks, handoff and lessons written out in full, use the [alternate style](#alternate-style-the-full-report-on-one-page) at the bottom of this page.

---

## Objectives and Results - [Program Name]

| Objective | Definition of Done | Result | Evidence | Notes |
|:---|:---|:---|:---|:---|
| | | | | |
| | | | | |
| | | | | |

For a larger program, add the columns you need: who confirmed each result, and what is carried forward with its owner.

### What goes in each column

- **Objective:** the objective exactly as the original charter stated it. Do not edit it retroactively to match what was delivered.
- **Definition of Done:** the original Definition of Done for that objective.
- **Result:** Achieved, Partial, or Not Achieved.
- **Evidence:** what proves the result, such as a scan, a report, or the requirements traceability matrix if the program kept one.
- **Notes:** anything the next reader needs, including what is left and who owns it.

---

## How to Fill It In

Fill it in honestly. A close-out report that says everything went well when it did not is not useful to anyone.

**Executive summary.** Three to five sentences. What the program set out to do, what it achieved, and the most important thing learned. Written for someone who did not follow the program closely and will not read beyond this section unless something catches their attention.

> Example: "The TLS Modernization Program set out to eliminate TLS 1.0 and 1.1 exposure across all platform services by Q3. The program achieved 100% coverage across 147 services, reducing protocol-level attack surface and meeting the TLS 1.2 minimum in our customer security addendum ahead of the contractual deadline. The primary lesson was that service inventory is always less complete than it appears - the final 20% of services took as long as the first 80% to remediate and required a dedicated tracking workstream to close."

**Objectives and results.** List the objectives from the original charter. Do not edit them retroactively to match what was delivered. If the program kept a requirements traceability matrix, link it. It is the evidence behind the Result column.

**Business metrics.** What moved in the business as a result of this program? Connect delivery to the outcome that justified the investment.

**Out of scope items.** Document anything that was explicitly out of scope and confirm it remained out of scope, or note if it was absorbed into the program through a scope change.

**Schedule and budget.** Compare planned and actual dates for each milestone, and approved budget and actual spend by category. Be specific about what drove schedule changes and whether they were foreseeable. If over budget, explain why. If under budget, explain what did not get spent and whether scope changed.

**Risks and issues: final disposition.** How did the risks and issues tracked in the RAID log resolve? This section closes the loop on the program's risk posture. List any risks or issues that were not fully resolved and are being carried forward. Name the owner and the plan.

**Operational handoff.** Who owns this now? This section confirms the handoff is complete and documents the operational model for whoever is inheriting the work.

**Known technical debt.** Be honest here. If the program delivered the objective but left technical debt behind - edge cases not remediated, legacy services given a temporary exemption, documentation not fully completed - document it. The team inheriting this work needs to know.

**Vendor and contract closure.** Skip this section if the program used no vendors and replaced no contracts. Otherwise list every vendor that delivered work, and every old contract the program replaces. Access revocation is the item most often missed.

An old contract does not have to end when the program does. On a migration it is usually smarter to keep it running past the planned cutover date, with a buffer or through the end of the year, so the old service is still there if the move slips. That overlap is a managed risk with a known cost. Record the planned end date and the person who owns the contract after the program closes.

For a larger vendor engagement, add the columns you need: final deliverables accepted (and by whom), final invoice paid, data returned or deleted, transition support finished. The [Vendor and SOW Management](vendor-and-sow-management.md) guide covers each one.

**Lessons learned.** This is the most valuable section of the close-out report and the most frequently skipped. Run a retrospective with the core team before writing this section - do not write it from memory alone. Cover what worked, what did not work, what surprised you, and what the next team should know: if you were handing this off to a new team starting a similar program tomorrow, what is the most important thing they should know that is not obvious from the charter or the project plan?

**Team recognition.** Programs are hard. People spent real effort on this. Name the team and acknowledge the work before you close the report. Acknowledge anyone who went beyond their defined role, cleared a critical blocker, or made a specific contribution that the program would not have succeeded without. A thank-you to leadership is optional but worth doing: one or two sentences thanking the executive sponsor for their support and investment.

**Recommendations.** Forward-looking recommendations based on what the program learned. What should the organization do next, do differently, or invest in as a result of what this program uncovered? Make each one specific, owned and actionable.

---

## What to Learn From

### Unknown vs Actionable

The same objective row, written two ways, for the TLS Modernization Program:

| | Objective | Definition of Done | Result | Evidence | Notes |
|:---|:---|:---|:---|:---|:---|
| **Unknown** | Improve TLS | TLS updated | Done | | Went well |
| **Actionable** | Eliminate TLS 1.0 and 1.1 exposure across all platform services | Every platform service accepts only TLS 1.2 or higher by end of Q3, the minimum in the customer security addendum | Achieved, [date] | 147 of 147 services, confirmed by the [date] protocol scan; traceability matrix [link] | The final 20% of services took as long as the first 80% and needed a dedicated tracking workstream. Two exempted services moved to [owner name] with a [date] retirement plan |

The actionable row answers what was promised, when it was due and done, where the proof is, who owns what is left, why it mattered and how it was confirmed. The unknown row cannot be checked by anyone, including the team that wrote it.

### Where This Breaks

- **Skipped, or done as a checkbox.** Most programs skip it or treat it as a checkbox. That is a mistake. A well-written close-out report is worth more to the organization than most of the status reports that preceded it - it is the only artifact that converts the program's experience into institutional knowledge.
- **Everything went well.** A close-out report that says everything went well when it did not is not useful to anyone.
- **Objectives edited to match what was delivered.** Use the charter's wording, not a rewrite.
- **Vague lessons.** Vague lessons ("communication could have been better") are not actionable. Specific ones are.
- **Access left open.** Access revocation is the item most often missed.

### The 90 Percent Problem

A remediation program that closes 90% of vulnerabilities still has open vulnerabilities. An encryption program that covers 90% of services still has unencrypted services. The long tail is where the real risk lives, and a close-out report is the last moment anyone is paying attention to it. Name what is left, put an owner on it, and resist the pull to round it up to done. More on this in [TPM craft notes](https://github.com/ChefPlex/learning-notes/blob/main/tpm-craft-notes.md).

---

## Reference

### Who Receives It

The close-out report goes to the program sponsor and key stakeholders when completed. List them in the Distribution field of the report's document control, and get the approvals at the end: the TPM, the executive sponsor, the engineering lead, and the operational owner confirming the handoff.

### Related Templates

- [Program Charter](program-charter-template.md) - where the objectives and Definition of Done come from.
- [Program Phases Playbook](program-phases-playbook.md) - Phase 5, Program Closure, lists everything that closes with the report.
- [RAID Log Guide](raid-log-guide.md) - the risks and issues the final disposition closes out.
- [Vendor and SOW Management](vendor-and-sow-management.md) - vendor and contract closure in detail.

---

## Alternate Style: The Full Report on One Page

Use this when the report needs every section written out. Copy the block into a new file, name it for the program, and send it to the distribution list.

```markdown
# Program Close-Out Report: [Program Name]

## Document Control

| Field | Detail |
|:---|:---|
| Program Name | |
| TPM | |
| Executive Sponsor | |
| Report Version | 1.0 |
| Date Submitted | |
| Distribution | [List stakeholders who receive this] |

## 1. Executive Summary
[Three to five sentences: what the program set out to do, what it achieved, and the most important thing learned.]

## 2. Program Objectives and Results

### Stated Objectives

| Objective | Definition of Done | Result | Notes |
|:---|:---|:---|:---|
| [Objective 1] | [Original DoD] | Achieved / Partial / Not Achieved | |
| [Objective 2] | [Original DoD] | Achieved / Partial / Not Achieved | |
| [Objective 3] | [Original DoD] | Achieved / Partial / Not Achieved | |

[Link to the requirements traceability matrix, if the program kept one.]

### Business Metrics

| Metric | Baseline | Target | Achieved | Notes |
|:---|:---|:---|:---|:---|
| [Metric 1] | | | | |
| [Metric 2] | | | | |

### Out of Scope Items

| Item | Original Status | Final Status | Notes |
|:---|:---|:---|:---|
| [Item 1] | Out of scope | Remained out of scope | |
| [Item 2] | Out of scope | Added via change control on [date] | |

## 3. Schedule and Budget Summary

### Schedule

| Milestone | Planned Date | Actual Date | Variance | Notes |
|:---|:---|:---|:---|:---|
| Program Kickoff | | | | |
| [Key Milestone 1] | | | | |
| [Key Milestone 2] | | | | |
| Go-Live / Launch | | | | |
| Program Close | | | | |

**Overall schedule variance:** [On time / X weeks ahead / X weeks behind]

**Explanation of significant variances:** [What drove schedule changes and whether they were foreseeable.]

### Budget

| Category | Approved Budget | Actual Spend | Variance | Notes |
|:---|:---|:---|:---|:---|
| Engineering headcount | | | | |
| Tooling / licensing | | | | |
| Vendor / contractor | | | | |
| Other | | | | |
| **Total** | | | | |

**Explanation of significant variances:** [If over budget, why. If under budget, what did not get spent and whether scope changed.]

## 4. Risks and Issues: Final Disposition

### Key Risks - Final Status

| Risk | Initial Rating | Final Status | How It Resolved |
|:---|:---|:---|:---|
| [Risk 1] | High / Med / Low | Closed / Accepted / Transferred | |
| [Risk 2] | | | |

### Key Issues - Final Status

| Issue | Priority | Resolution | Date Closed |
|:---|:---|:---|:---|
| [Issue 1] | | | |
| [Issue 2] | | | |

### Unresolved Items

| Item | Type | Owner | Plan | Target Date |
|:---|:---|:---|:---|:---|
| [Item 1] | Risk / Issue | | | |

## 5. Operational Handoff

| Item | Detail |
|:---|:---|
| Operational owner | |
| Support model | |
| Escalation path | |
| Runbook location | |
| Monitoring / alerting | |
| Known technical debt | |
| Handoff date | |
| Handoff confirmed by | |

### Vendor and Contract Closure

| Vendor or contract | Access revoked and verified | Contract end date, and owner after close | Closed by |
|:---|:---|:---|:---|
| [Implementation vendor] | | | |
| [Old license, circuit or support contract this replaces] | | [Cutover date plus buffer; owner] | |

## 6. Lessons Learned

### What Worked

| What Worked | Why It Mattered | Recommendation for Future Programs |
|:---|:---|:---|
| [Item 1] | | |
| [Item 2] | | |
| [Item 3] | | |

### What Did Not Work

| What Did Not Work | Root Cause | What to Do Differently |
|:---|:---|:---|
| [Item 1] | | |
| [Item 2] | | |
| [Item 3] | | |

### What Surprised Us
1. [Surprise 1 and its impact]
2. [Surprise 2 and its impact]

### What the Next Team Should Know
[The most important thing that is not obvious from the charter or the project plan.]

## 7. Team Recognition

**Core team:**

| Name | Role | Contribution |
|:---|:---|:---|
| | | |

**Notable contributions:**
[Anyone who went beyond their defined role, cleared a critical blocker, or made a contribution the program would not have succeeded without.]

**Thank you note to leadership:**
[Optional but worth doing. One or two sentences thanking the executive sponsor.]

## 8. Recommendations
1. [Recommendation 1 - specific, owned, actionable]
2. [Recommendation 2]
3. [Recommendation 3]

## Approvals

| Role | Name | Date Approved |
|:---|:---|:---|
| TPM | | |
| Executive Sponsor | | |
| Engineering Lead | | |
| Operational Owner (handoff confirmed) | | |
```

---

*Template version 1.1. Propose changes via pull request.*
