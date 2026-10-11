# AGENTS.md

AI handoff guide for this project.

## Core Contract

* `.context/` is the source of agreed current project rules.
* `docs/` holds reference material; follow context owners for current rules.
* `docs/tasks/` holds scoped task records.
* When code differs from context, check whether knowledge is stale or implementation diverges from agreed intent before changing either.

## Start Here

* Work from existing project context.
* For non-trivial work, read `.context/README.md` first and follow its reading map and conditional writing routes.
* Use the canonical terms in `.context/GLOSSARY.md`; consult relevant entries when a term is unclear or new.
* Keep this entry point under 180 lines when practical.

## Verify Before Changing Knowledge

* Verify important implementation claims against code, configuration, and relevant local references or official documentation.
* Preserve existing authorization. Resolve an undecided or conflicting policy before replacing it; use `.context/WRITING.md` for recording uncertain facts.

## Finish Non-Trivial Work

* Check whether the task added, changed, or revealed durable project knowledge; update its owner using the relevant `.context/WRITING.md` criteria.
* Check technical debt introduced, discovered, or resolved; maintain `.context/TECH_DEBT.md` using its writing criteria.
* End with one short context-maintenance note:

```text
Context updated: <path>
Context update not needed: <reason>
Context update suggested: <path/reason>
```
