---
description: "Establishes guidelines for Lazy Loading, Header-first Indexing, and Explicit Asset Pointers via res/"
---

# SDD Context Discovery and Resource Loading

> **Scope**: Applies to files under `.agents/specs/**` and `.agents/skills/**`.

## Mandatory Guidelines
1. **Lazy Loading:** Context MUST NOT be loaded eagerly into the AI model context window. Agents MUST rely on demand-driven context loading.
2. **Header-first Indexing:** The engine indexes primarily YAML Frontmatter and Markdown headers (`#`, `##`) during initial exploration phases.
3. **Explicit Asset Pointers (`res/`):** Supplementary static assets (JSON schemas, OpenAPI specs, diagrams, templates) MUST be stored in local `res/` subdirectories.
4. Agents MUST load assets explicitly using `@res/<filename>` or `@specs/<module>/res/<filename>` syntax only when required for active task execution.

## Anti-Patterns (What NOT to do)
* DO NOT embed massive inline JSON schemas, raw payload examples, or full diagrams directly inside `SPEC.md` or `SKILL.md` body text.
* DO NOT load `res/` directory contents automatically without explicit task references.
