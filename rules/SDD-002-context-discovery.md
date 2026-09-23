---
description: "Establishes guidelines for Lazy Loading, Header-first Indexing, and Explicit Asset Pointers via res/"
---

# SDD Context Discovery and Resource Loading

> **Scope**: Applies to all discovery and context loading activities across `.agents/**/*`, `openspec/**/*`, user inputs via prompts, and explicitly passed target files.

## Mandatory Guidelines
1. **Lazy Loading:** Context MUST NOT be loaded eagerly into the AI model context window. Agents MUST rely on demand-driven context loading.
2. **Header-first Indexing:** The engine indexes primarily YAML Frontmatter and Markdown headers (`#`, `##`) during initial exploration phases.
3. **Explicit Asset Pointers (`res/`):** Supplementary static assets (JSON schemas, OpenAPI specs, diagrams, templates) MUST be stored in local `res/` subdirectories (e.g., `.agents/skills/<skill-name>/res/` or `@openspec/specs/<module>/res/<filename>`).
4. Agents MUST load assets explicitly using `@openspec/specs/<module>/res/<filename>` or local skill `res/<filename>` syntax only when required for active task execution.

## Anti-Patterns (What NOT to do)
* DO NOT embed massive inline JSON schemas, raw payload examples, or full diagrams directly inside `spec.md` or `SKILL.md` body text.
* DO NOT load `res/` directory contents automatically without explicit task references.
