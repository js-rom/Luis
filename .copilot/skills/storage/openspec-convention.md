# OpenSpec File Convention (shared across all SDD skills)

## Directory Structure

```
openspec/
├── config.yaml              <- Project-specific SDD config
├── state.yaml               <- DAG state (survives compaction)
├── schemas/
│   └── default/
│       ├── templates/       <- Default artifacts for Unified Process
│       ├── instructions/    <- Default instructions for creating artifacts
│       └── schema.yaml      <- Default rules for creating artifacts
├── artifacts/               <- Source of truth (main specs)
│   └── {domain}/
│       ├── 01 Business Modeling/
│       │   └── Domain Model.md
│       ├── 02 Requirements/
│       │   ├── vision.md
│       │   ├── supplementary-specification.md
│       │   ├── glosary.md
│       │   ├── domain-rules.md
│       │   ├── Use Case Model.md
│       │   ├── use-cases/
│       │   │   └── UC{{#}} {{use-case.name}}.md
│       │   ├── SSDs/
│       │   │   └── SSD UC{{#}} {{use-case.name}}.md
│       │   └── Operation Contracts/
│       │       └── Contract CO{#} UC{{#}} {{use-case.name}}.md
│       ├── 03 Design/
│       │   ├── Design Model.md
│       │   ├── SW Architecture Document.md
│       │   ├── Data Model.md
│       │   └── Use Case Realization/
│       │       └── UCR UC{{#}} {{use-case.name}}.md
│       ├── 04 Implementation/
│       │   └── .gitkeep
│       ├── 05 Test/
│       │   └── {{#}} {Iteration} Test plan.md
│       ├── 06 Deployment/
│       │   └── .gitkeep
│       ├── 07 Configuration & CM/
│       │   └── .gitkeep
│       ├── 08 Project Management/
│       │   ├── {{#}} {Iteration} Plan.md
│       │   └── Requirements Ranking.md
│       └── 09 Enviroment/
│           └── .gitkeep
```

## Discipline Directories

| Directory | Purpose | Current artifact allocation |
|-----------|---------|----------------------------|
| `01 Business Modeling` | Domain-level business concepts and relationships | `Domain Model.md` |
| `02 Requirements` | Vision, use cases, supplementary requirements, glossary, and domain rules | `vision.md`, `supplementary-specification.md`, `glosary.md`, `domain-rules.md`, `Use Case Model.md`, `use-cases/`, `SSDs/SSD UC{{#}} {{use-case.name}}.md`, `Operation Contracts/Contract CO{#} UC{{#}} {{use-case.name}}.md` |
| `03 Design` | Logical design and architecture artifacts | `Design Model.md`, `SW Architecture Document.md`, `Data Model.md`, `Use Case Realization/UCR UC{{#}} {{use-case.name}}.md` |
| `04 Implementation` | Implementation-level artifacts | Reserved |
| `05 Test` | Test artifacts | `Test plan.md` |
| `06 Deployment` | Deployment artifacts | Reserved |
| `07 Configuration & CM` | Configuration and change-management artifacts | Reserved |
| `08 Project Management` | Project planning and tracking artifacts | `Requirements Ranking.md`, `Iteration Plan` |
| `09 Enviroment` | Environment setup and support artifacts | Reserved |

## Artifact File Paths

