## Unified Process phases Orchestrator

## Itialization (do only once at beginning)

**This file must always follow and apply the  content and behaviour in: [abstract-orchestrator](./utils/abstract-orchestrator.md)**

**This file must always follow and apply the  content and behaviour in: [storage, backend](./skills/storage/SKILL.md)**

## Workflow

This workflow is the structured planning layer for iteravive and incremental development in Unified Process methodology.

### Artifact Store Policy

Allready defined at [storage](./skills/storage/SKILL.md)

### Commands
- `/up-init` -> run `up-init`
- `/up-inception <topic>` -> run `up-inception`

### Dependency Graph
```
inception -> elaboration --> construction -> transition
```

### Result Contract
Each phase returns: `status`, `executive_summary`, `artifacts`, `next_recommended`, `risks`.

### Sub-Agent Launch Pattern
ALL sub-agent launch prompts that involve reading, writing, or reviewing code MUST include pre-resolved **compact rules** from the skill registry.

**Orchestrator skill resolution (do once per session):**
1. Read `.copilot/skills/skill-registry.md`
2. Cache the **Compact Rules** section and the **User Skills** trigger table
3. If no registry exists, warn and proceed without project-specific standards

For each sub-agent launch:
1. Match relevant skills by code context and task context
2. Copy matching compact rule blocks into the prompt as `## Project Standards (auto-resolved)`
3. Inject them BEFORE the task-specific instructions

### Sub-Agent Context Protocol

Sub-agents get a fresh context with NO memory. The orchestrator controls context access.

#### UP Phases

Each UP phase has explicit read/write rules based on the dependency graph:

| Phase | Reads artifacts from backend | Writes artifact to backend |
|-------|------------------------------|-----------------|
| `up-inception` | Nothing | Required (`Vision and Business Case`, `Use Case Model`), Optional (`Suplementary specification`,`Glossary`, `Risk List & Risk Management Plan`, `Prototypes and Proof of Concept`, `Iteration Plan`, `Phase Plan & Software Development Plan`) |
| `up-elaboration` | All (if exists) | Required (`Vision and Business Case`, `Use Case Model`,`Glossary`, `Iteration Plan`), Optional (`Suplementary specification`, `Risk List & Risk Management Plan`, `Prototypes and Proof of Concept`, `Phase Plan & Software Development Plan`) |

For UP phases with required dependencies, the sub-agent reads them directly from the backend the orchestrator passes artifact references (file paths ortopic keys), NOT the content itself.

### Recovery Rule

Do whe you need to get context of the previous session:
**apply the  content and behaviour in: [storage, backend](./skills/storage/SKILL.md)**