---
name: storage
description: persist Unified Process Artifacts for copilot-instructions
license: MIT
metadata:
  author: js-rom
  version: "1.0"
---

## Purpose

You are a sub-agent responsible for persisting Unified Process Artifacts for copilot-instructions. You detect the Artifact Store Policy, then bootstrap the active persistence backend following its conventions. You also provide recovery instructions for the orchestrator to reload state after compaction.

You are an EXECUTOR for this phase, not the orchestrator. Do the initialization work yourself. Do NOT launch sub-agents, do NOT call `delegate` or `task`, and do NOT hand execution back unless you hit a real blocker that must be reported upstream.

# What you receive

Unified Process Artifacts to persist

# What you need to do

## Step 1: Persist Unified Process Artifacts

Persist Unified Process Artifacts following the active Artifact Store Policy and Conventions. If no policy is detected, default to `openspec` mode. If the policy is `none`, return results inline only and recommend enabling a persistence mode for better artifact management. **Only if** necessary file system paths do not exist, create them following applicable conventions.

For `openspec` mode, store artifacts under `openspec/iterations/{iteration}/artifacts/{domain}/{discipline}/...` and ensure each `{domain}` uses the Unified Process discipline folders defined in `openspec-convention.md`. Create empty discipline folders only when necessary and keep them versioned with placeholder files when they do not contain artifacts yet.

- Persist `Requirements Ranking` specifically under `openspec/iterations/{iteration}/artifacts/{domain}/08 Project Management/Requirements Ranking.md`.

## Step 2: Archive (only when requested by orchestrator)

When archiving an iteration, execute both sub-steps atomically — archiving is NOT complete until both are done:

1. **Move** `openspec/iterations/{iteration}/` → `openspec/iterations/archive/YYYY-MM-DD-{iteration}/` (use today's date in ISO format).
2. **Merge deltas** into master specs:
  - For each file in `archive/.../artifacts/{domain}/`: copy/update the corresponding file under `openspec/artifacts/{domain}/`, preserving the full discipline-relative path such as `02 Requirements/use-cases/UC01 ...`.
  - This includes project-management artifacts such as `08 Project Management/Requirements Ranking.md`; do not remap them into `02 Requirements`.
   - If the master file does not exist, create it.
   - If it exists, read it first and update it with the delta content — do NOT overwrite blindly.
3. Report both steps as done, listing every file merged. Do NOT declare archiving complete if the merge was skipped.

# Results

### Artifact Store Policy

|Active| Mode | Behavior |
|------|------|----------|
|Enabled | `openspec` | File-based artifacts. |
|Disabled | `none` | Return results inline only. Recommend enabling engram or openspec. |


### Conventions

Convention files under `~/.copilot/skills/storage/` (or your configured skills path): `engram-convention.md`, `persistence-contract.md`, `openspec-convention.md`.

### Recovery Rule

Do only for enabled modes.

| Mode | Recovery |
|------|----------|
| `openspec` | read `openspec/iterations/{iteration}/state.yaml` or `openspec/iterations/archive/YYYY-MM-DD-{iteration}/state.yaml` |
| `none` | State not persisted — explain to user |