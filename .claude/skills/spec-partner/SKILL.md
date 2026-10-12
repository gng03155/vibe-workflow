---
name: spec-partner
description: Plan or review a change with the user and prepare agreed scope, completion criteria, and a development handoff. Use when the user invokes /spec-partner.
disable-model-invocation: true
---

# Spec Partner

This session is a **planning session**. Its output is an agreed **handoff**: scope, completion criteria, context owner links, and a task record when required. While planning, write only `.context/` and `docs/`; investigate code only after the user confirms your understanding and scope.

Follow [AGENTS.md](../../../AGENTS.md) and the [reading map](../../../.context/README.md). Use the relevant [writing rules](../../../.context/WRITING.md) when changing records.

## Plan And Review

1. **Read context first.** Read [GLOBAL Direction](../../../.context/GLOBAL.md#direction) and the affected context owners through the map before restating the request or asking questions. Do this for every planning task; use the documents to answer questions about documented capabilities.
2. **Restate and wait.** In the first reply, summarize documented current behavior, the requested outcome, and the scope boundary. Distinguish verified state from intended rules; mark undocumented behavior as unverified. Ask only about points the documents do not answer that require a user decision. Request verbs such as "fix", "add", or "change" describe handoff goals. Wait for the user's confirmation before investigating code or editing documents.
3. **Investigate after confirmation.** Read relevant code, configuration, and references to verify assumptions. Report the likely cause and affected paths as findings; keep implementation read-only.
4. **Agree scope.** Preserve confirmed scope and agree completion criteria with the user. Present any scope wider or narrower than the request as a proposal; adopt it only after the user chooses it.
5. **Check task-record criteria.** Read the writing rules' [Tasks criteria](../../../.context/WRITING.md#tasks) before deciding whether a task record is required. Follow the reading map's template-reading condition and keep proposals separate from agreed scope.
6. Write completion criteria that an agent can evaluate through a repeatable check, explicit pass condition, and evidence. Keep user judgments as unresolved dependencies.
7. Update authorized rules in their owner and link from the task when one exists. Record significant decision rationale in DECISIONS.

## Deliver

For a review, return findings and open decisions. For an agreed handoff, return the task path when a record exists, owner links, agreed scope, completion criteria, and a short instruction the user can paste into a development session. Present it as Ready only when the [task readiness criteria](../../../.context/WRITING.md#tasks) are met.

The handoff ends this skill; stop after delivering it. Remain in the planning role until, after receiving the handoff, the user explicitly switches this session to development or delegates implementation, such as "Implement this handoff in this session." Scope confirmation or a generic "go ahead" continues planning.

Use AGENTS.md's maintenance obligations in the development session when implementation reveals new facts.

Invocation format: [Claude Code skill controls](https://code.claude.com/docs/en/skills#control-who-invokes-a-skill).
