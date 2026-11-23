# specify

Create spec-driven development artifacts from an agreed plan.

## Purpose

Turn a confirmed plan into `spec.md`, `plan.md`, and `tasks.md` under `.docs/specs/<feature-name>/`. `spec.md` records the solution. Add a feature document when the plan changes what a user or caller can observe, and an architecture decision record when the plan needs one. When no caller-visible outcome changes, skip the feature document.

## How to use

Ask the agent to specify, write the spec, or create the SDD artifacts after a plan session. The agent writes the artifacts and stops. Implementation is a separate request.

## Install

`specify` follows `feature-document` and `manage-adr`. Install all three:

```bash
npx skills add diegosurita/skills --skill specify --skill feature-document --skill manage-adr
```
