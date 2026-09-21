---
id: "SDD-001"
name: "sdd-structure-and-conventions"
description: "Enforces directory structure, kebab-case naming, YAML Frontmatter, and English language across .agents/"
severity: "error"
scope:
  paths:
    - ".agents/**/*"
tags: ["sdd", "governance", "conventions"]
---

# SDD Structure and Conventions

## Mandatory Guidelines
1. All artifacts in `.agents/` MUST be located in their designated subdirectories:
   - Rules: `.agents/rules/<RULE-ID-name>.md`
   - Skills: `.agents/skills/<skill-name>/SKILL.md`
   - Specs: `.agents/specs/<module-name>/SPEC.md`
   - Agents: `.agents/agents/<agent-name>.md`
   - Workflows: `.agents/workflows/<workflow-name>.md`
2. Naming Conventions:
   - File and directory names MUST use `kebab-case`.
   - Rule IDs MUST use uppercase letters and numbers (e.g., `SDD-001`, `ARCH-001`).
   - Agent identifiers MUST start with the prefix `agent-` (e.g., `agent-sdd-architect`).
   - Workflow identifiers MUST start with the prefix `wf-` (e.g., `wf-create-sdd-artifact`).
3. All internal document prose and technical content MUST be written in English.
4. Every file MUST begin with valid YAML Frontmatter conforming strictly to the schema in `SPEC-SDD-FRAMEWORK`.

## Anti-Patterns (What NOT to do)
* DO NOT place arbitrary files at the root of `.agents/` outside designated directories.
* DO NOT use camelCase, PascalCase, or snake_case for file or directory names.
* DO NOT omit YAML Frontmatter or leave required frontmatter fields empty.
* DO NOT write artifact documentation in languages other than English.
