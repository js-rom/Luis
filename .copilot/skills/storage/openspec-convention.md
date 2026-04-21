# OpenSpec File Convention (shared across all SDD skills)

## Directory Structure

```
openspec/
├── config.yaml              <- Project-specific SDD config
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
│       │   └── SSDs/
│       │       └── SSD UC{{#}} {{use-case.name}}.md
│       ├── 03 Design/
│       │   ├── Design Model.md
│       │   ├── SW Architecture Document.md
│       │   ├── Data Model.md
│       ├── 04 Implementation/
│       │   └── .gitkeep
│       ├── 05 Test/
│       │   └── .gitkeep
│       ├── 06 Deployment/
│       │   └── .gitkeep
│       ├── 07 Configuration & CM/
│       │   └── .gitkeep
│       ├── 08 Project Management/
│       │   ├── use-cases/
│       │   │   └── {iteration} Plan.md
│       │   └── Requirements Ranking.md
│       └── 09 Enviroment/
│           └── .gitkeep
└── iterations/              <- Active and archived iteration deltas
    ├── archive/
    │   └── YYYY-MM-DD-{iteration}/
    │       ├── state.yaml
    │       └── artifacts/
    │           └── {domain}/
    │               └── ...same discipline layout as master artifacts...
    └── {iteration}/
        ├── state.yaml       <- DAG state (survives compaction)
        └── artifacts/
            └── {domain}/
                └── ...same discipline layout as master artifacts...
```

## Discipline Directories

| Directory | Purpose | Current artifact allocation |
|-----------|---------|----------------------------|
| `01 Business Modeling` | Domain-level business concepts and relationships | `Domain Model.md` |
| `02 Requirements` | Vision, use cases, supplementary requirements, glossary, and domain rules | `vision.md`, `supplementary-specification.md`, `glosary.md`, `domain-rules.md`, `Use Case Model.md`, `use-cases/`, `SSDs/SSD UC{{#}} {{use-case.name}}.md` |
| `03 Design` | Logical design and architecture artifacts | `Design Model.md`, `SW Architecture Document.md`, `Data Model.md` |
| `04 Implementation` | Implementation-level artifacts | Reserved |
| `05 Test` | Test artifacts | Reserved |
| `06 Deployment` | Deployment artifacts | Reserved |
| `07 Configuration & CM` | Configuration and change-management artifacts | Reserved |
| `08 Project Management` | Project planning and tracking artifacts | `Requirements Ranking.md`, `Iteration Plan` |
| `09 Enviroment` | Environment setup and support artifacts | Reserved |

## Artifact File Paths

| Skill | Creates / Reads | Path |
|-------|----------------|------|
| orchestrator | Creates/Updates | `openspec/iterations/{iteration}/state.yaml` |
| storage | Creates (required) | `openspec/config.yaml`, `openspec/artifacts/`, `openspec/iterations/`, `openspec/iterations/archive/`, `openspec/schemas/default/templates/`, `openspec/schemas/default/instructions/` |
| storage | Creates (required) | `openspec/iterations/{iteration}/artifacts/{domain}/01 Business Modeling/Domain Model.md` |
| storage | Creates (required) | `openspec/iterations/{iteration}/artifacts/{domain}/02 Requirements/vision.md` |
| storage | Creates (required) | `openspec/iterations/{iteration}/artifacts/{domain}/02 Requirements/supplementary-specification.md` |
| storage | Creates (required) | `openspec/iterations/{iteration}/artifacts/{domain}/02 Requirements/glosary.md` |
| storage | Creates (required) | `openspec/iterations/{iteration}/artifacts/{domain}/02 Requirements/domain-rules.md` |
| storage | Creates (required) | `openspec/iterations/{iteration}/artifacts/{domain}/02 Requirements/Use Case Model.md` |
| storage | Creates (required) | `openspec/iterations/{iteration}/artifacts/{domain}/02 Requirements/use-cases/UC{{#}} {{use-case.name}}.md` |
| storage | Creates (required) | `openspec/iterations/{iteration}/artifacts/{domain}/02 Requirements/SSDs/SSD UC{{#}} {{use-case.name}}.md` |
| storage | Creates (required) | `openspec/iterations/{iteration}/artifacts/{domain}/03 Design/Design Model.md` |
| storage | Creates (required) | `openspec/iterations/{iteration}/artifacts/{domain}/03 Design/SW Architecture Document.md` |
| storage | Creates (required) | `openspec/iterations/{iteration}/artifacts/{domain}/03 Design/Data Model.md` |
| storage | Creates (required) | `openspec/iterations/{iteration}/artifacts/{domain}/08 Project Management/Requirements Ranking.md`, `openspec/iterations/{iteration}/artifacts/{domain}/08 Project Management/Iteration Plan.md` |
| storage | Moves | `openspec/iterations/{iteration}/` → `openspec/iterations/archive/YYYY-MM-DD-{iteration}/` |
| storage | Updates | `openspec/artifacts/{domain}/{discipline}/...` (merges deltas into main specs while preserving the discipline-relative path) |

