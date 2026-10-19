# Vendor and SOW Management

When a vendor does the work, you still own the outcome. You do not own the people. You cannot reassign them, you cannot change their priorities, and you cannot add scope by asking nicely in a meeting. The only tools you have are the ones written into the contract, plus the relationship you build around it.

That changes the job. On an internal program, a vague plan can be fixed later by talking to people. On a vendor program, a vague statement of work (SOW) is fixed later by paying for it, arguing about it, or both. **The SOW is the program plan the vendor is actually bound by.** Everything in this guide is a way of making that document carry enough weight to run the work, accept it, pay for it, change it, and leave.

This guide covers, in order: choosing the right kind of work statement, writing a SOW that can be accepted or rejected, acceptance and payment, change control, running the vendor after signature, third-party risk, key-person and subcontractor risk, and exit. Two fill-in templates are at the end: a SOW review checklist and a vendor scorecard.

**A note on sources.** The clearest public rules on how to describe and inspect contracted work are in the US Federal Acquisition Regulation (FAR), the rulebook for federal agency purchasing. Those rules bind federal agencies, not private buyers. They are used here because they are a tested, written-down model of what a work statement should contain, not because a private contract must follow them. **This is a program manager's guide, not legal advice.** Your legal and procurement teams own the paper.

---

## 1. Before the SOW: who owns what

A vendor engagement has three owners, and programs get into trouble when one of them assumes another is covering a gap.

| Owner | Owns | Does not own |
|:---|:---|:---|
| **Program** (you, the technical program manager, TPM) | What the work is, what done looks like, who accepts it, the schedule, day-to-day performance | Contract terms, pricing, liability, signature authority |
| **Procurement** | Vendor selection process, commercial terms, the master services agreement (MSA), purchase orders | Whether a deliverable works |
| **Legal** | Liability, indemnity, data terms, termination rights, the final wording | Whether the scope is complete |

The MSA is the umbrella contract with the vendor: legal and commercial terms that apply to every piece of work. The SOW sits under it and describes one specific piece of work. You will rarely write the MSA. You will often write most of the SOW, and you are usually the only person in the room who can tell whether its scope is complete.

