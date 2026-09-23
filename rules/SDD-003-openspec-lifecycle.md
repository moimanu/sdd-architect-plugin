---
description: "Defines OpenSpec change proposal lifecycle, delta merging into living specs, and archiving standards."
---

# SDD OpenSpec Lifecycle and Archiving

> **Scope**: Applies to specifications, change proposals, and archives under `openspec/**`.

## Mandatory Guidelines

1. **OpenSpec Lifecycle Stages:** All feature development, architectural updates, and functional changes MUST follow the 3-stage OpenSpec sequence:
   - **specs/ (`Living Specifications`):** Serves as the authoritative source of truth for the system's current state (`openspec/specs/<module>/spec.md`).
   - **changes/<change-id>/ (`Active Changes`):** Mandatory pipeline for any changes to existing specifications. Contains `proposal.md` describing rationale/context, along with spec deltas (`specs/<module>/spec.md`) marked explicitly with requirement changes (`ADDED`, `MODIFIED`, `REMOVED`).
   - **archive/ (`Immutable Delivery History`):** Upon completing implementation and validation, deltas are merged into the living specifications in `openspec/specs/`, and the change folder is moved to `openspec/archive/YYYY-MM-DD_<change-id>/`.

2. **Execution Steps within Changes:**
   - **Explore:** Inspect existing living specs in `openspec/specs/` to understand current capabilities.
   - **Proposal & Deltas:** Scaffold `openspec/changes/<change-id>/proposal.md` and spec deltas.
   - **Execute:** Implement the changes in codebase according to the proposal.
   - **Verify & Archive:** Merge deltas into `openspec/specs/` and archive the change folder.

## Anti-Patterns (What NOT to do)

* **DO NOT** modify living specifications in `openspec/specs/` directly without going through an active change proposal in `openspec/changes/<change-id>/`.
* **DO NOT** leave active change proposals in `openspec/changes/` after implementation and verification are finalized.
* **DO NOT** delete change folders instead of archiving them to `openspec/archive/`.
