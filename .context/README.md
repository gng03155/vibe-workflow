# Context README

This file explains how to read and maintain `.context/`.

`.context/` is the compressed source of current project knowledge.
It exists to help future AI agents and developers understand the project quickly without reading the entire codebase first.

Do not use `.context/` as a task log, scratchpad, or code dump.

---

## Structure

```text
.context/
  README.md
  GLOBAL.md
  DESIGN.md
  DECISIONS.md
  GLOSSARY.md
  TECH_DEBT.md
  domains/
    trading-calculators.md
    toss-webview.md
```

---

## Read Order

Start here when project context is needed.

Read only the files relevant to the task.

```text
Project-wide rules, stack, conventions
→ GLOBAL.md

UI, UX, copy, accessibility, reusable design rules
→ DESIGN.md

Important decisions and rationale
→ DECISIONS.md

Project-specific terms
→ GLOSSARY.md

Known technical debt affecting the task
→ TECH_DEBT.md

Domain-specific business rules and constraints
→ domains/<domain>.md
```

Examples:

```text
Electron shell, storage, commands
→ GLOBAL.md + DECISIONS.md

Toss webview, session, navigation
→ GLOBAL.md + domains/toss-webview.md

UI/copy change
→ GLOBAL.md + DESIGN.md

Calculator behavior or validation
→ GLOBAL.md + domains/trading-calculators.md

Unclear project term
→ GLOSSARY.md
```

---

## File Responsibilities

### `GLOBAL.md`

Use for project-wide context.

Include:

* Tech stack
* Coding conventions
* Testing conventions
* Shared constraints
* Cross-domain rules
* Common implementation principles

Do not include:

* Domain-specific business logic
* UI/UX rules
* Temporary task notes

---

### `DESIGN.md`

Use for durable design-system context.

Follow the DESIGN.md format when practical:
YAML front matter for machine-readable design tokens, followed by Markdown sections for design rationale and usage guidance.

Source of truth:
- https://github.com/google-labs-code/design.md/blob/main/docs/spec.md

Start from the checked-in `.context/DESIGN.md` template.
Replace `Needs verification` only with verified design values.
If token values are incomplete or uncertain, the file may not pass lint yet.

When token values are defined, validate when possible:

```text
npx @google/design.md lint .context/DESIGN.md
```

---

### `DECISIONS.md`

Use for important decisions and rationale.

Include:

* Architectural decisions
* Product policy decisions
* Important trade-offs
* Rejected alternatives
* Consequences of decisions

Recommended format:

```md
## YYYY-MM-DD — Decision title

Status: Active | Deprecated | Replaced

Decision:
- ...

Reason:
- ...

Consequences:
- ...
```

Do not include:

* Trivial implementation choices
* Temporary debugging decisions

---

### `GLOSSARY.md`

Use for project-specific terminology.

Include:

* Terms with special meaning in this project
* Similar terms that may be confused
* Domain vocabulary

Recommended format:

```md
## Term

Definition:
- ...

Notes:
- ...
```

Do not include:

* Generic programming terms
* Obvious words

---

### `TECH_DEBT.md`

Use for unresolved technical debt that future work must account for.

* Record verified limitations, fragile workarounds, or deferred fixes with concrete impact beyond the current task.
* Keep each item short: problem and impact, relevant paths, reason deferred, and resolution direction or trigger.
* Read when the task touches an affected area; do not load it for every task.
* At the end of non-trivial work, add or update relevant items and remove resolved items after verification.
* Exclude speculative improvements, ordinary task TODOs, progress logs, and resolved history.
* Reference durable rules or decision rationale in other context files instead of duplicating them here. Preserve still-relevant knowledge there when removing a resolved item.
* Mark unverified details as `Needs verification`.

Recommended format:

```md
## Short debt title

- Problem / impact: ...
- Relevant paths: ...
- Reason deferred: ...
- Resolution / trigger: ...
```

---

### `domains/*.md`

Use for domain-specific context.

Include:

* Business rules
* Domain lifecycle rules
* Permissions
* Important flows
* External dependencies
* Edge cases
* Gotchas

Recommended format:

```md
# Domain Name

## Purpose

## Core Concepts

## Business Rules

## Permissions

## Important Flows

## Gotchas
```

Do not include:

* Full source code
* Full DB schema dumps
* Task progress
* Rules that belong in GLOBAL.md
* Design rules that belong in DESIGN.md

---

## Update Rules

Update `.context/` only when durable knowledge changes.

Update when work adds, changes, or reveals:

* Business rule
* Design rule
* Domain invariant
* Security or permission constraint
* Project-wide convention
* Meaningful decision
* Project-specific term
* Repeated failure case
* Non-obvious gotcha
* Unresolved technical debt affecting future work, or resolution of a recorded item

Do not update for:

* Small bug fixes
* Simple refactors
* Test-only changes
* Temporary implementation details
* One-off task progress
* Obvious renames

---

## Context Diet Rules

Keep documents compact.

1. Prefer bullets over long prose.
2. Do not duplicate the same rule across files.
3. Put information in the highest-level appropriate file.
4. Reference another file by path instead of repeating content.
5. Remove stale content when clearly obsolete.
6. Mark uncertain information as `Needs verification`.
7. Keep code snippets rare and tiny.
8. Do not turn context into history.

When unsure, ask:

> Will this help a future AI avoid a likely mistake?

If yes, document it.
If no, leave it out.

---

## Adding New Domain Files

Create a new file under `domains/` when a domain has durable rules likely to matter again.

Use lowercase kebab-case names.

Examples:

```text
domains/billing.md
domains/notification.md
domains/workspace.md
```

After adding a domain file, update this README.

---

## Optional Architecture Map

Do not add `architecture.mmd` by default.

Add it later only if the project structure becomes hard to explain with text alone.

Useful signals:

* Multiple major domains interact
* External integrations become important
* Auth, permission, payment, or order flows become complex
* AI agents repeatedly misunderstand module relationships

If added, keep it high-level.
Do not turn it into a full file map.