Two gates come before any of this. The [Buy vs. Build Decision Record](https://github.com/ChefPlex/tpm-templates/blob/main/program-phases-playbook.md) records why you are buying at all, and the [Vendor / Third-Party Review](https://github.com/ChefPlex/security-program-playbooks/blob/main/security-program-intake-kickoff.md) gets security and procurement eyes on the vendor before work starts. The phases playbook says it plainly for the SOW itself: "Do not start vendor work without this."

**The test for ownership** is the same one used in the [sample RACI (responsible, accountable, consulted, informed) rows](https://github.com/ChefPlex/tpm-templates/blob/main/examples/sample-raci-rows.md): when the vendor delivers something and it is wrong, whose calendar does the meeting land on? If the answer is "it depends," the SOW is not finished.

---

## 2. SOW, PWS or SOO: how much of the method you specify

Three kinds of work statement exist, and they sit on a dial. At one end you tell the vendor **how** to do the work. At the other you tell them **what** you need and let them propose the how.

| Type | What it says | Use it when | Watch for |
|:---|:---|:---|:---|
| **Statement of work (SOW)** | The activities the vendor will perform, often including method | You know the method and want it followed. A defined migration of a known list of services. | You can get exactly what you asked for and still not get the result you needed. |
| **Performance work statement (PWS)** | The required results and the measurable standard each must meet | You care about the outcome and can measure it | A standard nobody can measure is not a standard. |
| **Statement of objectives (SOO)** | What you want to achieve; the vendor proposes the approach | You do not yet know the best method and want the vendor's expertise to shape it | The SOO itself is not the commitment. The vendor's response is. |

The FAR states the direction it prefers. Agencies shall, to the maximum extent practicable, "Describe the work in terms of the required results rather than either "how" the work is to be accomplished or the number of hours to be provided" and "Enable assessment of work performance against measurable performance standards" ([FAR 37.602(b)](https://www.acquisition.gov/far/subpart-37.6), as of October 2026).

The same section is clear on the SOO: "Offerors use the SOO to develop the PWS; however, the SOO does not become part of the contract" ([FAR 37.602(c)](https://www.acquisition.gov/far/subpart-37.6), as of October 2026). The practical lesson carries to private work: **if you start from objectives, the vendor's proposed statement of work is the thing you must review line by line**, because that is what they will be held to.

In private contracts, "SOW" is the umbrella word for all three, and the PWS and SOO labels are rare. The dial still applies. Most good private SOWs are a blend: fixed method where you need it (security controls, tools, environments) and measurable results everywhere else.

---

## 3. Write a SOW that can be accepted or rejected

A SOW line is useful only if two reasonable people, reading it after the work is done, would agree on whether it was delivered. Every line that fails that test is a future dispute.

### Weak vs better

**Weak SOW line**

> Vendor will implement certificate rotation for platform services and provide documentation and knowledge transfer.

**Why this fails**

- **"Implement" has no finish line.** Implemented in one test environment? In production for every service? Running unattended for a month?
- **"Platform services" has no list.** The vendor will count the services that were easy. You will count the ones you needed.
- **"Documentation and knowledge transfer" has no acceptance.** Any document delivered will meet it.
- **No one accepts it, and no date applies.** So it is never late, and never done.

**Better SOW line**

> **Deliverable D3: Automated certificate rotation in production.** Vendor will enable automated rotation for the 40 services listed in Appendix B, in the production environment. **Acceptance criterion:** for each listed service, two consecutive scheduled rotations complete with no manual step and no service error, as shown in the rotation log. **Accepter:** Platform Engineering lead (one named person, recorded in Appendix A). **Due:** milestone M3. **Buyer dependency:** Buyer provides production change windows for all 40 services by milestone M2; a late window moves the D3 date day for day.

**Why this works**

- **The scope is a list,** so "done" is countable.
- **The acceptance criterion is observable** in a log, not a matter of opinion.
- **One person accepts it,** so there is no committee to wait on.
- **The buyer's own obligation is written down.** Most vendor delays that turn into disputes start with something the buyer was supposed to supply.

### What a complete SOW contains

There is no single legal standard for private SOW contents. The FAR lists the minimum for a statement of objectives: "(1) Purpose; (2) Scope or mission; (3) Period and place of performance; (4) Background; (5) Performance objectives, i.e., required results; and (6) Any operating constraints" ([FAR 37.602(c)](https://www.acquisition.gov/far/subpart-37.6), as of October 2026). The checklist in **Template A** below is this guide's synthesis for private work, built outward from that list. It is a practitioner's checklist, not a standard.

Three items on it are skipped more often than the rest, and each is expensive later:

1. **Explicit out-of-scope.** What the vendor will not do. Without it, every gap becomes a change request argument.
2. **Buyer dependencies with dates.** Access, environments, data, decisions, people. If the buyer is late, the SOW should say what moves.
3. **Transition and exit duties.** Written while everyone is friendly, because nobody negotiates them well at the end.

---

## 4. Acceptance: a named act by a named person

Acceptance is the moment the buyer confirms that the work meets the contract. It is not a feeling and it is not a status update. The FAR definition is a useful model: "Acceptance constitutes acknowledgment that the supplies or services conform with applicable contract quality and quantity requirements" and "Acceptance may take place before delivery, at the time of delivery, or after delivery, depending on the provisions of the terms and conditions of the contract" ([FAR 46.501](https://www.acquisition.gov/far/subpart-46.5), as of October 2026).

Three points carry over to any contract:

1. **Acceptance is a defined act.** Write down what the accepter does: sign a form, approve a ticket, send a written notice.
2. **The contract decides when it happens.** If the SOW is silent on timing, the dispute starts there.
3. **One role accepts.** The FAR puts it in a single place: "Acceptance of supplies or services is the responsibility of the contracting officer" ([FAR 46.502](https://www.acquisition.gov/far/subpart-46.5), as of October 2026). In your SOW, one named person accepts each deliverable. This matches the one-accountable-per-row rule in a [RACI](https://github.com/ChefPlex/tpm-templates/blob/main/raci-template-waterfall.md).

### Write the acceptance window into the SOW

For each deliverable, the SOW should say:

- **How long the accepter has to review** after delivery.
- **What a rejection must contain:** the specific criterion not met, in writing. "We do not like it" is not a rejection.
- **How many correction rounds** the vendor gets, and what happens after the last one.
- **What silence means.** Many contracts treat a deliverable as accepted if the buyer does not respond within the window. That is common practice, not a universal rule, and its exact form is a question for your legal team. Either way, decide it on purpose.

**The program-side risk is your own capacity.** If the accepter has no time to inspect deliverables, a "deemed accepted" clause turns their silence into approval of work nobody checked. Federal audits have found buyer-side oversight stretched past capacity. In one agency's own analysis of the staff overseeing its IT software contracts, "eight of nine staff exceeded a full workload" ([GAO-25-107437](https://files.gao.gov/reports/GAO-25-107437/index.html), as of October 2026). Before you sign, book the accepter's review time on their calendar for every milestone.

---

## 5. Paying for progress

Payment is the strongest lever you have after signature, so connect it to the things you care about.

The FAR separates two ideas that private contracts often blur. Performance-based payments "are the preferred Government financing method when the contracting officer finds them practical, and the contractor agrees to their use," and they "are contract financing payments that are not payment for accepted items" ([FAR 32.1001](https://www.acquisition.gov/far/subpart-32.10), as of October 2026). In plain terms: **paying a vendor for reaching an event helps their cash flow; it is not the same as agreeing the work is right.**

A practical private pattern follows from that:

- **Pay a smaller share on defined events** (kickoff complete, design approved, environment built). These keep the vendor funded.
- **Hold a meaningful share until acceptance of working output.** This is the money that keeps quality honest.
- **Tie the final payment to transition duties,** not just the last technical deliverable (see section 10).

There is no authoritative standard for the split. Percentages are a negotiation between procurement and the vendor. Your job is to make sure the milestones that carry money are the ones defined by an acceptance criterion, not by elapsed time.

**Weak:** "25% on signature, 25% at month 3, 25% at month 6, 25% on completion."
**Better:** "Payment 2 on acceptance of D2 per its criterion. Payment 3 on acceptance of D3. Final payment on acceptance of the transition deliverables in section 10."

The weak version pays for the calendar. The better one pays for results.

---

## 6. Change control on a contract

Scope will change. The question is whether it changes on paper with a price, or in a hallway conversation that both sides remember differently.

The federal model is strict about who can change a contract. A changes clause "permits the contracting officer to make unilateral changes, in designated areas, within the general scope of the contract. These are accomplished by issuing written change orders," and "The contractor must continue performance of the contract as changed" ([FAR 43.201](https://www.acquisition.gov/far/subpart-43.2), as of October 2026). The standard federal changes clause also puts a clock on the contractor: it must assert its right to an adjustment "within 30 days from the date of receipt of the written order" ([FAR 52.243-1](https://www.acquisition.gov/far/52.243-1), as of October 2026).

Three lessons carry to private work:

1. **Only named people can change scope.** Name one change authority on each side in the SOW. A request from anyone else is a conversation, not a change.
2. **Every change is written,** with its cost, schedule and risk impact stated before work starts.
3. **There is a clock.** Put a notice period in the SOW for either side to raise the impact of a change. Without it, impact claims arrive at invoice time.

**The rule that saves the most money: no work on verbal changes.** If an engineer on your side asks the vendor's engineer for "one small thing," it is either inside the SOW or it needs a change request. Tell your own team this at kickoff, because they are usually the source.

### Change request (fill in)

```
CHANGE REQUEST
ID:                       CR-___
Raised by / date:
SOW section affected:
Description of change:    (what is added, removed or altered, in SOW language)
Reason:
Schedule impact:          (which milestones move, by how much)
Cost impact:              (vendor estimate; fixed or not-to-exceed)
Risk impact:              (new risks, or existing risk log items affected)
Acceptance criterion:     (for any new or changed deliverable)
Buyer approver:           (the named change authority)
Vendor approver:          (the named change authority)
Decision / date:          Approved / Rejected / Deferred
```

Log approved changes against the SOW, and log the decision in your decisions register the same way you would any other. A change that lives only in email will not be found at renewal.

---

## 7. Running the vendor after signature

Signature is where most of the work starts, and where most buyer attention stops. A federal audit found contracting personnel "not always establishing or enforcing quality assurance surveillance plans (QASPs)," which meant the government might not receive the services it paid for ([GSA Office of Inspector General, Report A210064, 2023-02-09](https://www.gsaig.gov/content/gsas-administration-performance-based-contracts-puts-government-risk-unsatisfactory), as of October 2026). A quality assurance surveillance plan is simply the written plan for how the buyer will check the vendor's work. The failure is not specific to government. If nobody is assigned to look, nobody looks.

### SLI, SLO, SLA: get the words right

These three get used interchangeably and they are not the same thing. The cleanest definitions come from the Google Site Reliability Engineering book. It is a software reliability source, not a procurement standard, but the distinction is exact ([Google SRE Book, chapter 4](https://sre.google/sre-book/service-level-objectives/), as of October 2026):

| Term | Definition (verbatim) | In a vendor program |
|:---|:---|:---|
| **SLI** (service level indicator) | "a carefully defined quantitative measure of some aspect of the level of service that is provided" | The number you track: ticket response time, defect rate at first acceptance |
| **SLO** (service level objective) | "a target value or range of values for a service level that is measured by an SLI" | The target: 95% of severity-1 tickets answered within one hour |
| **SLA** (service level agreement) | "an explicit or implicit contract with your users that includes consequences of meeting (or missing) the SLOs they contain" | The target plus what happens when it is missed: a service credit, a fee reduction, a right to terminate |

**The practical test: if missing the target has no stated consequence, it is an SLO, not an SLA.** Many "SLAs" in vendor contracts are SLOs with a misleading label. That is not always wrong, because an SLO is still useful for running the relationship. It is wrong to rely on one in an escalation as though it carried a penalty.

The scorecard in **Template B** has a column for the consequence. A blank cell there tells you, in one glance, which of your targets have teeth.

### The governance cadence

There is no primary standard for vendor meeting cadence. This is a recommendation, and it scales down for small engagements.

| Cadence | Who | Purpose | Output |
|:---|:---|:---|:---|
| **Weekly working session** | TPM, vendor delivery lead, technical leads | Progress against milestones, blockers in both directions, upcoming buyer dependencies | Updated risk and dependency log, action items |
| **Monthly performance review** | TPM, vendor delivery lead, buyer accepters | Scorecard review, open change requests, acceptance status, invoice check | Scorecard for the period |
| **Quarterly business review (QBR)** | Sponsors on both sides, procurement, TPM | Trend across quarters, relationship health, renewal or exit signals | Decisions, and escalations closed or raised |

**Two habits make this work.** First, put buyer dependencies on the weekly agenda alongside vendor tasks. A vendor review that only discusses the vendor misses half the causes of slip. Second, check invoices against accepted deliverables every month. An invoice for work nobody accepted is the earliest signal that the acceptance process has quietly stopped running.

### Escalation

Write the escalation path into the SOW so nobody has to invent it under pressure. A three-tier ladder is common practice:

1. **Delivery leads** (the TPM and the vendor's delivery lead) try to resolve within a set number of business days.
2. **Account owners** (the vendor's account executive and the buyer's procurement owner or program sponsor).
3. **Executive sponsors** on both sides.

Each tier has a time limit, and the move to the next tier is automatic when the limit passes. An escalation path that requires someone to decide whether to escalate will not be used until too late.

### What goes in the risk log

Vendor risks and dependencies go in the program's [RAID (risks, assumptions, issues, dependencies) log](https://github.com/ChefPlex/tpm-templates/blob/main/raid-log-guide.md) like any other. The ones worth logging from day one: each buyer dependency in the SOW (as a dependency with a date), key-person risk on the vendor side, single-supplier concentration, and any SLO without a consequence that the program relies on. Transferring a risk to a vendor is a legitimate strategy, and the RAID guide covers it. Transfer only works if the contract actually carries the risk, so check the clause before you mark it transferred.

---

## 8. Third-party risk

A vendor can deliver on time and still be the way your program gets breached. Security review of the vendor is a separate track from delivery performance, and both need an owner.

This section is short on purpose. The security program side is covered elsewhere: the [Security TPM role guide](https://github.com/ChefPlex/security-program-playbooks/blob/main/security-tpm-role-guide.md) on why vendor relationships are more complex on security programs, and [AI tooling with regulated data](https://github.com/ChefPlex/security-program-playbooks/blob/main/ai-tooling-regulated-data.md) for AI vendors.

**References worth knowing:**

- **NIST SP 800-161 Rev. 1** (National Institute of Standards and Technology, *Cybersecurity Supply Chain Risk Management Practices for Systems and Organizations*). Published May 2022, with an update dated 2024-11-01 that supersedes the original text ([NIST CSRC](https://csrc.nist.gov/pubs/sp/800/161/r1/final), as of October 2026). It is the reference framework for supply chain risk. Read it for structure; do not expect a checklist.
- **CISA Vendor SCRM Template** (Cybersecurity and Infrastructure Security Agency, supply chain risk management, April 2021). A standard set of questions for asking a vendor about its information and communications technology (ICT) supply chain risk, meant to work for public and private organizations of any size ([CISA](https://www.cisa.gov/sites/default/files/publications/ICTSCRMTF_Vendor-SCRM-Template_508.pdf)). Use it as a question bank when comparing vendors before you sign.

### Reading a vendor's SOC 2 report

What a SOC 2 (System and Organization Controls 2) report is, and the difference between Type I and Type II, is covered in the [Compliance Framework Reference](https://github.com/ChefPlex/security-program-playbooks/blob/main/compliance-framework-reference.md#soc-2---system-and-organization-controls-2). The American Institute of CPAs (AICPA), which owns the framework, describes these reports as giving users information to assess "the risks associated with outsourcing services" ([AICPA](https://www.aicpa-cima.com/resources/landing/system-and-organization-controls-soc-suite-of-services), as of October 2026).

Receiving the report is not the same as reading it. These are the things to look for. They are this guide's practitioner checklist, not AICPA requirements:

- **The period covered.** Does it cover the months you care about, or did it end a year ago?
- **The system covered.** Is the service in your SOW inside the report's scope, or is it a different product from the same company?
- **The opinion.** Is it qualified, and are there exceptions noted in the testing?
- **Subservice organizations carved out.** If the vendor relies on another provider that is excluded from the report, that provider's controls are untested from your point of view.
- **Complementary user entity controls.** Controls the report assumes **you** perform. If you do not perform them, part of the assurance does not apply to you.

### Clauses to check in the SOW or MSA

- **Security incident notification:** how fast the vendor must tell you, through what channel, and what they must provide. Connect it to your [incident playbook](https://github.com/ChefPlex/security-program-playbooks/blob/main/cyber-incident-playbook.md) so the vendor's contact is already in it.
- **Data handling:** where your data lives, who can access it, and what happens to it at exit.
- **Right to evidence:** your ability to request current audit reports each year.
- **Regulated data:** if the vendor will handle protected health information, a business associate agreement (BAA) is required; the [Compliance Framework Reference](https://github.com/ChefPlex/security-program-playbooks/blob/main/compliance-framework-reference.md) covers it.

---

## 9. Key-person and subcontractor risk

Neither of these has a good primary source on how often it causes failure. Both are mechanisms worth controlling anyway, because they are cheap to address before signature and expensive after.

### Key-person risk

You chose the vendor partly because of two or three specific people. The contract usually lets the vendor replace them. Controls to put in the SOW:

- **Name the key personnel** and their roles in an appendix.
- **Require notice and buyer approval** before a key person is replaced, with the replacement's qualifications stated.
- **Require an overlap period** in which the outgoing and incoming person both work on the program.
- **Make documentation a deliverable,** with acceptance criteria, so that knowledge lives in a file and not in one head.

Track staffing stability on the scorecard. A vendor rotating its team every quarter is telling you something before the milestones do.

### Subcontractor risk

Your vendor may hand part of the work to someone you have never met, and the buyer is usually the last to know. You contract with the vendor, not with its subcontractors, so the SOW is the only place to get visibility. Controls to put in it:

- **Disclosure:** the vendor names every subcontractor that will touch your work or your data.
- **Approval:** new subcontractors need your written approval.
- **Flow-down:** the security, data, confidentiality and key-person terms in your contract pass down to each subcontractor. "Flow-down" means the vendor must put the same obligations into its own subcontracts.
- **Single point of accountability:** the vendor stays responsible for subcontractor performance. Your scorecard measures the vendor, not the subcontractor.

---

## 10. Exit and transition

Every vendor engagement ends: completion, renewal with someone else, termination, or the vendor being acquired. The exit terms are the ones you negotiate with the most leverage at the start and the least at the end.

The federal continuity-of-services clause is a good model of what to cover. The outgoing contractor must, on notice, "furnish phase-in, phase-out services for up to 90 days after this contract expires" and "negotiate in good faith a plan with a successor"; must "allow as many personnel as practicable to remain on the job to help the successor"; and is reimbursed "for all reasonable phase-in, phase-out costs" ([FAR 52.237-3](https://www.acquisition.gov/far/52.237-3), as of October 2026). The numbers will differ in a private deal. The elements should not.

**Write these into the SOW:**

| Exit element | What the SOW should say |
|:---|:---|
| **Transition duty survives termination** | The vendor's transition obligations apply however the contract ends, including termination for cause |
| **Transition period** | How long the vendor supports the handover after end date, and at what rate |
| **Transition plan** | A deliverable, due a set time before end date, with dates for each knowledge-transfer step |
| **Knowledge transfer deliverables** | Runbooks, configuration, architecture, open defects, credentials inventory: each with acceptance criteria |
| **Data return and deletion** | What is returned, in what format, by when, and written confirmation of deletion |
| **Access revocation** | The vendor's accounts and access are removed on a date, and you verify it |
| **Successor access** | Your next provider can talk to the vendor's people during transition |
| **Who pays** | Whether transition work is in the fixed price or billed separately |

At the end, the vendor row in your [close-out report](https://github.com/ChefPlex/tpm-templates/blob/main/program-close-out-report-template.md) should show each of these as done, with the accepter's name. Access revocation is the one most often missed, and the one a security reviewer will check first.

---

## Worked example: Larkspur Logistics and its certificate vendor

*Larkspur Logistics and Corvid Trust are fictional companies. All names, figures and dates are invented for illustration.*

Larkspur is running the platform encryption migration from the [sample ADR](https://github.com/ChefPlex/tpm-templates/blob/main/examples/sample-adr.md): one central certificate authority (CA) with automated rotation. Larkspur buys integration services from the CA vendor, Corvid Trust, to connect its first 40 services.

**The first draft.** Procurement sent the TPM a SOW drafted from Corvid's standard template. Its core line read: "Corvid will implement certificate rotation for Larkspur platform services and provide knowledge transfer." Payment was split evenly across four calendar dates.

**The review.** The TPM ran the draft through Template A and marked eleven of eighteen rows as missing or failing the test. The three that mattered most: no service list, no acceptance criterion, and nothing on what Larkspur had to provide. The TPM rewrote the deliverable as shown in section 3 (40 named services, two clean rotations per service, one named accepter, change windows due from Larkspur at M2). Procurement moved the payments onto accepted deliverables. Legal added a transition clause and a 72-hour security incident notification.

**The acceptance dispute.** At M3, Corvid submitted D3 as complete. The Larkspur accepter checked the rotation log and found 36 of 40 services with two clean rotations. Four had rotated once, and one of those had needed a manual restart. The accepter rejected D3 in writing, naming the four services and the criterion each failed. Corvid did not argue, because there was nothing to argue about: the criterion was in the log. Corvid fixed the four within the correction round and D3 was accepted eleven days later. Under the first draft, this would have been a debate about what "implement" meant, with a calendar payment already made.

**The change request.** In week nine, a Larkspur engineer asked Corvid's engineer to add six more services "while you are in there." Corvid's delivery lead, following the SOW, declined to start and asked for a change request. The TPM raised CR-004: six services added to Appendix B, D3 date moved by two weeks, cost on a not-to-exceed basis, approved by the named change authority on each side. The six were delivered and accepted under the same criterion as the original 40.

**What the scorecard showed by month four.** Every milestone delivered within a week of plan, first-pass acceptance at 9 of 10 deliverables, one key person replaced with three weeks of overlap, and one SLO with no consequence (documentation turnaround) that the TPM flagged at the QBR for the renewal negotiation.

---

## Where this breaks

**Small vendors with no procurement process.** A three-person firm may not have a delivery lead, a QBR, or the patience for an eighteen-item SOW review. Keep the core: a deliverable list, an acceptance criterion per deliverable, one accepter, and payment on acceptance. Drop the ceremony, not the criteria.

**Time-and-materials work.** When you pay for hours rather than results, acceptance criteria are harder to attach and the vendor's incentive is not to finish. If the outcome cannot be defined, at least define what each period's hours must produce and review it monthly. If it can be defined, consider whether this should be a results-based SOW instead.

**The only supplier.** If the vendor is the only one who can do the work, your leverage is mostly gone. Scorecards and escalations still help, but the real control is reducing the dependency over time. Record it as a concentration risk, as the sample ADR does, and give it a revisit trigger.

**Contracts you inherit.** You will often take over an engagement where the SOW is already signed and weak. You cannot rewrite it, but you can still name accepters, write acceptance criteria into the next change request, and start a scorecard. Treat it as a rescue: [Rescuing Work That Is Off Track](https://github.com/ChefPlex/tpm-templates/blob/main/rescuing-work-that-is-off-track.md) applies to vendor relationships too.

**Legal owns the paper.** Some organizations do not let the program touch contract wording. Then your output is a marked-up review using Template A, sent to legal with each gap explained in one line. You are still the only one who can tell whether the scope is complete.

**Federal rules do not bind private buyers.** The FAR is used here as a model. If you do work for a federal agency, the actual rules apply in full and your contracting officer, not this guide, is the authority.

**A scorecard can become theater.** If nobody acts on a red cell, the monthly review becomes a ritual. Every red cell needs either an action with an owner or a written decision to accept it.

---

## Template A: SOW review checklist

Use this on every SOW before signature, and on any inherited SOW in your first week. Mark each row Pass, Fail or Missing. Send failures to procurement and legal with the one-line reason.

```
SOW REVIEW CHECKLIST
SOW title / version:
Vendor:
Reviewed by / date:
```

| # | Section | What it must say | Test | Pass / Fail / Missing | Note |
|:---|:---|:---|:---|:---|:---|
| 1 | Purpose and background | Why the work exists and the context the vendor needs | Could a new vendor engineer explain the goal from this alone? | | |
| 2 | In scope | The work, as a list where possible (services, systems, sites) | Can you count it? | | |
| 3 | Out of scope | What the vendor will not do | Does it name the obvious adjacent work? | | |
| 4 | Deliverables | Each deliverable, numbered | Is each one a thing, not an activity? | | |
| 5 | Acceptance criteria | One observable criterion per deliverable | Would two people agree whether it was met? | | |
| 6 | Accepter | One named role or person per deliverable | Is there exactly one per deliverable? | | |
| 7 | Acceptance process | Review window, rejection format, correction rounds, meaning of silence | Is "deemed accepted" decided on purpose? | | |
| 8 | Milestones and dates | Dates or relative milestones for each deliverable | Is every deliverable on the schedule? | | |
| 9 | Performance standards | Targets for ongoing service and how each is measured | Is each one measurable, with a named data source? | | |
| 10 | Buyer dependencies | What the buyer supplies, by when, and what moves if late | Is every buyer obligation dated? | | |
| 11 | Key personnel | Named roles, replacement approval, overlap period | Can the vendor swap the lead without telling you? | | |
| 12 | Subcontractors | Disclosure, approval, flow-down, vendor stays accountable | Do you know who will touch your data? | | |
| 13 | Reporting and cadence | What the vendor reports, how often, to whom | Does it match your governance cadence? | | |
| 14 | Change control | Named change authority each side, written requests, impact notice period | Can anyone else change scope? | | |
| 15 | Payment | Payments tied to accepted deliverables; final payment tied to transition | Does any payment depend only on the calendar? | | |
| 16 | Security and data | Data location, access, handling, right to evidence | Has the security review signed off? | | |
| 17 | Incident notification | Time limit, channel, content | Is the vendor contact in your incident plan? | | |
| 18 | Transition and exit | Transition plan, period, knowledge transfer, data return, access revocation, successor access, cost | Does it survive termination for cause? | | |
| 19 | Termination | Rights on each side, notice, what is paid on termination | Do you know what an early exit costs? | | |

**Result:** ___ Pass / ___ Fail / ___ Missing. **Do not sign with any Fail or Missing on rows 2, 5, 6, 10 or 18** without a written decision to accept the gap.

---

## Template B: Vendor scorecard

Fill in monthly. Review at the monthly performance review, and bring the trend to the QBR. Each row answers the same five questions: what is required, what standard it must meet, how it is measured and from what source, how often, and what happens if it is missed.

```
VENDOR SCORECARD
Vendor:                       SOW / contract reference:
Period:                       Prepared by:
Overall status:               Green / Amber / Red
```

**Delivery and service**

| Requirement | Standard (SLO) | Measure and source | Frequency | This period | Trend | Consequence if missed |
|:---|:---|:---|:---|:---|:---|:---|
| Milestones delivered on plan | e.g. within 5 business days of SOW date | Milestone plan vs delivery date | Monthly | | ↑ → ↓ | |
| First-pass acceptance | e.g. 90% of deliverables accepted without rejection | Acceptance records | Monthly | | | |
| Defects found after acceptance | e.g. none at severity 1 | Defect tracker | Monthly | | | |
| Ticket response time | e.g. 95% of severity-1 within 1 hour | Vendor ticket system | Monthly | | | |
| Change requests raised | Count, and how many from each side | Change log | Monthly | | | n/a |
| Open RAID items owned by vendor | Count, and any past due | RAID log | Monthly | | | n/a |
| Staffing stability | Key personnel changes, with notice given | Vendor report vs SOW appendix | Monthly | | | |
| Invoice accuracy | Every invoice line matches an accepted deliverable or approved CR | Invoice review | Monthly | | | |

**A blank "Consequence if missed" cell means the target is an SLO, not an SLA.** That is allowed. Know which ones they are before you escalate on them.

**Buyer side** (the half most scorecards leave out)

| Buyer obligation | Due | Met? | Effect if late |
|:---|:---|:---|:---|
| | | | |

**Relationship**

| Item | Status |
|:---|:---|
| Sponsor-to-sponsor check this quarter | Done / Not done |
| Open escalations (tier and age) | |
| Subcontractor changes this period | |
| Security evidence current (audit report period end date) | |
| Exit readiness: transition plan delivered and current | Yes / No / Not yet due |

**Actions from this review**

| Action | Owner | Due |
|:---|:---|:---|
| | | |

---

## The test

If this vendor vanished on Friday, could someone who was never in the room read the SOW and the scorecard and say what was owed, what was accepted, and what was paid?

If yes, you are running a vendor program. If they would have to go and ask people, you are running a relationship, and relationships do not survive a change of staff on either side.

---

## Related

- [Program Phases Playbook](https://github.com/ChefPlex/tpm-templates/blob/main/program-phases-playbook.md): the Buy vs. Build record and the Vendor SOW / MSA gate
- [Program Charter Template](https://github.com/ChefPlex/tpm-templates/blob/main/program-charter-template.md): where the vendor's role and procurement review first appear
- [RAID Log Guide](https://github.com/ChefPlex/tpm-templates/blob/main/raid-log-guide.md): vendor risks, the Transfer strategy, external dependencies
- [Sample RACI Rows](https://github.com/ChefPlex/tpm-templates/blob/main/examples/sample-raci-rows.md): one accountable owner per row
- [Sample ADR](https://github.com/ChefPlex/tpm-templates/blob/main/examples/sample-adr.md): the encryption migration and its single-vendor dependency
- [Program Close-Out Report Template](https://github.com/ChefPlex/tpm-templates/blob/main/program-close-out-report-template.md): the vendor handoff row
- [Rescuing Work That Is Off Track](https://github.com/ChefPlex/tpm-templates/blob/main/rescuing-work-that-is-off-track.md): for an inherited, late vendor engagement
- [Security Program Intake and Kickoff](https://github.com/ChefPlex/security-program-playbooks/blob/main/security-program-intake-kickoff.md): the vendor and third-party review gate
- [Compliance Framework Reference](https://github.com/ChefPlex/security-program-playbooks/blob/main/compliance-framework-reference.md): SOC 2 and HIPAA business associate agreements
- [Cyber Incident Management Playbook](https://github.com/ChefPlex/security-program-playbooks/blob/main/cyber-incident-playbook.md): third-party compromise and vendor notification

---

*Part of the [ChefPlex TPM portfolio](https://github.com/ChefPlex/tpm-templates/blob/main/PORTFOLIO-GUIDE.md). Maintained by [Eric White](https://www.linkedin.com/in/edwhite). Licensed under [CC BY 4.0](LICENSE).*
