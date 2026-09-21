---
id: "SDD-000"
name: "sdd-framework-governance"
description: "Enforces taxonomy, template standards, automated scaffolding, and version control rules for the Antigravity SDD framework."
severity: "error"
scope:
  paths:
    - ".agents/**/*"
tags: ["sdd", "governance", "specification"]
---

# Antigravity SDD Governance & Framework Rules

## Mandatory Guidelines

1. **Taxonomy Enforcement:**
   - The system MUST support five distinct declarative artifact types: **Rules**, **Skills**, **Specs**, **Agents**, and **Workflows**.
2. **Template Provision:**
   - The framework MUST maintain standardized Markdown templates with valid YAML Frontmatter for all artifact types under `skills/scaffold-sdd-artifact/res/` (or `res/`).
3. **Automated Scaffolding:**
   - Automated tooling/skills MUST read `res/` templates and generate valid artifacts under `.agents/` matching the project standards.
4. **Version Control:**
   - All declarative artifacts produced inside `.agents/` MUST be versioned in Git.
5. **Runtime Isolation:**
   - Local engine caches and runtime indexes MUST remain inside `.antigravity/` and be excluded from Git versioning via `.gitignore`.

## Anti-Patterns (What NOT to do)

* **DO NOT** create artifact types outside the five defined categories (Rules, Skills, Specs, Agents, Workflows).
* **DO NOT** commit local runtime caches or indexes from `.antigravity/` into Git version control.
* **DO NOT** generate `.agents/` artifacts manually without validating against the templates provided under `res/`.
