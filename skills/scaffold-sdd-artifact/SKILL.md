---
name: scaffold-sdd-artifact
description: Generates new SDD artifacts (Rule, Skill, Spec, Agent, Workflow) by reading templates from res/
---

# Protocol for Scaffolding SDD Artifacts

## Expected Parameters
- **`artifact_type`**: The type of SDD artifact (`rule`, `skill`, `spec`, `agent`, `workflow`).
- **`artifact_name`**: Unique kebab-case name (or uppercase ID for rules).
- **`target_path`**: Destination file path relative to project root.

1. **Locate Template:**
   - Locate Template in `res/<artifact_type>-template.md` relative to this skill folder.
2. **Process Inputs & Fill Schema:**
   - Read template file content.
   - Replace placeholder YAML Frontmatter fields and Markdown titles with user-confirmed parameters.
   - Ensure final file content is written strictly in English.
3. **Write Destination File:**
   - Ensure target directory exists (`rules/`, `skills/<name>/`, `agents/`, etc.).
   - Write processed content to target path.
4. **Verify Compliance:**
   - Validate generated file against `SDD-001`, `SDD-002`, and `SDD-003` guardrails.
