# RAG Use Case Catalog Template

A running catalog of candidate use cases, scored so the program can say no with a reason. Owned by the Product Manager and the TPM.

The purpose is not to collect ideas. It is to make the sequencing defensible when four executives each want theirs first.

## Scoring

Score each candidate 1 to 5 on the first four columns. Data readiness is usually the one that decides the order, and it is usually the one nobody scores honestly.

| Dimension | 1 | 5 |
|---|---|---|
| Business value | Nice to have | Named cost or revenue impact |
| Data readiness | Sources scattered, ownership unclear, permissions undocumented | Single authoritative source, owned, permissions modeled |
| User volume | A handful of people, occasionally | Large population, daily |
| Wrong-answer tolerance | Wrong answer causes real harm | Wrong answer is an inconvenience |

**Sequencing rule:** first use case should score high on data readiness and high on wrong-answer tolerance, even at the cost of business value. The first one exists to prove the platform, not to win the quarter. Programs that lead with their highest-value, highest-risk use case tend to spend months in security review with nothing shipped.

## Catalog

| ID | Use case | Users | Sources | Value | Data | Volume | Tolerance | Risk tier | Question shape | Candidate approach | Phase | Status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| UC-01 | | | | | | | | | | | | |
| UC-02 | | | | | | | | | | | | |
| UC-03 | | | | | | | | | | | | |

Status: proposed, accepted, deferred, rejected. A rejected row keeps its reason.

## Approach Routing

No single retrieval approach wins across every kind of question, so record the question shape per use case and treat the approach as a hypothesis the eval set tests, not a platform-wide default.

| Question shape | Candidate approach | Evidence |
|---|---|---|
| Single-hop fact lookup, detail questions ("what is the retention period for X") | Plain RAG | Han et al. found RAG excels on "detailed single-hop queries" ([arXiv 2502.11371](https://arxiv.org/abs/2502.11371)) |
| Multi-hop reasoning across entities ("which teams own services that depend on X") | Consider GraphRAG | Same study: GraphRAG methods are "more effective on reasoning-intensive, multi-hop queries." The authors describe the two as complementary rather than one dominating, and report that selecting or combining them by query gave consistent gains |
| A small, bounded set of long documents that fits in the model's context window | Consider long context, compared against RAG on your own questions | LaRA (ICML 2025, 2,326 test cases, 11 models) found the better choice "depends on a complex interplay of model capabilities, context length, task type, and retrieval characteristics" ([PMLR](https://proceedings.mlr.press/v267/li25dv.html)) |
| Large, changing, or permission-mixed corpus | RAG, with permission-aware retrieval | A design consequence rather than a benchmark result: the corpus cannot fit in one context, and the retrieval step is where per-document permissions and freshness are enforced |

This is qualitative guidance. Cost and latency differ by approach and are not compared here; measure them on your own workload before committing. Adding a second approach adds a second pipeline to evaluate, secure, and operate, so it needs a use case that the first approach measurably fails.

## Per Use Case Detail

Copy this block per accepted use case.

### UC-__ : _______________

**The question users are actually asking.** Write real examples, in their words, gathered from real people. Invented example questions produce eval sets that pass while the system fails.

```text
1.
2.
3.
4.
5.
```

**Authoritative source of truth today:** _______________

**Who owns that source:** _______________

**What happens when the answer is wrong:** _______________

**What "good" looks like to the user:** _______________

**Can the system act, or only answer:** _______________

**Question shape and candidate approach:** _______________ (single-hop, multi-hop, long bounded document, mixed; see Approach Routing)

**Deferred because:** _______________ (for deferred rows only)

## Anti-Patterns

Reject or defer candidates matching these, and record which one applied:

- **No authoritative source.** If humans disagree about the right answer, retrieval cannot fix it. This is a content-governance problem wearing an AI costume.
- **The source is a person.** If the knowledge lives in someone's head, the program is a documentation program first.
- **Permission model undocumented.** Cannot be made permission-aware, so cannot be shipped safely.
- **Answer changes hourly.** Freshness cost will exceed the value.
- **Nobody owns the content.** Post-launch answer quality will decay with no one accountable.
