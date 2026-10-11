# Context README

## Reading Map

* Start with [GLOBAL.md](GLOBAL.md) when orienting to the project; then read only files relevant to the task.
* Paths in code below are repository-relative; linked paths are relative to this file.

| Need | Read |
| --- | --- |
| Direction, current state, shared rules | [GLOBAL.md](GLOBAL.md) |
| Shared design rules | [DESIGN.md](DESIGN.md) |
| Domain rules | `.context/domains/<domain>.md`; exact registered paths below |
| Decision rationale or replacement | [DECISIONS.md](DECISIONS.md); follow its Owner links |
| Project terminology | [GLOSSARY.md](GLOSSARY.md); relevant terms only |
| Limitation affecting this task | [TECH_DEBT.md](TECH_DEBT.md); relevant items only |
| Supporting evidence or assets | Reference Map below, or [GLOBAL References](GLOBAL.md#references) |
| Task scope, completion criteria, results | `docs/tasks/YYYY-MM-DD-<slug>.md`, when required |

Domain paths: none registered yet.

## Reference Map

`docs/` is optional; no subfolders exist yet.
Register every created `docs/` subfolder with its exact path and one-line purpose here or in GLOBAL References; keep the map in one location.

## Conditional Reading

| Action | Read |
| --- | --- |
| Resolve rule ownership or conflicting rules | [WRITING.md: Knowledge and Ownership](WRITING.md#knowledge) |
| Update context, a reference map, or a task record | Relevant section of [WRITING.md](WRITING.md) |
| Write or update entries | No entries, including a new file: read its matching template below; existing entries: follow an existing entry's format |
| Plan or review with `/spec-partner` | Optional Claude Code [spec-partner](../.claude/skills/spec-partner/SKILL.md) |

If existing entries do not establish the needed format or allowed status values, read the matching template.

## Templates

Templates are the format source, not current project rules.

| File | Template |
| --- | --- |
| Global context | [_templates/global.md](_templates/global.md) |
| Domain context | [_templates/domain.md](_templates/domain.md) |
| Decision log | [_templates/decisions.md](_templates/decisions.md) |
| Glossary | [_templates/glossary.md](_templates/glossary.md) |
| Task record | [_templates/task.md](_templates/task.md) |
| Technical debt log | [_templates/tech-debt.md](_templates/tech-debt.md) |
| Design context | [_templates/design.md](_templates/design.md) |
| External reference | [_templates/reference.md](_templates/reference.md) |
