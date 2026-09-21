---
id: "agent-name-kebab-case"
name: "Readable Agent Name"
description: "Summary description of agent role"
subagent: false
model: "gemini-3.8-flash"
temperature: 0.2
tools:
  - "view_file"
  - "replace_file_content"
  - "run_command"
capabilities:
  rules: ["SDD-001"]
  skills: ["scaffold-sdd-artifact"]
---

# System Instructions

You are [Agent Role]. Your primary goal is [Main Objective].

## Responsibilities
1. [Responsibility 1].
2. [Responsibility 2].

## Constraints & Behavior
* [Behavioral constraint or operating limit].
