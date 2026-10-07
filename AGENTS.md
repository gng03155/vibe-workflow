# AGENTS.md

AI handoff guide for this project.

## Core Rule

Do not treat the repository as a blank slate.

For non-trivial work, read `.context/README.md` first, then only the relevant context files.

`.context/` is the compressed source of current project knowledge.
It is not a task log, scratchpad, or code dump.

Document only durable information that helps future agents avoid wrong assumptions.

---

## Context Structure

```text
.context/
  README.md
  GLOBAL.md
  DESIGN.md
  DECISIONS.md
  GLOSSARY.md
  TECH_DEBT.md
  domains/
```

---

## Reading Order

Start with `.context/README.md`.

Then route by task type:

```text
Project-wide rules, stack, conventions
→ .context/GLOBAL.md

UI, UX, copy, accessibility, reusable design rules
→ .context/DESIGN.md

Important decisions and rationale
→ .context/DECISIONS.md

Project-specific terms
→ .context/GLOSSARY.md

Known technical debt affecting the task
→ .context/TECH_DEBT.md

Domain-specific business rules and constraints
→ .context/domains/<domain>.md
```

Do not load every context file by default.
Read narrowly to save tokens and reduce noise.

---

## What Belongs in `.context/`

Add or update context only when the information is durable beyond the current task.

Good context:

* Business, product, design, or domain rules
* Permission, security, API, SDK, or platform constraints
* Important trade-offs, gotchas, failed approaches, or decisions
* Unresolved technical debt that affects future work
* Project-specific terminology

Bad context:

* Full source code or large snippets
* Temporary task progress or one-off debugging notes
* Full API dumps, prop lists, or obvious implementation details
* Information easily inferred from code

When unsure, ask:

> Will this help a future AI avoid a likely mistake?

If yes, document it.
If no, leave it out.

---

## Context Diet Rules

Keep context compact.

1. Prefer bullets over long prose.
2. Do not duplicate the same rule across files.
3. Put information in the highest-level appropriate file.
4. Reference other files by path instead of repeating content.
5. Remove stale content when clearly obsolete.
6. Mark uncertain information as `Needs verification`.
7. Keep code snippets rare and tiny.
8. Keep this file under 180 lines when possible.

---

## Automatic Context Maintenance

At the end of every non-trivial task, check whether `.context/` should be updated, even if the user did not ask.

Update `.context/` only when the task changes durable project knowledge.

Check for technical debt introduced, discovered, or resolved during the task. Maintain `.context/TECH_DEBT.md` using the criteria in `.context/README.md`.

Update when work adds, changes, or reveals:

* Business, design, or domain rules
* Permission or security constraints
* Project-wide conventions
* Important product or architecture decisions
* Project-specific terms
* Repeated gotchas or failed approaches
* External API, SDK, or platform constraints

Do not update `.context/` for:

* Small bug fixes
* Simple refactors
* Test-only changes
* Temporary implementation notes
* One-off task progress
* Obvious renames
* Details easily inferred from code

When updating context:

1. Choose the highest-level appropriate file.
2. Keep the update short.
3. Do not duplicate an existing rule.
4. Do not copy large code blocks.
5. Mark uncertain information as `Needs verification`.

If the update is clear and verified, update the relevant context file directly.

If uncertain, policy-sensitive, or conflicting with existing context, do not silently overwrite it. Add `Needs verification` or mention the suggested update in the final response.

End non-trivial work with one short note:

* `Context updated: <path>`
* `Context update not needed: <reason>`
* `Context update suggested: <path/reason>`

---

## External Docs and Local References

If the project depends on external APIs, SDKs, or platform rules, prefer local reference notes or local documentation pointers inside the repository.

Do not rely on memory when official docs or local references exist.

If local external documentation exists, mention it in `.context/GLOBAL.md` or the relevant domain file.

---

## Agent Behavior

Verify important behavior against code, and treat context as stale when it conflicts with code.

End with the required context maintenance note.

---

## Where Detailed Guidance Lives

AGENTS.md should stay short.

Detailed context-file responsibilities, templates, and examples belong in `.context/README.md`.

If a rule becomes too detailed for AGENTS.md, move it there.
