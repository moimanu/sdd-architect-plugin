---
description: "Defines the unified workspace directory structure, integrating .agents/ (behavior) and openspec/ (product specifications)."
---

# SDD Structure and Conventions (Unified OpenSpec + .agents Architecture)

> **Scope**: Applies to the entire workspace directory tree (`.agents/` and `openspec/`).

## 1. Mandatory Directory Structure

The workspace MUST strictly maintain the following separation of responsibilities:

```
/
├── .agents/                                # AGENT INFRASTRUCTURE AND BEHAVIORS
│   ├── skills/<skill-name>/
│   │   ├── SKILL.md                        # Mandatory: Manifest and instructions
│   │   ├── scripts/                        # Optional: Helper scripts
│   │   ├── examples/                       # Optional: Usage examples
│   │   └── res/                            # Optional: Static templates/schemas/references
│   ├── agents/
│   │   ├── <agent-name>.md                 # Single-file format (Supported)
│   │   └── <agent-name>/agent.md           # Directory format (Supported)
│   ├── rules/
│   │   └── <RULE-ID-name>.md               # Persistent code/architecture rules
│   ├── plugins/<plugin-name>/
│   │   ├── plugin.json                     # Plugin manifest (Mandatory)
│   │   ├── mcp_config.json                 # MCP configuration (Optional)
│   │   ├── hooks.json                      # Plugin lifecycle hooks (Optional)
│   │   ├── skills/                         # Plugin skills
│   │   ├── agents/                         # Plugin agents
│   │   └── rules/                          # Plugin rules
│   └── hooks.json                          # Global workspace hooks
│
└── openspec/                               # SDD ARCHITECTURE AND LIFECYCLE (OpenSpec)
    ├── specs/<module>/spec.md              # Living Specifications
    ├── changes/<change-id>/
    │   ├── proposal.md                     # Change rationale and context
    │   └── specs/<module>/spec.md          # Deltas (ADDED / MODIFIED / REMOVED)
    └── archive/YYYY-MM-DD_<change-id>/     # Immutable delivery archive
```

## 2. Naming Conventions and Format

1. **Naming:** All directory and file names MUST use `kebab-case`.
2. **Rule IDs:** Files in `.agents/rules/` MUST start with an uppercase ID prefix (e.g., `SDD-001-structure-and-conventions.md`).
3. **Agent Prefixes and Formats:** Agent definitions in `.agents/agents/` MUST use the `agent-` prefix. Both single-file (`.agents/agents/<name>.md`) and directory-based (`.agents/agents/<name>/agent.md`) formats are explicitly permitted.
4. **Change Subfolder:** Folders in `openspec/changes/` MUST use a descriptive `kebab-case` identifier (e.g., `add-user-authentication`).
5. **Language:** All procedural instructions, internal documentation, and specifications MUST be written in English.

## 3. Anti-Patterns (What NOT to do)

* **DO NOT** mix functional specifications inside `.agents/` — product artifacts belong exclusively in `openspec/`.
* **DO NOT** use the obsolete structure `.agents/workflows/` — use **Skills** (`.agents/skills/`).
* **DO NOT** create arbitrary loose files at the root of `.agents/` or `openspec/` outside the designated directories defined in this specification.
* **DO NOT** modify specifications in `openspec/specs/` directly without going through the proposal flow in `openspec/changes/`.
