# RAG Evaluation Plan Template

How the program proves quality, and the gate that stops a regression from reaching users.

**Measure retrieval and generation separately.** They fail separately and the fixes are unrelated. If the right document was never retrieved, no amount of prompt work will save the answer. If the right document was retrieved and the answer is still wrong, the retrieval metrics will look fine while users lose trust.

## The Eval Set

The artifact that decides whether any of the other numbers mean anything, and the one most often skipped.

**Source the questions from real users.** Invented questions produce an eval set that passes while the system fails in production, because engineers write questions the system is already good at without meaning to.

| Property | Target |
|---|---|
| Question count | 100 minimum to start, 300+ before general availability |
| Sourced from real users | 100% |
| Has a known correct answer | 100% |
| Has a known source document | 100% |
| Includes unanswerable questions | 10-15% |
| Includes permission-boundary questions | 5-10% |
| Reviewed by a subject matter expert | 100% |
| Held-out set the team does not tune against | 20-30% of questions, kept separate |

**Keep a held-out set.** Engineers tuning prompts, chunking, and retrieval against the full eval set will fit it, and the scores will rise while production quality does not. Split off a held-out portion, restrict access to it, and run it only at milestone gates. If the tuned set improves and the held-out set does not, the change fitted the test.

The unanswerable set matters more than it looks. A system that confidently answers a question the corpus cannot support is worse than one that says it does not know, and nothing else in the eval catches that behavior.

The permission-boundary set is questions where the answer exists in the corpus but the asking user is not entitled to it. Correct behavior is a refusal, not an answer.

## Retrieval Metrics

| Metric | What it measures | Target |
|---|---|---|
| Recall@K | Was the correct document in the top K retrieved | > ____ |
| Precision@K | How much of what was retrieved is relevant | > ____ |
| MRR | How high the first correct result ranks | > ____ |

Recall is the one to optimize first. A document that is never retrieved cannot be used, and precision problems can be partly absorbed by reranking while recall problems cannot be absorbed at all.

## Generation Metrics

| Metric | What it measures | Target |
|---|---|---|
| Groundedness | Is every claim supported by retrieved context | > ____ |
| Answer correctness | Is the answer right | > ____ |
| Citation accuracy | Do citations point at the content actually used | > ____ |
| Refusal correctness | Does it decline when the corpus cannot support an answer | > ____ |
| Completeness | Does it answer the whole question | > ____ |
| Nugget coverage | Share of the key facts ("nuggets") an SME listed for the question that the answer contains | > ____ |
| Citation support | Share of cited sentences whose cited passage actually supports them (fully, partially, not) | > ____ |

