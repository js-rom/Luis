# Skill Registry

**Delegator use only.** Any agent that launches sub-agents reads this registry to resolve compact rules, then injects them directly into sub-agent prompts. Sub-agents do NOT read this registry or individual SKILL.md files.

See `_shared/skill-resolver.md` for the full resolution protocol.

## User Skills

| Trigger | Skill | Path |
|---------|-------|------|
| — | storage | C:\Users\Jesús\.copilot\skills\storage\SKILL.md |
| — | up-inception | C:\Users\Jesús\.copilot\skills\up-inception\SKILL.md |

## Compact Rules

Pre-digested rules per skill. Delegators copy matching blocks into sub-agent prompts as `## Project Standards (auto-resolved)`.

### storage
- Detect the active Artifact Store Policy before persisting anything.
- Default to `openspec` when no policy is detected.
- If policy is `none`, return results inline and recommend enabling persistence.
- Persist Unified Process artifacts using the active policy conventions.
- Create required filesystem paths only when they do not exist.
- Do not launch sub-agents or delegate tasks.
- Provide recovery instructions for reloading state after compaction.

### up-inception
- Collaborate with the user to establish vision, business case, and scope.
- Propose answers first and ask for confirmation or edits.
- Identify use cases, then ask which ones to detail and refine them.
- Focus on feasibility and rationale; avoid exhaustive requirements or precise estimates.
- Treat inception artifacts as optional and lightweight.
- Avoid defining architecture or full requirements at this phase.
- Immediately invoke `storage` to persist created artifacts.

## Project Conventions

| File | Path | Notes |
|------|------|-------|
| — | — | No project conventions found |

Read the convention files listed above for project-specific patterns and rules. All referenced paths have been extracted — no need to read index files to discover more.