## Default artifacts

- Use `openspec/schemas/default` as templates and rules for all artifacts you create or update.

## Reading Artifacts

```
vision: openspec/iterations/{iteration}/artifacts/{domain}/02 Requirements/vision.md
supplementary specification: openspec/iterations/{iteration}/artifacts/{domain}/02 Requirements/supplementary-specification.md
glosary: openspec/iterations/{iteration}/artifacts/{domain}/02 Requirements/glosary.md
domain rules: openspec/iterations/{iteration}/artifacts/{domain}/02 Requirements/domain-rules.md
use case model: openspec/iterations/{iteration}/artifacts/{domain}/02 Requirements/Use Case Model.md
use case: openspec/iterations/{iteration}/artifacts/{domain}/02 Requirements/use-cases/UC{{#}} {{use-case.name}}.md
system sequence diagram: openspec/iterations/{iteration}/artifacts/{domain}/02 Requirements/SSDs/SSD UC{{#}} {{use-case.name}}.md
domain model: openspec/iterations/{iteration}/artifacts/{domain}/01 Business Modeling/Domain Model.md
design model: openspec/iterations/{iteration}/artifacts/{domain}/03 Design/Design Model.md
SW architecture document: openspec/iterations/{iteration}/artifacts/{domain}/03 Design/SW Architecture Document.md
data model: openspec/iterations/{iteration}/artifacts/{domain}/03 Design/Data Model.md
requirements-ranking: openspec/iterations/{iteration}/artifacts/{domain}/08 Project Management/Requirements Ranking.md
Iteration Plan: openspec/iterations/{iteration}/artifacts/{domain}/08 Project Management/Iteration Plan.md
artifacts: openspec/iterations/{iteration}/artifacts/{domain}/  (all discipline subdirectories)
config: openspec/config.yaml
```

## Writing Rules

- Always create the iteration directory before writing artifacts.
- If a file already exists, READ it first and UPDATE it (do not overwrite blindly).
- If the iteration directory already exists with artifacts, the iteration is being CONTINUED.
- Within each `{domain}`, always place artifacts in the correct Unified Process discipline directory.
- Create all nine discipline directories for each `{domain}`. If a discipline has no artifact yet, keep the directory versioned with a placeholder such as `.gitkeep`.
- Use `openspec/config.yaml` `rules` section for project-specific constraints per phase.

## Archive Structure

When archiving, the iteration folder moves to:

```
openspec/iterations/archive/YYYY-MM-DD-{iteration}/
```

Then merge each archived delta into the matching master path under:

```
openspec/artifacts/{domain}/
```

The merge must preserve the full discipline-relative path. Example:

```
openspec/iterations/archive/YYYY-MM-DD-{iteration}/artifacts/registro-horario/02 Requirements/Use Case Model.md
→ openspec/artifacts/registro-horario/02 Requirements/Use Case Model.md
```

Use today's date in ISO format. The archive is an AUDIT TRAIL — never delete or modify archived changes.