**Nugget coverage and citation support are answer measures used by the public TREC 2024 RAG Track** ([nugget evaluation, arXiv 2411.09607](https://arxiv.org/abs/2411.09607); [support evaluation, arXiv 2504.15205](https://arxiv.org/abs/2504.15205)). Nugget coverage is a practical, measurable form of completeness: an SME writes the few facts a good answer must contain, and the answer is scored on which it includes. Citation support is scored per sentence against the passage cited for it, which is stricter than asking whether the answer as a whole is grounded.

**Reference-free metrics are the practical choice here.** Enterprise programs rarely have a gold-standard answer written for every question, which makes classical reference-based scoring inapplicable by construction. Grounding checks and model-graded scoring with explicit criteria work without one.

Two approaches worth knowing:

- **Question-generation grounding.** Generate questions from the retrieved context, check the answer addresses them. Directly tests whether the answer reflects its sources.
- **Model-graded scoring with explicit criteria.** A judge model scores against a written rubric. Cheap, repeatable, and only as good as the rubric, so the rubric belongs in this document rather than in a prompt somewhere.

Whatever you choose, **validate the judge against human scoring on a sample before trusting it.** An unvalidated automated judge is a number that feels like evidence.

**Calibrate the judge on this program's own corpus and report the agreement.** A published agreement figure is evidence about that study's corpus, task, and judge model, not about yours. For scale: in the TREC 2024 RAG Track support evaluation, human and GPT-4o support labels agreed exactly on 56% of assessments done from scratch, and 72% when humans post-edited the model's labels; the same study found an independent human judge agreed more with GPT-4o than with the first human ([Thakur et al., arXiv 2504.15205](https://arxiv.org/abs/2504.15205)). Those are that study's figures, for one judge on one task. The lesson for a program is that humans also disagree with each other, so the calibration has to measure both: human-human agreement on a sample, and judge-human agreement on the same sample. Record both numbers and the sample size next to every judged metric.

**Treat off-the-shelf faithfulness scores as unvalidated until calibrated.** Popular faithfulness metrics come with thin published validation. RAGAS, for example, was validated on WikiEval, 50 questions built from 50 Wikipedia pages ([Es et al., arXiv 2309.15217](https://arxiv.org/abs/2309.15217)). A score that has not been checked against human labels on your corpus is a trend line at best, not a gate.

## Operational Metrics

| Metric | Target |
|---|---|
| P50 latency | |
| P95 latency | |
| Cost per query | |
| Cost per active user per month | |
| Availability | |
| Cache hit rate | |

## Safety and Security Evals

Run alongside quality evals, not as a separate late-stage activity. Scenarios and corpus: [Prompt Injection Threat Model](https://github.com/ChefPlex/security-program-playbooks/tree/main/enterprise-rag-security).

| Check | Target |
|---|---|
| Unauthorized retrieval events | **0** |
| Direct prompt injection resisted | 100% of known corpus |
| Indirect injection resisted | 100% of known corpus |
| System prompt disclosure | 0 |
| Cross-user data leakage | 0 |

**What 100% of a known corpus means.** Passing every case in a known injection corpus means nothing obvious was found. It does not mean the system is safe. The corpus only contains attacks someone already wrote down, so keep adding new cases from red-team work and incidents, and report the result as "resisted N of N known cases, corpus version X," never as "secure."

## CI Gates

Evals run in continuous integration. A change that regresses a gate does not merge.

| Gate | Blocks on | Runs |
|---|---|---|
| Retrieval regression | Recall@K drops more than ____ | Every PR touching retrieval |
| Generation regression | Groundedness drops more than ____ | Every PR touching prompt or model |
| Security regression | Any injection or permission failure | Every PR, no exceptions |
| Cost regression | Cost per query rises more than ____ | Nightly |
| Full suite | Any gate | Pre-release |

The security gate has no tolerance band on purpose. Retrieval quality is a negotiation, unauthorized retrieval is not.

**Set the thresholds above the noise.** Model output varies from run to run, so a single eval run cannot tell a regression from ordinary variation. Before filling in the blanks above:

- **Run each eval suite N times** (N = ____, at least 3) on an unchanged baseline, and record the spread for each metric.
- **Set each regression threshold larger than that measured spread.** A threshold inside the noise blocks good changes at random and teaches the team to override the gate.
- **Gate on the repeated result**, not on one run: compare the mean of N runs against the baseline, and report the range with it.
- **The judge must differ from the generator** in model family or in method (for example a rule-based check, or human scoring on a sample). A judge that shares the generator's model tends to share its blind spots and will grade its own mistakes as correct.

## Review Cadence

| Activity | Frequency | Owner |
|---|---|---|
| Eval suite run | Every PR plus nightly | AI engineering |
| Eval set expansion from production questions | Monthly | Product plus QA |
| Judge validation against human scoring | Quarterly, and after any judge model or rubric change | AI engineering |
| Held-out set run | At each milestone gate only | QA |
| Failure-point review of production misses | Monthly during pilot, quarterly after | AI engineering plus Product |
| Metric target review | Quarterly | Program |

Production questions the system handled badly are the best source of new eval cases. Build the feedback path at launch, not after the first bad quarter.
