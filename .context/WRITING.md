# Context Writing Rules

Optimize this structure for AI reading and writing: explicit paths, selective reads, fixed formats, canonical terms, and verifiable completion criteria.

## Document Management Terms

These terms describe this documentation contract; put project-specific terminology in GLOSSARY.

| Term | Meaning |
| --- | --- |
| Rule | An agreed ongoing project requirement. |
| Owner | The single context file responsible for a current rule; `Owns:` declares its topics. |
| Decision | An important choice and its rationale, linked to the current rule's owner. |
| Reference | Supporting evidence, assets, or documentation used to understand or verify context. |
| Task | Scoped work with completion criteria and results, separate from ongoing rules. |
| Completion criterion | A repeatable check with a pass condition and evidence for a task outcome. |
| Technical debt | A verified unresolved implementation limitation affecting future work. |

## Knowledge

* Apply the [AGENTS.md core contract](../AGENTS.md#core-contract). Assign each rule one owner; link that owner from other files.
* Define a new project-specific concept in [GLOSSARY.md](GLOSSARY.md) before introducing its term. Reuse that canonical term for the same concept.
* Record agreed intent separately from verified implementation. Label unverified facts `Needs verification`; keep unagreed proposals in a task draft or the conversation.
* Put agreed durable rules in their owner before implementation when known. Add verified constraints discovered during implementation when they become known.
* Correct or label references that conflict with a current project rule; reverify external facts against official evidence.
* Write action instructions. Pair necessary guardrails with the action to take instead. Keep short explanations needed to apply a rule locally; put significant alternatives and trade-offs in DECISIONS.
* Summarize durable knowledge and link evidence; keep progress, full code, and easily inferred fields or defaults in their existing implementation or task record.

## Ownership

* Read the affected file's `Owns:` line before adding a rule. Select the narrowest owner covering its scope.
* GLOBAL owns direction and cross-domain rules; DESIGN owns shared design rules; each domain owns its specific rules and interaction behavior.
* Move a rule when its owner changes; update `Owns:` and references, then remove the former current copy. Resolve conflicting context copies through ownership rather than precedence exceptions.
* Register each real domain's exact path and purpose in the README Reading Map. Templates stay under `_templates/` and are not registered as real domains.

## Fixed Format

Follow the formats in `_templates/` through the [README template map](README.md#templates) and its conditional reading route. Preserve existing entry headings, field labels, and value spelling when updating records.

Preserve DESIGN's YAML format using the [DESIGN.md specification](https://github.com/google-labs-code/design.md/blob/main/docs/spec.md) when changing its structure. Validate filled tokens when possible with `npx @google/design.md lint .context/DESIGN.md`; template values may not pass lint.

Replace template placeholders and examples with agreed or verified content. Keep empty sections distinct from unknown facts.

## Decisions

* Record significant choices future agents should not accidentally reverse in [DECISIONS.md](DECISIONS.md).
* Give each entry a unique stable ID. Summarize the choice and link the current rule's owner instead of reproducing its detailed rules.
* On replacement, retire the old entry and link the two entries in both directions. Distinguish replacement from retirement without a successor using the template's statuses.
* Keep short retired records useful to current judgment; use Git or a labelled reference archive for older detail.
* Preserve task-specific reasoning in its task record; record only durable significant rationale here.

## References

* Apply the README Reference Map registration rule to every docs subfolder, including nested folders. Update paths and purposes when folders are renamed or removed.
* Link folders or their indexes from context; add individual file links when needed for current interpretation. Completed task records can remain discoverable through their registered folder.
* Create folders only for actual references or task records. Suggested roles: `docs/references/` for external notes, `docs/research/` for measurements, `docs/designs/` for assets, and `docs/tasks/` for task records.
* Keep source URLs, applicable versions, and verification dates with external references. Read relevant local notes or official sources to verify facts rather than relying on memory.
* Keep snapshots and human-facing descriptions as references; link the context owner for ongoing rules instead of maintaining an independent specification.
* Review unlinked material for relevance before cleanup; missing individual links alone do not make a file disposable.

## Tasks

* Create `docs/tasks/YYYY-MM-DD-<slug>.md` for work handed to another session or agent, or work needing separate completion criteria. Complete small same-session changes without a task record.
* Use the creation date in the path and update that same record through completion.
* Agree scope, completion criteria, and context links before implementation; keep unresolved questions visible. Add results, verification evidence, reasoning, and user-confirmation needs as work progresses.
* Mark work ready only when scope and completion criteria are agreed and blockers are resolved or excluded. Use the template's statuses to distinguish proposals, active work, and cancellation.
* Cover each agreed scope outcome with at least one criterion with a unique stable ID, repeatable check, explicit pass condition, and evidence.
* Use observable outputs, measurable thresholds, or reproducible inspection steps so an agent can judge the outcome. Replace subjective phrases with those checks.
* Leave untested criteria pending. If evidence is unavailable or external/user judgment is required, record the dependency and treat the criterion as blocked.
* Mark work complete only when all completion criteria pass and the agreed scope has no unresolved completion blocker.
* Promote newly verified durable knowledge to its context owner; link it from the task. Task scope and results remain here rather than becoming another ongoing rule source.

## Technical Debt

* Record verified unresolved limitations with impact beyond the current task in [TECH_DEBT.md](TECH_DEBT.md).
* Keep ordinary task TODOs and user-confirmation items in their task record; treat an improvement idea as debt only after its concrete limitation is verified.
* Mark uncertain details of an established limitation Needs verification.
* Remove an item after its resolution is verified; preserve still-useful rules or rationale in their owner and task results in their record.

## Maintenance

* Update durable rules, constraints, decisions, terms, or verified debt when their knowledge changes. Judge information rather than task size: a small fix can reveal a lasting constraint.
* Record confirmed changes within existing authorization. Keep unresolved policy proposals separate and mark uncertain facts for verification.
* Prefer concise bullets and one example when needed. Keep headings stable and link supporting material rather than repeating it.
* Split topics when owners or typical reading tasks differ. Around 200 lines is a review signal, not a cap that justifies omitting knowledge.
* Use a short domain entry file to link independently read subtopics; register those exact paths so they remain discoverable.
* Keep verified major capabilities and important open validation in GLOBAL Current State; link task or debt details instead of copying progress.
* Keep optional architecture diagrams high-level and linked from the reading map; create one only when relationships need it.
* Verify project facts when adopting placeholders. Match filename case: uppercase core context files, lowercase kebab-case domain and template files.
