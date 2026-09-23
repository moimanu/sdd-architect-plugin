---
name: orchestrate-sdd-artifact
description: Orchestrates the interactive creation flow for SDD artifacts, mapping 3 User Interaction Stages to 5 Internal Execution Steps.
---

# SDD Artifact Creation Orchestration (`orchestrate-sdd-artifact`)

## Objective
Conduces the interactive process of creating SDD artifacts, ensuring alignment with the user before file generation through a strict 3-Stage Interaction protocol powered by 5 internal execution steps.

## Scope & Responsibilities

### What it DOES:
1. Triggers `agent-sdd-discovery` for subagent context mapping (Step 1).
2. Performs strict lazy loading based on the subagent's Context Plan (Step 2).
3. Formats the initial plan and asks 2–4 open questions (Stage 1 / Step 3).
4. Consolidates user answers into an Executive Summary for validation (Stage 2).
5. Triggers `render-sdd-template` and writes/applies generated artifacts (Stage 3 / Step 4).
6. Runs compliance checks against guardrails `SDD-001`, `SDD-002`, and `SDD-003` (Step 5).

### What it DOES NOT do:
* **DO NOT** contain static templates or local `res/` directories.
* **DO NOT** perform direct string replacement on templates (delegates strictly to `render-sdd-template`).

---

## Interaction vs. Execution Architecture

```text
+-----------------------------------------------------------------------------------+
| STAGE 1: Detailed Planning & Open Questions (User-Facing / Interface)             |
|   Step 1: Discovery (Invoke agent-sdd-discovery)          [Agent Internal]        |
|   Step 2: Context Loading (Strict read of Context Plan)   [Agent Internal]        |
|   Step 3: Plan & Questions (Present plan & 2-4 questions for user)                |
+-----------------------------------------------------------------------------------+
                                         |
                                         v
+-----------------------------------------------------------------------------------+
| STAGE 2: Executive Summary Confirmation (User-Facing / Interface)                 |
|   Consolidate user responses and request final validation                         |
+-----------------------------------------------------------------------------------+
                                         |
                                         v
+-----------------------------------------------------------------------------------+
| STAGE 3: Artifact Generation & Verification (Execution)                           |
|   Step 4: Execute (Invoke render-sdd-template skill & write/apply files)            |
|   Step 5: Verify (Validate against rules SDD-001, SDD-002, and SDD-003)             |
+-----------------------------------------------------------------------------------+
```

---

## Detailed Execution Protocol

### STAGE 1: Detailed Planning & Open Questions (User-Facing)
* **Step 1: Discovery (Internal)**
  - Spawn `agent-sdd-discovery` via `invoke_subagent`.
  - Pass the user's prompt and target directories (`.agents/rules/`, `openspec/specs/`).
* **Step 2: Context Loading (Internal)**
  - Receive the *Context Plan* from `agent-sdd-discovery`.
  - Read ONLY the files explicitly justified in the Context Plan using `view_file`.
* **Step 3: Plan & Questions (User Interaction)**
  - Present proposed paths, frontmatter mapping, and taxonomy interconnections.
  - Formulate 2 to 4 directed open questions for user feedback.

### STAGE 2: Executive Summary Confirmation (User-Facing)
* Process user responses to the questions.
* Present a consolidated executive summary showing final spec paths and confirmed parameters.
* Request final explicit confirmation before proceeding to file generation.

### STAGE 3: Artifact Generation & Verification
* **Step 4: Execute**
  - Invoke `render-sdd-template` to perform template rendering.
  - Write/apply the resulting content to target file paths using appropriate file operations or tool actions supported by the workspace environment.
* **Step 5: Verify**
  - Verify generated output against `SDD-001` (structure & conventions), `SDD-002` (lazy loading & res/ pointers), and `SDD-003` (OpenSpec lifecycle).