| Skill | Creates / Reads | Path |
|-------|----------------|------|
| orchestrator | Creates/Updates | `openspec/state.yaml` |
| storage | Creates (required) | `openspec/config.yaml`, `openspec/state.yaml`, `openspec/artifacts/`, `openspec/schemas/default/templates/`, `openspec/schemas/default/instructions/` |
| storage | Creates (required) | `openspec/artifacts/{domain}/01 Business Modeling/Domain Model.md` |
| storage | Creates (required) | `openspec/artifacts/{domain}/02 Requirements/vision.md` |
| storage | Creates (required) | `openspec/artifacts/{domain}/02 Requirements/supplementary-specification.md` |
| storage | Creates (required) | `openspec/artifacts/{domain}/02 Requirements/glosary.md` |
| storage | Creates (required) | `openspec/artifacts/{domain}/02 Requirements/domain-rules.md` |
| storage | Creates (required) | `openspec/artifacts/{domain}/02 Requirements/Use Case Model.md` |
| storage | Creates (required) | `openspec/artifacts/{domain}/02 Requirements/use-cases/UC{{#}} {{use-case.name}}.md` |
| storage | Creates (required) | `openspec/artifacts/{domain}/02 Requirements/SSDs/SSD UC{{#}} {{use-case.name}}.md` |
| storage | Creates (required) | `openspec/artifacts/{domain}/02 Requirements/Operation Contracts/Contract CO{#} UC{{#}} {{use-case.name}}.md` |
| storage | Creates (required) | `openspec/artifacts/{domain}/03 Design/Design Model.md` |
| storage | Creates (required) | `openspec/artifacts/{domain}/03 Design/SW Architecture Document.md` |
| storage | Creates (required) | `openspec/artifacts/{domain}/03 Design/Data Model.md` |
| storage | Creates (required) | `openspec/artifacts/{domain}/03 Design/Use Case Realization/UCR UC{{#}} {{use-case.name}}.md` |
| storage | Creates (required) | `openspec/artifacts/{domain}/05 Test/{{#}} {Iteration} Test plan.md` |
| storage | Creates (required) | `openspec/artifacts/{domain}/08 Project Management/Requirements Ranking.md`, `openspec/artifacts/{domain}/08 Project Management/{{#}} {Iteration} Plan.md` |
| storage | Updates | `openspec/artifacts/{domain}/{discipline}/...` (direct master update; no archive merge) |

## Default artifacts

- Use `openspec/schemas/default` as templates and rules for all artifacts you create or update.

## Reading Artifacts

```
vision: openspec/artifacts/{domain}/02 Requirements/vision.md
supplementary specification: openspec/artifacts/{domain}/02 Requirements/supplementary-specification.md
glosary: openspec/artifacts/{domain}/02 Requirements/glosary.md
domain rules: openspec/artifacts/{domain}/02 Requirements/domain-rules.md
use case model: openspec/artifacts/{domain}/02 Requirements/Use Case Model.md
use case: openspec/artifacts/{domain}/02 Requirements/use-cases/UC{{#}} {{use-case.name}}.md
system sequence diagram: openspec/artifacts/{domain}/02 Requirements/SSDs/SSD UC{{#}} {{use-case.name}}.md
operation contracts: openspec/artifacts/{domain}/02 Requirements/Operation Contracts/Contract CO{#} UC{{#}} {{use-case.name}}.md
domain model: openspec/artifacts/{domain}/01 Business Modeling/Domain Model.md
design model: openspec/artifacts/{domain}/03 Design/Design Model.md
SW architecture document: openspec/artifacts/{domain}/03 Design/SW Architecture Document.md
data model: openspec/artifacts/{domain}/03 Design/Data Model.md
use case realization: openspec/artifacts/{domain}/03 Design/Use Case Realization/UCR UC{{#}} {{use-case.name}}.md
requirements-ranking: openspec/artifacts/{domain}/08 Project Management/Requirements Ranking.md
Iteration Plan: openspec/artifacts/{domain}/08 Project Management/{{#}} {Iteration} Plan.md
test plan: openspec/artifacts/{domain}/05 Test/{{#}} {Iteration} Test plan.md
artifacts: openspec/artifacts/{domain}/  (all discipline subdirectories)
config: openspec/config.yaml
```

## Writing Rules

- Always write directly to `openspec/artifacts/{domain}/...`.
- If a file already exists, READ it first and UPDATE it (do not overwrite blindly).
- Do NOT create or use `openspec/iterations/` folders for artifact persistence.
- Within each `{domain}`, always place artifacts in the correct Unified Process discipline directory.
- Create all nine discipline directories for each `{domain}`. If a discipline has no artifact yet, keep the directory versioned with a placeholder such as `.gitkeep`.
- Use `openspec/config.yaml` `rules` section for project-specific constraints per phase.

## Archive Policy (Master-Only)

- Do NOT create or move `openspec/iterations/{iteration}/` folders.
- Do NOT run archive or delta-merge operations.
- Use version control history (for example, Git commits) as the audit trail for specification changes.
