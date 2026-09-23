---
description: "Enforces taxonomy, template standards, automated scaffolding, and version control rules for the Antigravity SDD framework."
---

# Antigravity SDD Governance & Framework Rules

> **Scope**: Applies to all files and directories matching `.agents/**/*` and `openspec/**/*`.

## Mandatory Guidelines

1. **Taxonomy Enforcement:**
   - The system MUST support distinct declarative artifact types: **Rules**, **Skills**, **Agents**, and **Plugins** in `.agents/`, alongside **Living Specs** and **Changes** in `openspec/`.
2. **Template Provision:**
   - The framework MUST maintain standardized templates with valid YAML Frontmatter (or JSON schemas) for all artifact types under `skills/render-sdd-template/res/`.
3. **Automated Scaffolding:**
   - Automated tooling/skills MUST read `res/` templates and generate valid artifacts matching the project standards.
4. **Version Control:**
   - All declarative artifacts produced inside `.agents/` and `openspec/` MUST be versioned in Git.
5. **Runtime Isolation:**
   - Local engine caches and runtime indexes MUST remain inside `.antigravity/` and be excluded from Git versioning via `.gitignore`.

## Anti-Patterns (What NOT to do)

* **DO NOT** create artifact types outside the defined categories or place product specs inside `.agents/`.
* **DO NOT** commit local runtime caches or indexes from `.antigravity/` into Git version control.
* **DO NOT** generate artifacts manually without validating against the templates provided under `res/`.
