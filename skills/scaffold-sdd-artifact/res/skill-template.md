---
id: "skill-id-kebab-case"
name: "skill-name-kebab-case"
description: "Clear description of when and how the agent should trigger this skill"
inputs:
  param_1:
    type: "string"
    description: "Parameter description"
    default: "default_value"
outputs:
  status:
    type: "string"
    enum: ["success", "failure"]
tools:
  - "run_command"
---

# Skill Execution Protocol

1. Procedural step-by-step instructions for environment or terminal execution.
2. Shell commands inside markdown code blocks.
3. Post-execution validation and error handling steps.
