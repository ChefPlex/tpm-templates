# Program Close-Out Report Template

A close-out report is the last thing a program produces and the first thing the next program team reads. It closes the loop with stakeholders, documents what the program actually achieved, captures what the team learned, and hands off whatever the program built to whoever owns it next.

Most programs skip it or treat it as a checkbox. That is a mistake. A well-written close-out report is worth more to the organization than most of the status reports that preceded it - it is the only artifact that converts the program's experience into institutional knowledge.

Fill it in honestly. A close-out report that says everything went well when it did not is not useful to anyone.

---

## Document Control

| Field | Detail |
|-------|--------|
| Program Name | |
| TPM | |
| Executive Sponsor | |
| Report Version | 1.0 |
| Date Submitted | |
| Distribution | [List stakeholders who receive this] |

---

## 1. Executive Summary

Three to five sentences. What the program set out to do, what it achieved, and the most important thing learned. Written for someone who did not follow the program closely and will not read beyond this section unless something catches their attention.

> Example: "The TLS Modernization Program set out to eliminate TLS 1.0 and 1.1 exposure across all platform services by Q3. The program achieved 100% coverage across 147 services, reducing protocol-level attack surface and satisfying the DSA compliance requirement ahead of the regulatory deadline. The primary lesson was that service inventory is always less complete than it appears - the final 20% of services took as long as the first 80% to remediate and required a dedicated tracking workstream to close."

---

## 2. Program Objectives and Results

### Stated Objectives

List the objectives from the original charter. Do not edit them retroactively to match what was delivered.

| Objective | Definition of Done | Result | Notes |
|-----------|-------------------|--------|-------|
| [Objective 1] | [Original DoD] | Achieved / Partial / Not Achieved | |
| [Objective 2] | [Original DoD] | Achieved / Partial / Not Achieved | |
| [Objective 3] | [Original DoD] | Achieved / Partial / Not Achieved | |

### Business Metrics

What moved in the business as a result of this program? Connect delivery to the outcome that justified the investment.

| Metric | Baseline | Target | Achieved | Notes |
|--------|---------|--------|---------|-------|
| [Metric 1] | | | | |
| [Metric 2] | | | | |

### Out of Scope Items

Document anything that was explicitly out of scope and confirm it remained out of scope, or note if it was absorbed into the program through a scope change.

| Item | Original Status | Final Status | Notes |
|------|----------------|--------------|-------|
| [Item 1] | Out of scope | Remained out of scope | |
| [Item 2] | Out of scope | Added via change control on [date] | |

---

## 3. Schedule and Budget Summary

### Schedule

| Milestone | Planned Date | Actual Date | Variance | Notes |
|-----------|-------------|------------|---------|-------|
| Program Kickoff | | | | |
| [Key Milestone 1] | | | | |
| [Key Milestone 2] | | | | |
| Go-Live / Launch | | | | |
| Program Close | | | | |

**Overall schedule variance:** [On time / X weeks ahead / X weeks behind]

**Explanation of significant variances:** [Be specific about what drove schedule changes and whether they were foreseeable.]

### Budget

| Category | Approved Budget | Actual Spend | Variance | Notes |
|----------|----------------|-------------|---------|-------|
| Engineering headcount | | | | |
| Tooling / licensing | | | | |
| Vendor / contractor | | | | |
| Other | | | | |
| **Total** | | | | |

**Explanation of significant variances:** [If over budget, explain why. If under budget, explain what did not get spent and whether scope changed.]

---

## 4. Risks and Issues: Final Disposition

How did the risks and issues tracked in the RAID log resolve? This section closes the loop on the program's risk posture.

### Key Risks - Final Status

| Risk | Initial Rating | Final Status | How It Resolved |
|------|---------------|-------------|-----------------|
| [Risk 1] | High / Med / Low | Closed / Accepted / Transferred | |
| [Risk 2] | | | |

### Key Issues - Final Status

| Issue | Priority | Resolution | Date Closed |
|-------|---------|-----------|-------------|
| [Issue 1] | | | |
| [Issue 2] | | | |

### Unresolved Items

List any risks or issues that were not fully resolved and are being carried forward. Name the owner and the plan.

| Item | Type | Owner | Plan | Target Date |
|------|------|-------|------|------------|
| [Item 1] | Risk / Issue | | | |

**The 90 percent problem.** A remediation program that closes 90% of vulnerabilities still has open vulnerabilities. An encryption program that covers 90% of services still has unencrypted services. The long tail is where the real risk lives, and a close-out report is the last moment anyone is paying attention to it. Name what is left, put an owner on it, and resist the pull to round it up to done. More on this in [TPM craft notes](https://github.com/ChefPlex/learning-notes/blob/main/tpm-craft-notes.md).

---

## 5. Operational Handoff

Who owns this now? This section confirms the handoff is complete and documents the operational model for whoever is inheriting the work.

| Item | Detail |
|------|--------|
| Operational owner | |
| Support model | |
| Escalation path | |
| Runbook location | |
| Monitoring / alerting | |
| Known technical debt | |
| Handoff date | |
| Handoff confirmed by | |

**Note on known technical debt:** Be honest here. If the program delivered the objective but left technical debt behind - edge cases not remediated, legacy services given a temporary exemption, documentation not fully completed - document it. The team inheriting this work needs to know.

---

## 6. Lessons Learned

This is the most valuable section of the close-out report and the most frequently skipped. Run a retrospective with the core team before writing this section - do not write it from memory alone.

### What Worked

What practices, decisions, tools, or relationships made this program more successful than it would have been otherwise?

| What Worked | Why It Mattered | Recommendation for Future Programs |
|------------|----------------|-----------------------------------|
| [Item 1] | | |
| [Item 2] | | |
| [Item 3] | | |

### What Did Not Work

Where did the program run into problems that were avoidable in retrospect? Be specific. Vague lessons ("communication could have been better") are not actionable. Specific ones are.

| What Did Not Work | Root Cause | What to Do Differently |
|------------------|-----------|----------------------|
| [Item 1] | | |
| [Item 2] | | |
| [Item 3] | | |

### What Surprised Us

Things nobody anticipated at the start of the program that materially affected how it ran.

1. [Surprise 1 and its impact]
2. [Surprise 2 and its impact]

### What the Next Team Should Know

If you were handing this off to a new team starting a similar program tomorrow, what is the most important thing they should know that is not obvious from the charter or the project plan?

---

## 7. Team Recognition

Programs are hard. People spent real effort on this. Name the team and acknowledge the work before you close the report.

**Core team:**

| Name | Role | Contribution |
|------|------|-------------|
| | | |

**Notable contributions:**

[Acknowledge anyone who went beyond their defined role, cleared a critical blocker, or made a specific contribution that the program would not have succeeded without.]

**Thank you note to leadership:**

[Optional but worth doing. One or two sentences thanking the executive sponsor for their support and investment.]

---

## 8. Recommendations

Forward-looking recommendations based on what the program learned. What should the organization do next, do differently, or invest in as a result of what this program uncovered?

1. [Recommendation 1 - specific, owned, actionable]
2. [Recommendation 2]
3. [Recommendation 3]

---

## Approvals

| Role | Name | Date Approved |
|------|------|--------------|
| TPM | | |
| Executive Sponsor | | |
| Engineering Lead | | |
| Operational Owner (handoff confirmed) | | |

---

*Template version 1.0. Propose changes via pull request.*
