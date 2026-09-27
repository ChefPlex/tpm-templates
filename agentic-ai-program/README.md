# Agentic AI Program

The control register for a program that puts AI agents to work - models that call tools, change records and send things, not only answer questions.

An agent program usually fails in one of two ways. Nobody can say which agents exist and what they are allowed to touch, or a guardrail everyone trusts turns out never to have seen the action that went wrong. This template is one page per program that makes both visible. Fill it in before the first agent gets write access, and review it whenever an agent gains a tool.

Companion: the [Enterprise RAG Program](../enterprise-rag-program/) for retrieval work, and the [Prompt Injection Threat Model](https://github.com/ChefPlex/security-program-playbooks/tree/main/enterprise-rag-security) for the attack side.

---

## 1. Agent Inventory

Every agent in production or pilot, including the ones a team built on its own. An agent with no row here is an agent nobody governs.

| Agent | What it does | Tools it can call | Permissions (read / write / send / delete) | Data it can reach | Named human owner | Status (pilot / live / retired) |
|:---|:---|:---|:---|:---|:---|:---|
| | | | | | | |

**The owner is a person, not a team.** If the agent does something wrong at 2 a.m., this is who gets the call.

## 2. Tool-Permission Map

One row per tool, so you can read it from the other direction: which agents can do this?

| Tool or integration | Actions it allows | Agents with access | Scope limit (which records, accounts, repos) | Reversible? | Needs human release? |
|:---|:---|:---|:---|:---|:---|
| | | | | | |

Give each agent only the tools its job needs. A tool granted "in case" is the one that shows up in the incident review.

## 3. Go / No-Go on Irreversible and Outbound Actions

| Action class | Examples | Who holds go / no-go (named) | How the release is recorded |
|:---|:---|:---|:---|
| Irreversible | Delete data, drop tables, revoke access, pay | | |
| Outbound | Send mail or messages, publish, post to a customer | | |
| Privileged | Change permissions, rotate credentials, deploy | | |

The agent can prepare the action. A named person releases it. Keep this list short, so that each request is rare enough to get read - a gate that asks fifty times a day gets approved without reading.

## 4. Guardrail Coverage

The table that finds the gap before an incident does. One row per guardrail.

| Guardrail | Actions it matches | Actions it cannot see | How we would know it failed |
|:---|:---|:---|:---|
| | | | |

- **The third column is the one that gets left blank.** A filter on shell commands does not see the same deletion made through an API tool. A write guard on files does not see a write made through a script.
- **The fourth column needs a reader.** Name the log, report or check that would show the failure, and who reads it. A guardrail whose output nobody reads is not a control.
- **Test each guardrail on known-bad actions** and record the catch rate and the false-positive rate, not only how often it fires.

## 5. Review

| Activity | Trigger | Owner |
|:---|:---|:---|
| Inventory and permission map review | An agent gains a tool or a scope, and quarterly | |
| Guardrail coverage re-test on known-bad actions | A guardrail changes, and quarterly | |
| Exception log review (go / no-go overrides) | Monthly | |

A run of exceptions is the signal that a gate is miscalibrated. Redesign it rather than waiving it again.

---

*Part of the [tpm-templates](https://github.com/ChefPlex/tpm-templates) repo. The reasoning is in [Lessons from Putting AI Into a Company](https://github.com/ChefPlex/learning-notes/blob/main/lessons-from-putting-ai-into-a-company.md), lesson 8.*
