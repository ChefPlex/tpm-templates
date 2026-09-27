# Enterprise RAG Program

Running Retrieval-Augmented Generation as a program, not as an AI experiment.

RAG gets treated as an AI engineering project and then fails on data, security, or adoption. It's a platform program that happens to use a retrieval architecture, and the workstreams that sink it are usually the ones nobody staffed.

These are working templates, same as the rest of this repo. Fill them in, argue with them, delete what doesn't apply to your program.

Security workstream: [Enterprise RAG Security](https://github.com/ChefPlex/security-program-playbooks/tree/main/enterprise-rag-security) (trust boundary, controls, prompt-injection threat model, GA sign-off).

Last reviewed: 2026-09-27.

## Start Here

| Document | What It Is |
|---|---|
| [Enterprise RAG Program Playbook](enterprise-rag-program-playbook.md) | The whole program in one place. Phases 0 through 8, seven workstreams, governance, risk tiers, a 24-week shape, and M0 through M7. Read this first. |

## Templates

| Template | What It Is | Used At |
|---|---|---|
| [RAG Program Charter](rag-program-charter-template.md) | The founding document. Extends the general [Program Charter](../program-charter-template.md) with baseline metrics, data scope, autonomy level, and the architecture decisions that need an ADR. | Phase 0 |
| [Use Case Catalog](rag-use-case-catalog-template.md) | Candidate use cases scored on value, data readiness, volume, and wrong-answer tolerance, so sequencing is defensible when four executives each want theirs first. | Phase 0 |
| [Data Source Inventory](rag-data-source-inventory-template.md) | Every source with its owner, sensitivity, access-control model, permission-hygiene status, refresh need, and deletion propagation. The access-control and hygiene columns are the ones that drive the architecture. | Phase 0-2 |
| [Evaluation Plan](rag-evaluation-plan-template.md) | Retrieval and generation measured separately, the eval set composition, and the CI gates that block a regression from merging. | Phase 4 |
| [RAID Starter Register](rag-raid-starter-register.md) | Twenty-four risks (including oversharing, judge drift, and seven RAG engineering failure points), six assumptions, and six dependencies. Pre-seeded so you are not discovering them one at a time. | Phase 0 |
| [Milestone Exit Criteria](rag-milestone-exit-criteria.md) | Exit criteria for M0 through M7, with the most common failure at each gate. | Every milestone |
| [Definition of Done](rag-definition-of-done.md) | Eleven dimensions, each with a named owner, including validation in operation. Agreed before anyone is under launch pressure. | Phase 7 |

## Security

The security workstream lives in the companion repo, because it's a security program in its own right and belongs next to the other security playbooks:

**[Enterprise RAG Security](https://github.com/ChefPlex/security-program-playbooks/tree/main/enterprise-rag-security)**

Trust boundary, permission-aware retrieval, the required control set, and a prompt-injection threat model with a test corpus.

The one rule worth carrying into every architecture conversation on this program:

> The system can never retrieve information the requesting user could not have accessed directly.

## What This Reuses

This folder does not restate the general program-management material. It points at it:

- [Program Charter Template](../program-charter-template.md)
- [Program Phases Playbook](../program-phases-playbook.md)
- [RAID Log Guide](../raid-log-guide.md)
- [ADR Template](../adr-template.md)
- [Communications Plan Template](../communications-plan-template.md)
- [Program Swim Lanes Template](../program-swim-lanes-template.md)

## If You Read Only One Thing

Don't charter this as "implement RAG." Charter it as building a knowledge platform that securely connects authorized data to AI models and returns measurable, grounded answers.

That is not word games. The first framing produces a demo. The second produces something with a business case, a security model, named owners, and a reason to exist after the person who championed it moves on.
