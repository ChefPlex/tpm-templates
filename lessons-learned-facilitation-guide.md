# Lessons Learned Facilitation Guide

A lessons learned session is worth doing only if it generates honest insight. A session where everyone says things went well, nobody names what actually went wrong, and the output is a list of vague platitudes ("communication could be better") isn't a lessons learned session. It's a ritual that consumes an hour and produces nothing useful.

This guide is about running the version that's actually useful - the one where people say the thing they actually think, the root causes get surfaced, and the output is specific enough that the next program team can do something with it.

---

## When to Run It

At program close-out, before resources are released and before the team disperses. It is the session most often skipped, and the one most worth keeping. The further you get from the program, the hazier the memory and the lower the participation. Run it within two weeks of final delivery.

For long programs, also consider a mid-program retrospective at a major milestone. You don't need to wait until the end to capture learning.

---

## Who Should Participate

The core delivery team: TPM, engineering lead(s), product or program owner, and key individual contributors who were in the work. Limit to 8-12 people if possible - larger groups produce less honest conversation.

The executive sponsor should not be in the main session. Their presence changes what people say. Brief them separately after the session with the key outputs.

---

## Pre-Work - What to Do Before the Session

### Collect data

Do not walk in cold. Before the session, gather:
- The original charter and Definition of Done
- Final milestone actuals vs. planned dates
- Budget actuals vs. plan
- Key decisions made during the program and when they were made
- RAID log - what risks materialized, what issues took longest to resolve
- Status report history - when did the program go Yellow or Red and why

This data grounds the conversation in facts rather than impressions. Impressions are useful but they drift toward recency and toward whoever speaks loudest.

### Pre-survey (optional but recommended)

Send a short anonymous survey 2-3 days before the session with four questions:

1. What is the one thing this program did really well that we should repeat?
2. What is the one thing this program did that we should never do again?
3. What surprised you most about how this program ran?
4. What would you tell the next team that takes on a program like this?

Read the responses before the session. They tell you where the honest conversation is and where the session needs to go.

---

## Facilitation Principles

**Psychological safety is the prerequisite.** People will only say what they actually think if they believe it's safe to say it. Open the session by naming this explicitly: the goal is learning, not blame. No names attached to specific problems unless the person wants their name attached.

**Separate facts from opinions.** "The compliance review started too late" is a fact that can be verified against the timeline. "Leadership did not prioritize this program" is an interpretation. Both are useful, but treat them differently in the discussion.

**Root causes, not symptoms.** "We were always behind schedule" is a symptom. "We underestimated the service inventory gap by 40%" is a root cause. "We had no process for escalating cross-team dependency slippage before it became a crisis" is a root cause. Push past the first-level observations.

**Bias toward specificity.** "Communication could be better" is not a lesson. "Status reports went out consistently but stakeholders didn't know where the document repository was until week six, which generated repeated status questions that duplicated what was already published" is a lesson. Push for the specific version of every general observation.

**The facilitator doesn't defend.** If you're the TPM and you're also facilitating, this is hard. Something will come up that's a critique of something you did. The facilitation instinct - to explain, to defend, to provide context - works against the session. Take notes, ask clarifying questions, and address your own items in the output if needed. Do not defend in the moment.

---

## Session Structure (90 minutes)

### Opening - 10 minutes

Welcome the team, name the purpose, and establish the ground rules:
- This session is about learning, not judgment
- All observations are valid - there is no wrong answer
- We are looking for root causes, not symptoms
- Nothing said here is attributed to a person; themes go into the close-out report

Walk through the program timeline briefly using actual data - major milestones, key decision points, when the program was Green / Yellow / Red and why. This resets everyone's memory from "how I remember it" to "what actually happened."

### What Worked - 20 minutes

Start positive. This isn't just about tone - it surfaces practices worth repeating, which is as valuable as identifying what to avoid.

**Facilitation prompt:** "What did this program do well that we should intentionally repeat on the next program?"

For each item, push for specificity:
- What exactly was the practice?
- Why did it work? What made it effective in this context?
- Is it transferable? Would it work in a different program context?

Write everything on a shared surface (whiteboard, shared doc, Miro). Do not filter during capture. Filter during synthesis.

### What Did Not Work - 30 minutes

The most important part of the session. This is where the real learning is.

**Facilitation prompt:** "What would you do differently if you were starting this program over tomorrow?"

For each item, push deeper:
- What specifically happened? (fact)
- Why did it happen? (root cause)
- What would have prevented it? (lesson)
- Is it specific to this program or would it happen again in a similar context? (transferability)

**Common root causes to probe for:**
- Scope that was unclear at the start and expanded during execution
- Assumptions made at planning that turned out to be wrong
- Dependencies that were identified but not managed proactively
- Risks that were logged but not escalated when they should have been
- Decisions that were deferred too long and created downstream problems
- Resources that were committed but not available when needed

Do not rush this section. Thirty minutes is about right for a medium-complexity program. If the group is engaged and specific insights are emerging, let it run.

### Surprises - 15 minutes

**Facilitation prompt:** "What happened that nobody predicted at the start of this program?"

Surprises are often where the most useful institutional learning lives - the things nobody thought to put in the RAID log because nobody saw them coming. They also tend to be the things that recur across programs because nobody captures them.

For each surprise:
- Could it have been anticipated? What information would have surfaced it earlier?
- What would have been the right response if we had seen it coming?
- Should it be in the RAID log template for future programs?

### What Would You Tell the Next Team - 10 minutes

**Facilitation prompt:** "If you were handing this off to a new team starting a similar program tomorrow, what is the most important thing they should know that's not obvious?"

This question surfaces the tacit knowledge that lives in the team's experience but is hard to extract with direct questions. Often the most practical and memorable lessons come from this prompt.

### Close - 5 minutes

Summarize the key themes - don't read back everything, identify the 3-5 most important insights.

Name the follow-up: who is writing the close-out report, when it will be distributed, and what happens with the action items from this session.

Thank the team genuinely. They spent time on a hard program and then spent additional time reflecting on it honestly. That is worth acknowledging.

---

## Output

Within one week of the session, produce:
- **Lessons Learned Summary** - 1-2 pages, organized into What Worked / What Did Not Work / What Surprised Us / Recommendations for Future Programs
- **RAID Log Template Updates** - any risks or assumptions that came up as surprises should be added to the template so future programs start with them already logged
- **Specific Action Items** - if the session surfaced process improvements, infrastructure investments, or tools the organization should build, assign owners and dates

The summary goes into the close-out report and into whatever knowledge management system the organization uses. If the organization doesn't have a knowledge management system for this kind of institutional learning, that's itself a lesson worth documenting.

---

## Common Facilitation Failures and How to Avoid Them

**The session turns into a gripe session.** If the conversation becomes a list of complaints without root causes or recommendations, redirect: "That's a real problem - what do you think caused it and what would have prevented it?"

**Nobody says anything critical.** Usually means the psychological safety isn't there. Try breaking into pairs for 5 minutes and then sharing to the group - it's easier to say something critical to one person than to a room.

**The same person dominates.** Call explicitly on quieter team members: "We haven't heard from [name] yet - what was your experience with that?"

**The session produces vague outputs.** Before closing each item, ask: "If a new TPM read this lesson, would they know what to do differently? If not, what would make it more specific?"

**The close-out report never gets written.** Assign the report owner in the session, not after. Give them a due date. The lessons learned session produces no value if the output never gets documented and distributed.

---

*Version 1.0. Propose changes via pull request.*
