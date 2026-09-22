# sdd-architect

A specialist AI plugin for Spec-Driven Development (SDD) architecture, artifact scaffolding, and governance enforcement built for the Antigravity ecosystem and OpenSpec framework.

## Overview

`sdd-architect` acts as an automated architecture assistant designed to enforce strict workspace organization, manage the lifecycle of specifications, and scaffold standardized declarative artifacts for AI-driven development.

The project segregates operational behavior from domain specifications:
* **`.agents/`**: Infrastructure, agents, skills, rules, and workspace hooks.
* **`openspec/`**: Living technical specifications, active change proposals, and historical archives.

---

## Directory Structure

```text
.
├── .agents/                                # Behavior & AI Infrastructure
│   ├── agents/                             # Specialist AI subagents
│   ├── plugins/                            # Extensions & MCP configs
│   ├── rules/                              # Workspace rules and guardrails
│   ├── skills/                             # Executable workflows & templates
│   └── hooks.json                          # Global lifecycle hooks
│
└── openspec/                               # Product Specifications & Lifecycle
    ├── specs/                              # Living specifications (Source of Truth)
    ├── changes/                            # Active proposals and spec deltas
    └── archive/                            # Immutable historical records
```

---

## Core Principles & Governance Rules

The engine is governed by three primary rules:

1. **SDD-001 (Structure & Conventions)**: Enforces folder separation (`.agents/` vs `openspec/`), `kebab-case` naming conventions, uppercase Rule IDs (e.g., `SDD-001`), and English-only documentation.
2. **SDD-002 (Context Discovery)**: Implements lazy loading, header-first indexing, and explicit resource pointers (`res/`) to minimize context window bloat.
3. **SDD-003 (OpenSpec Lifecycle)**: Guarantees feature updates strictly follow the **Explore > Proposal & Deltas > Execute > Verify & Archive** workflow. Living specs inside `openspec/specs/` must never be modified directly without an active proposal in `openspec/changes/`.

---

## Interactive Interaction Flow

When interacting with `agent-sdd-architect` to create or modify artifacts, the system follows a mandatory 3-stage protocol:

1. **Stage 1: Detailed Planning & Open Questions**
   * Analyzes workspace context against schema rules.
   * Presents proposed path structures, frontmatter mapping, and asks 2–4 targeted questions.
2. **Stage 2: Executive Summary Confirmation**
   * Summarizes confirmed choices and parameters based on user input.
   * Requests final confirmation before execution.
3. **Stage 3: Terminal Automation**
   * Generates clean, reproducible shell commands (`mkdir -p`, `cat << 'EOF' > ...`) to write validated files directly into the target directories.

---

## Supported Artifact Types

The system includes scaffolding capabilities for the following artifact types located in `skills/scaffold-sdd-artifact/res/`:

* **Agent**: Definition files for AI agents with mapped tools and skills (`agent-template.md`).
* **Rule**: Architecture guardrails and mandatory constraints (`rule-template.md`).
* **Skill**: Action protocols and command execution steps (`skill-template.md`).
* **Spec**: Module living technical specifications (`spec-template.md`).
* **Change**: Delta proposals detailing requirement changes (`change-template.md`).
* **Plugin**: JSON manifests for plugin integration (`plugin-template.json`).

---

## Quick Start

1. Ensure the `.agents/` and `openspec/` directories exist in your project root.
2. Load the `sdd-architect` plugin into your Antigravity environment.
3. Invoke `agent-sdd-architect` or trigger the `create-sdd-artifact` skill to begin scaffolding new specifications or rules interactively.