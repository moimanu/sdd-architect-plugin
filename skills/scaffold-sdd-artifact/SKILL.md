---
name: scaffold-sdd-artifact
description: Generates new SDD artifacts (Rule, Skill, Spec, Change, Agent, Plugin) by reading templates from res/
---

# Protocol for Scaffolding SDD Artifacts

## Expected Parameters
- **`artifact_type`**: The type of SDD artifact (`rule`, `skill`, `spec`, `change`, `agent`, `plugin`).
- **`artifact_name`**: Unique kebab-case name (or uppercase ID for rules).
- **`target_path`**: Destination file path relative to project root.

1. **Locate Template:**
   - Locate template in `res/<artifact_type>-template.md` (or `.json`) relative to this skill folder.
2. **Process Inputs & Fill Schema:**
   - Read template file content.
   - Replace placeholder YAML Frontmatter fields and Markdown titles with user-confirmed parameters.
   - Ensure final file content is written strictly in English.
3. **Write Destination File:**
   - Ensure target directory exists (`.agents/rules/`, `.agents/skills/<name>/`, `.agents/agents/`, `openspec/specs/<module>/`, `openspec/changes/<change-id>/`, `.agents/plugins/<name>/`, etc.).
   - Write processed content to target path.
4. **Verify Compliance:**
   - Validate generated file against `SDD-001`, `SDD-002`, and `SDD-003` guardrails.
