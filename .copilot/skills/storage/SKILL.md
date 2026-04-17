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

Persist Unified Process Artifacts following the actives Artifact Store Policy and Conventions. If no policy is detected, default to `openspec` mode. If the policy is `none`, return results inline only and recommend enabling a persistence mode for better artifact management. **Only if** necessary file system paths do not exist, create them following applicable conventions. 

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
| `openspec` | read `openspec/changes/*/state.yaml` |
| `none` | State not persisted — explain to user |