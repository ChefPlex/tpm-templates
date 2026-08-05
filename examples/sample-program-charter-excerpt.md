# Sample Program Charter Excerpt

A charter is only as strong as its core: the problem it names, the outcomes it commits to, and the line it draws around the work. Those three sections are where most charters quietly fail - vague enough to approve, vague enough to argue about later. The PMI's own numbers make the cost concrete: scope creep hits about half of all projects, and projects without clearly defined objectives fail roughly a third of the time. This example shows the difference on the sections that carry the weight.

**Scenario (sanitized).** An "Encryption in Transit Modernization" program. The excerpt below is Sections 1 through 3 of the [Program Charter Template](../program-charter-template.md) - Why, What, and Scope. Numbers, dates, and org names are illustrative; sanitize to your context before use.

---

## Weak

> **Problem:** Improve our encryption posture across the platform to reduce risk and support compliance.
>
> **Objective:** Increase encryption coverage and strengthen platform security.
>
> **Scope:** Encryption across platform services.

### Why This Fails

Every line is a direction, not a commitment. "Improve," "increase," "strengthen" have no number, no baseline, and no date, so no one can ever say the program is done - or hold it accountable if it is not. "Encryption across platform services" is not a scope, it is a category; with no explicit out-of-scope, the program will absorb encryption-at-rest, third-party SaaS, and every adjacent request until it collapses under its own weight. A sponsor can approve this charter without agreeing to anything, which is exactly the problem: it creates the illusion of alignment without the substance.

---

## Better

> ### 1. Why Are We Doing This
>
> **Problem Statement.** Encryption-in-transit coverage across platform services is at 10 percent (30 of roughly 300 services). Every unencrypted service that carries customer data is a direct trust risk and a live finding in the DSA [Digital Services Act] compliance assessment. Because there is no default-TLS standard, the gap grows about 5 percent each quarter as new services ship unencrypted.
>
> **Strategic Alignment.** Supports the FY compliance commitment and the enterprise trust objective. **Cost of inaction:** the DSA finding stays open through the Q2 audit, and the remediation surface grows every quarter we wait.
>
> ### 2. What We Are Building
>
> **Objectives (specific and measurable):**
> 1. Raise encryption-in-transit coverage from 10 percent to 80 percent or more of platform services by Dec 31.
> 2. Establish and enforce a TLS 1.2 minimum standard so new services ship encrypted by default - zero net-new unencrypted services after Mar 1.
> 3. Close the DSA finding on the 12 highest-exposure services by the Mar 31 contractual deadline.
>
> **Definition of Done (the contract):**
>
> | Success Criterion | Measurement | Target |
> |-------------------|-------------|--------|
> | Coverage | % of platform services with TLS in transit | 80%+ by Dec 31 |
> | Default standard | Net-new unencrypted services per quarter | 0 after Mar 1 |
> | Compliance finding | DSA finding status | Closed by Mar 31 |
>
> ### 3. Scope
>
> **In Scope:** the ~300 platform services in the Core and Data orgs; the TLS 1.2 minimum standard plus a CI enforcement gate; remediation of the 12 audit-flagged services.
>
> **Out of Scope:** encryption at rest (separate program); third-party SaaS not on the platform; edge and client-side TLS termination changes; the ~40 legacy services slated for decommission by Q3 (tracked, not remediated). Anything not explicitly listed in scope above.

### Why This Works

The problem has a baseline (10 percent), a magnitude (30 of 300), a named exposure (the DSA finding), and a rate of decay (5 percent a quarter) - a sponsor understands the stakes without asking a single follow-up. The objectives are testable: each one has a number and a date, so "done" is a fact, not an opinion, and the Definition of Done table turns that into a contract anyone can check. The scope draws a hard line, and the out-of-scope list does the real work - it names the four things this program will be asked to absorb and refuses them in writing, before the requests arrive.

---

## The Pattern That Works

The core of a charter has to answer four questions before it is worth an approval:

1. **What is true today?** A problem with a baseline and a number, not an adjective.
2. **What will be true when we are done?** Objectives that are specific and time-bound, and a Definition of Done a reasonable person could grade yes or no.
3. **What are we not doing?** An explicit out-of-scope list, because scope is defended by what it excludes.
4. **Why does it matter now?** A cost of inaction that gets worse with delay.

If the charter cannot answer those four, it is not ready for sign-off. A blank or vague section is not a formatting gap - it is the program telling you where the alignment does not yet exist.

---

## A Note on the Half-Filled Charter

The instinct under pressure is to soften the charter so it is easier to approve: round the numbers off, leave the out-of-scope list for later, keep the objectives directional so no one can miss them. This feels like progress. It is the opposite.

A half-filled charter is worse than no charter, because it creates the illusion of alignment. Everyone signs, everyone reads their own meaning into "improve encryption posture," and the disagreement surfaces months later as a scope fight or a missed date nobody agreed to. The discipline of the charter is not the document - it is forcing the hard conversations to the front, when they are cheap, instead of the back, when they are not. If you cannot get sponsor sign-off on a specific charter, you do not have a program yet. That is the most valuable thing the charter can tell you.

---

*Part of the [tpm-templates](https://github.com/ChefPlex/tpm-templates) repo. See the [Program Charter Template](../program-charter-template.md) for the full framework.*
