# Stakeholder Engagement Playbook

A communications plan tells people what is happening. A stakeholder engagement plan decides whose alignment you actually need, and how you earn it. They are not the same document, and confusing them is why programs with beautiful status reports still stall: everyone is informed, and nobody is aligned.

For a TPM [Technical Program Manager], this is not a soft skill on the side of the job. It is most of the job. You own the outcome and almost none of the people. The program moves at the speed of the alignment you can build across teams that do not report to you. Engagement is the work of building the coalition that delivers, not the courtesy of keeping an audience updated.

This playbook covers how to identify the stakeholders who matter, analyze where they stand, and move them - including the ones who start out skeptical or indifferent - using influence rather than authority.

---

## 1. Identify: Who Actually Has a Stake

Start wider than the org chart. A stakeholder is anyone who can help the program, block it, or is materially affected by it. The ones who sink programs are usually not on the kickoff invite:

- **Decision authority** - who can say yes or no to scope, budget, or launch.
- **Resource owners** - who controls the people or systems you depend on but do not command.
- **Gatekeepers** - security, legal, compliance, architecture review. A late no from any of them is the most expensive no there is.
- **The quiet veto** - the senior engineer or ops lead who will not sit in the steering committee but whose skepticism can stall adoption after launch.
- **The affected** - the teams and users whose work changes when you ship.

If you cannot name who could quietly kill this program six weeks in, you have not finished the map.

---

## 2. Analyze: Power, Interest, and What They Actually Want

### The Power / Interest Grid

The standard first cut. Place each stakeholder by how much **power** they have over the program and how much **interest** they have in it. The quadrant sets the engagement strategy.

| | Low Interest | High Interest |
|---|---|---|
| **High Power** | **Keep Satisfied** - enough information to stay comfortable; engage when their domain is touched. A high-power stakeholder who feels blindsided becomes high-interest fast, and not on your side. | **Manage Closely** - your core coalition. Involve early, co-own the decisions, high-touch cadence. Their alignment *is* the program. |
| **Low Power** | **Monitor** - light, routine communication. Do not spend scarce engagement time here. | **Keep Informed** - interested but not deciding. Often your best allies and your early-warning system; keep them close and they surface problems before the powerful stakeholders see them. |

Two disciplines most people skip:

- **Positions move.** Power and interest change as the program crosses phase gates and as risk rises. Re-map at each major milestone; a grid built once at kickoff is fiction by launch.
- **Power is not only the org chart.** Legitimacy (whose concern is seen as valid) and urgency (whose issue is loud right now) shift real influence. The person with the loudest legitimate concern this month has power the title does not show.

### Know Three Things About Everyone You Must "Manage Closely"

The grid tells you how much to engage. It does not tell you how to move someone. For every stakeholder whose alignment you actually need, know:

- **Their win** - what does success look like *for them*, in their terms, on their scorecard? You will frame every ask in this language.
- **Their concern** - what are they actually afraid of? Loss of control, more work for their team, a past program that burned them, an incentive that points the other way.
- **Their currency** - what do they value that you can offer? Recognition, information, a reciprocal favor, cover with their own leadership, a problem of theirs you can solve.

If you cannot fill in those three for a key stakeholder, that gap is your next conversation, not your next status report.

---

## 3. Engage: Influence Without Authority

This is the craft. When you cannot mandate cooperation, you earn it. A few things that consistently work:

**Lead with their interest, not your ask.** Nobody reprioritizes to help *your* program. They reprioritize because you have connected your program to *their* win. Frame the request in the language of their scorecard, not yours.

**Build the coalition before the meeting, not in it.** Decisions are made in the hallway; meetings ratify them. Pre-wire every significant decision one-on-one with the people who matter, so the steering committee is a confirmation and not a fight. A key stakeholder should never be surprised in a room - surprise reads as disrespect and hardens positions.

**Make it "us versus the problem."** The moment a disagreement becomes you versus them, you have lost, even if you win the argument. Name the shared problem, put it on the wall between you, and solve it together.

**Address the reason, not the objection.** A no is a surface. Under it is a reason - fear, workload, a bad past experience, a misaligned incentive. You do not overcome the objection by arguing it; you dissolve it by addressing the reason. "This will overload my team" is solved with sequencing or help, not with a better slide.

**Escalate the decision, not the person - and late, not early.** Escalation is a tool, not a failure, but it spends relationship capital. Use it only after you have genuinely worked the problem at the working level, and escalate the *decision that is stuck* with a clear recommendation, never a complaint about a *person*. An escalation that arrives as "here is the call I need and why" keeps the relationship; one that arrives as "make them cooperate" burns it.

---

## 4. Engage Across the Lifecycle

Alignment is cheapest at the start and most expensive at the end.

- **Kickoff / charter.** The charter conversation *is* the alignment. If you cannot get a stakeholder to agree to the problem, scope, and Definition of Done on paper, you do not have their alignment - you have their politeness. Surface the disagreement now, when it is cheap.
- **Execution.** Re-engage at phase gates and whenever risk rises. The cost of a misaligned high-power stakeholder compounds the longer it goes unaddressed.
- **Launch.** The quiet-veto stakeholders from Section 1 decide whether the thing you shipped actually gets adopted. Engage them before go-live, not after.
- **Close.** The program ends; the relationships do not. The coalition you built is the asset you carry into the next program. Close the loop, share the credit widely, and the next alignment starts from trust instead of zero.

---

## 5. Where This Breaks

- **The dead map.** A stakeholder grid built once and never revisited is worse than none - it gives false confidence while the real positions have moved.
- **Communication mistaken for engagement.** Sending a status report is not engaging a stakeholder. Engagement is a two-way relationship; a newsletter is not.
- **Engaging only the friendly.** It is comfortable to spend time with the stakeholders who already agree. The program is decided by the ones who do not.
- **Escalating too early or too late.** Too early burns capital and signals you cannot operate without authority. Too late turns a solvable misalignment into a surprise crisis. The judgment on timing is the skill.
- **Over-engineering the artifact.** The map and the analysis are tools for having better conversations, not deliverables to polish. If the document is immaculate and you have not talked to the person, you have done the wrong work.

---

## How This Fits With the Other Tools

- The [Communications Plan Template](communications-plan-template.md) is how you *execute* the engagement strategy - the cadence, channels, and message discipline. This playbook decides *whose* alignment you need and *how you earn it*; the comms plan runs the machine that keeps them informed.
- The [RACI Template (Waterfall)](raci-template-waterfall.md) and [RACI Template (Agile)](raci-template-agile.md) settle who actually owns each decision, which is often the thing a stakeholder conflict is really about.
- The [Steering Committee Deck Structure](https://github.com/ChefPlex/program-reporting-frameworks/blob/main/steering-committee-deck-structure.md) is where you bring the decision you have already pre-wired one-on-one.
- The [Influence Without Authority Plan](https://github.com/ChefPlex/ai-automations/blob/main/prompts/director-review/influence-without-authority-plan.md) prompt helps you work a *specific* hard situation with a *specific* stakeholder.

---

*Version 1.0. Propose changes via pull request.*
