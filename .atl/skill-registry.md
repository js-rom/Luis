# Skill Registry

**Delegator use only.** Any agent that launches sub-agents reads this registry to resolve compact rules, then injects them directly into sub-agent prompts. Sub-agents do NOT read this registry or individual SKILL.md files.

See `_shared/skill-resolver.md` for the full resolution protocol.

## User Skills

| Trigger | Skill | Path |
|---------|-------|------|
| - | storage | D:\DEV\luisito\.copilot\skills\storage\SKILL.md |
| crear un proyecto | up-inception | D:\DEV\luisito\.copilot\skills\up-inception\SKILL.md |

## Compact Rules

Pre-digested rules per skill. Delegators copy matching blocks into sub-agent prompts as `## Project Standards (auto-resolved)`.

### storage
- Persist artifacts following the active store policy and conventions.
- If no policy is detected, default to `openspec` mode.
- If policy is `none`, return results inline and recommend enabling persistence.
- Create required filesystem paths only if they do not exist.
- Act as executor only; do not launch sub-agents or delegate tasks.

### up-inception
- Collaborate with the user; propose answers and ask for confirmation or edits.
- Ask at least the four core questions (vision/business case, feasibility, rough cost range, proceed or stop).
- Do just enough investigation to justify the feasibility decision, not full requirements.
- Identify a list of use cases, confirm with the user, and detail only those selected.
- Keep artifacts lightweight and iterative; avoid full-scope specs in this phase.
- Avoid anti-patterns such as defining full requirements, architecture-first sequencing, or missing a vision.

## Project Conventions

| File | Path | Notes |
|------|------|-------|
| copilot-instructions.md | .copilot/copilot-instructions.md | Index - references files below |
| abstract-orchestrator.md | .copilot/skills/utils/abstract-orchestrator.md | Referenced by copilot-instructions.md |
| storage SKILL | .copilot/skills/storage/SKILL.md | Referenced by copilot-instructions.md |
| skill-registry.md | .copilot/skills/skill-registry.md | Referenced by copilot-instructions.md |

Read the convention files listed above for project-specific patterns and rules. All referenced paths have been extracted - no need to read index files to discover more.
