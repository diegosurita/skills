---
name: specify
description: >-
  Create spec-driven development artifacts from an agreed plan. Use only when
  the user asks to specify, write the spec, or create SDD artifacts after a
  plan session.
disable-model-invocation: true
---

# Specify

Use this skill only when the user asks for it.

Write the artifacts for a change that already has a confirmed plan. Stop when the artifacts are consistent. Implementation is a separate request.

## Source of scope

The confirmed plan in the conversation is the only source of scope. Read that plan, and read its plan file when the conversation points at one.

Carry into the artifacts only what that plan decided. When a mandatory section cannot be filled from the plan or the repo, ask before writing `tasks.md`.

## Project guides

Before writing the artifacts, look the root of the repository for `STYLEGUIDE.md` and `CONTRIBUTING.md`. Read each file that exists. When both exist, apply both. When neither exists, continue from the plan and the repository.

Those files are project rules, not scope. Use their content while writing the artifacts:

- `plan.md` records the language, structure, tests, and boundaries those files already set. A plan decision that departs from one of them uses the departure fields and names the rule.
- `tasks.md` uses the paths, checks, and commands those files document. When they name a test, lint, or formatting command, use that command.
- `spec.md` and the feature document stay free of implementation detail. Carry a rule from those files into them only when it changes observable behavior the plan already includes.

## Where the files go

One directory per planned change. `<feature-name>` is the plan title in kebab-case.

```
.docs/specs/<feature-name>/
  spec.md
  plan.md
  tasks.md
```

When the same change is specified again, edit these files. Keep a single directory for that change.

Write in this order:

1. The feature document, when the plan has observable behavior.
2. An ADR, when the plan records a decision that is hard to reverse.
3. `spec.md`
4. `plan.md`
5. `tasks.md`

Copy the template named below and replace every placeholder. Drop a conditional section the plan leaves empty.

When the plan covers more than one isolated feature, write one feature document per feature. The directory name stays the plan title, and `spec.md` cites every feature document.

## Feature document

Follow the `feature-document` skill and read its `SKILL.md`. Create `.docs/feature/<feature-name>.md`.

`spec.md` cites that file by scenario name. Leave the scenario text in the feature document.

## Architecture decisions

Follow the `manage-adr` skill for a decision that is hard to reverse: stack, module split, persistence, or a cross-module contract. Link the ADR from `plan.md`. Leave the ADR body in its own file. An ordinary implementation choice stays in `plan.md` and gets no ADR.

## spec.md

Copy `spec-template.md` from this skill to `.docs/specs/<feature-name>/spec.md`.

This file is the behavior contract:

- Purpose, scope, and out of scope come from the plan.
- Each user story has a priority, why that priority, and how to test the story on its own. The story names the feature-document scenarios that prove it.
- Each functional requirement takes the next id, starting at `FR-001`, states one behavior with MUST, and points at the story and scenarios that test it.
- Key entities are domain concepts and relationships. Include them only when the plan has data.
- Success criteria are measurable outcomes the plan already stated.
- Assumptions are ones the plan already stated.

Keep frameworks, libraries, module paths, and transport details out of this file and out of the feature document.

## plan.md

Copy `plan-template.md` from this skill to `.docs/specs/<feature-name>/plan.md`.

Read the repository before filling technical context and structure. Record the language, storage, tests, and environment this change uses, and the paths and boundaries that repository already uses.

Record the approach the plan decided. Link `spec.md` instead of restating its purpose. Name the areas this change touches. A departure from a rule the project already has needs the reason and the simpler alternative the plan rejected. Each decision records the choice, why, and the rejected alternative, and links an ADR when one exists.

Use the data model, interface contract, migration, and risks sections only for what the plan decided. An open question belongs here only when it leaves the spec, the approach, and the task list unchanged. Ask the user when an answer would change any of those.

## tasks.md

Copy `tasks-template.md` from this skill to `.docs/specs/<feature-name>/tasks.md`.

Each task is a checkbox:

```markdown
- [ ] T001 [P] [US1] Action in an exact path, and the check that proves it.
```

- Number tasks `T001` upward in execution order.
- `[P]` marks a task that touches a different file and waits on nothing. Omit it otherwise.
- `[US1]` maps the task to a story in `spec.md`. Setup and foundational tasks omit the story label.
- One task is one session of work. The path is one the plan creates or that already exists.
- Phases run setup, then foundational work that blocks every story, then one phase per story from P1 onward, then polish. Drop foundational or polish when the plan has no such work.
- Inside a story, order the work the way the plan and the repository build it, then the tests for that story. Include a step only when the plan changes it. Verify story tests with the test command the project documents. Verify an end-to-end flow the plan includes with the project's end-to-end command. If the project documents no command, ask before inventing one.

## Consistency

Edit the artifacts until all of these hold:

- Every story has at least one scenario in a feature document, and every functional requirement points at a story.
- Every task traces to a story or to foundational work the plan named, and adds no scope the spec lacks.
- The feature document and `spec.md` stay free of implementation detail.
- `plan.md` matches the repository's structure, and the tasks use those paths.
- Rules in `STYLEGUIDE.md` and `CONTRIBUTING.md`, when those files exist, show up in `plan.md` and `tasks.md`.
- Any question that would change the spec, the approach, or the task list is answered.

Stop after the artifacts. Implement, migrate, or commit only when the user asks.
