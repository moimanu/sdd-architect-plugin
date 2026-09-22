---
description: "Defines the SDD lifecycle phases (Explore > Plan > Execute > Verify) and task archiving standards"
---

# SDD Lifecycle and Task Archiving

> **Scope**: Applies to task execution and specs under `.agents/specs/**`.

## Mandatory Guidelines
1. **Lifecycle Phases:** All feature development and architectural execution MUST follow the 4-phase sequence:
   - **Explore:** Analyze repository state and specifications without code modification.
   - **Plan:** Generate active execution artifacts (`plan.md` and `tasks.md`).
   - **Execute:** Sequentially implement atomic tasks in `tasks.md`, updating task status from `[ ]` to `[x]`.
   - **Verify:** Run validation skills, linters, and tests to verify compliance with active Rules and Specs.
2. **Task Archiving:** Upon completing a task or workflow execution, active artifacts (`plan.md` and `tasks.md`) MUST be moved to `.agents/specs/archive/YYYY-MM-DD_<TASK-ID>-<short-description>/` for historical tracking.

## Anti-Patterns (What NOT to do)
* DO NOT leave stale or completed `plan.md` and `tasks.md` files in active working directories.
* DO NOT skip the `Verify` phase before marking a workflow execution as complete.
