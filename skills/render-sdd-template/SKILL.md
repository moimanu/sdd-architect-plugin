---
name: render-sdd-template
description: Pure deterministic utility skill for rendering SDD template files from local res/ with parameter substitution and Frontmatter formatting.
---

# SDD Template Rendering Protocol (`render-sdd-template`)

## Objective
Pure utility function for deterministic file generation from static templates. Performs parameter substitution and YAML Frontmatter updates without user interaction or subagent invocation.

## Scope & Operational Responsibilities

### What it DOES:
1. **Locate Template:** Reads the template corresponding to `artifact_type` from the local `res/` directory (`res/<artifact_type>-template.md` or `.json`).
2. **Variable Substitution & Formatting:** Replaces placeholders in YAML Frontmatter and Markdown content using provided input parameters.
3. **Deterministic Output:** Formats and writes the resulting content directly to the target destination path (`target_path`).

### What it DOES NOT do:
* **DO NOT** ask questions to the user or request feedback.
* **DO NOT** invoke subagents (such as `agent-sdd-discovery`).
* **DO NOT** make decisions regarding interaction workflow or stage transitions.

---

## Expected Parameters
- **`artifact_type`**: The type of SDD artifact (`rule`, `skill`, `spec`, `change`, `agent`, `plugin`).
- **`artifact_name`**: Unique kebab-case name (or uppercase ID for rules).
- **`target_path`**: Destination file path relative to project root.
- **`params`**: Key-value map of template variable replacements (e.g., description, tools, skills, dependencies).

---

## Execution Steps

1. **Locate Template:**
   - Find template file in `res/<artifact_type>-template.md` (or `.json`) relative to this skill folder (`skills/render-sdd-template/res/`).
2. **Process Inputs & Fill Schema:**
   - Read template file content using `view_file`.
   - Replace placeholder YAML Frontmatter fields and Markdown headers with parameters.
   - Ensure final file content is written strictly in English.
3. **Write Destination File:**
   - Ensure target directory exists (`.agents/rules/`, `.agents/skills/<name>/`, `.agents/agents/`, `openspec/specs/<module>/`, `openspec/changes/<change-id>/`, `.agents/plugins/<name>/`).
   - Write processed content to `target_path`.
4. **Return Render Result:**
   - Report success status and target path back to caller agent.
