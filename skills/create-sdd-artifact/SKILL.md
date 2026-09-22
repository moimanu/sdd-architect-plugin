---
name: create-sdd-artifact
description: Orchestrates the interactive 3-stage process (Explore > Plan > Execute > Verify) for scaffolding SDD artifacts
---

# SDD Artifact Creation Execution Workflow

This skill orchestrates the interactive 3-stage process for scaffolding new Rules, Skills, Specs, Changes, Agents, or Plugins within the workspace.

## Context Parameters
- **`artifact_type`**: The type of SDD artifact to generate (`rule`, `skill`, `spec`, `change`, `agent`, `plugin`).

## Execution Steps
1. **Explore:** `agent-sdd-architect` scans workspace to detect existing artifacts and avoid conflicts.
2. **Plan:** `agent-sdd-architect` interviews the user (Stage 1), proposes file architecture, and collects parameters.
3. **Execute:** Upon user confirmation (Stage 2), `agent-sdd-architect` invokes `scaffold-sdd-artifact` skill to generate terminal commands (Stage 3) and create files.
4. **Verify:** `agent-sdd-architect` checks generated files against `SDD-001`, `SDD-002`, and `SDD-003` guardrails.
