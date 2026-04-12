# OpenSpec File Convention (shared across all SDD skills)

## Directory Structure

```
openspec/
├── config.yaml              <- Project-specific SDD config
├── artifacts/               <- Source of truth (main specs)
│   └── {domain}/
│       ├── vision.md
│       └── use-cases/
└── iterations/                 <- Active iteration
    ├── archive/             <- Completed changes (YYYY-MM-DD-{iteration}/)
    └── {iteration}/         <- Active iteration folder
        ├── state.yaml       <- DAG state (survives compaction)
        ├── artifacts/       <- from sdd-spec
            └── {domain}/
                ├── vision.md  <- Delta
                └── use-cases/ <- Delta

```

## Artifact File Paths

| Skill | Creates / Reads | Path |
|-------|----------------|------|
| orchestrator | Creates/Updates | `openspec/iterations/{iteration}/state.yaml` |
| storage | Creates | `openspec/config.yaml`, `openspec/artifacts/`, `openspec/iterations/`, `openspec/iterations/archive/` |
| up-inception | Creates (required) | `openspec/iterations/{iteration}/vision.md` |
| up-inception | Creates (required) | `openspec/iterations/{iteration}/use-cases/UC{{#}} {{use-case.name}}.md` |
| up-archive | Moves | `openspec/iterations/{iteration}/` → `openspec/iterations/archive/YYYY-MM-DD-{iteration}/` |
| up-archive | Updates | `openspec/artifacts/{domain}/vision.md` (merges deltas into main specs) |
| up-archive | Updates | `openspec/artifacts/{domain}/use-cases/{{use-case.name}}.md` (merges deltas into main specs) |

## Reading Artifacts

```
vision:   openspec/iterations/{iteration}/artifacts/vision.md
use case:   openspec/iterations/{iteration}/artifacts/UC{{#}} {{use-case.name}}.md
artifacts:      openspec/iterations/{iteration}/artifacts/  (all domain subdirectories)
Config:     openspec/config.yaml
```

## Writing Rules

- Always create the change directory before writing artifacts
- If a file already exists, READ it first and UPDATE it (don't overwrite blindly)
- If the change directory already exists with artifacts, the change is being CONTINUED
- Use `openspec/config.yaml` `rules` section for project-specific constraints per phase

## Config File Reference

```yaml
# openspec/config.yaml
schema: spec-driven

context: |
  Tech stack: {detected}
  Architecture: {detected}
  Testing: {detected}
  Style: {detected}

rules:
  proposal:
    - Include rollback plan for risky changes
  specs:
    - Use Given/When/Then for scenarios
    - Use RFC 2119 keywords (MUST, SHALL, SHOULD, MAY)
  design:
    - Include sequence diagrams for complex flows
    - Document architecture decisions with rationale
  tasks:
    - Group by phase, use hierarchical numbering
    - Keep tasks completable in one session
  apply:
    - Follow existing code patterns
    tdd: false           # Set to true to enable RED-GREEN-REFACTOR
    test_command: ""
  verify:
    test_command: ""
    build_command: ""
    coverage_threshold: 0
  archive:
    - Warn before merging destructive deltas
```

## Archive Structure

When archiving, the change folder moves to:
```
openspec/changes/archive/YYYY-MM-DD-{iteration}/
```

Use today's date in ISO format. The archive is an AUDIT TRAIL — never delete or modify archived changes.
