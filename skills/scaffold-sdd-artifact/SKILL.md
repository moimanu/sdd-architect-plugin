---
id: "scaffold-sdd-artifact"
name: "scaffold-sdd-artifact"
description: "Generates new SDD artifacts (Rule, Skill, Spec, Agent, Workflow) by reading templates from res/"
inputs:
  artifact_type:
    type: "string"
    description: "The type of SDD artifact to generate"
    enum: ["rule", "skill", "spec", "agent", "workflow"]
  artifact_id:
    type: "string"
    description: "Unique identifier for the artifact (kebab-case or uppercase for rules)"
  artifact_name:
    type: "string"
    description: "Human readable or kebab-case name"
  target_path:
    type: "string"
    description: "Destination file path relative to project root"
outputs:
  status:
    type: "string"
    enum: ["success", "failure"]
tools:
  - "run_command"
  - "view_file"
---

# Protocol for Scaffolding SDD Artifacts

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
