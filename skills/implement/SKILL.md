---
name: implement
description: >-
  Implement a named spec one task at a time with test-driven development,
  then review until the verdict is positive. Use only when the user asks to
  implement a spec, execute tasks.md, or build the change in a
  .docs/specs/ directory.
disable-model-invocation: true
---

# Implement

Use this skill only when the user asks for it.

Orchestrate the implementation. Do not implement a task and do not review the diff. Each task, each fix, and each review runs in a new subagent. Do not resume a subagent, and do not reuse an agent id.

## Spec name

The user names the spec. That name is the directory `.docs/specs/<feature-name>/`. If the message does not name it, ask for the name and wait. Do not infer it from open files or git status.

If that directory does not exist, say so and stop. If the name is not an exact directory and more than one directory matches, ask which one.

## Read the artifacts

Read these before the first task:

- `.docs/specs/<feature-name>/spec.md`
- `.docs/specs/<feature-name>/plan.md`
- `.docs/specs/<feature-name>/tasks.md`
- Every feature document cited by `spec.md`
- Every ADR linked from `plan.md`

Take unchecked tasks from `tasks.md` from top to bottom. Skip tasks already marked `[x]`. A `[P]` marker does not run tasks in parallel.

## One subagent per task

For each unchecked task, launch a new `generalPurpose` subagent and wait until it finishes. Do not set `resume`.

A subagent does not inherit this conversation, so the prompt is the whole assignment. Include only what that task needs:

- The task id and its text, including the paths it may change.
- The check, and the command that runs it. That command is the project's test command, the end-to-end command when the check is an end-to-end flow, or the migration command when the task is a migration. Name it in the prompt. If the project documents no command, ask before inventing one.
- The story's independent test and the scenarios it names, quoted, only when the task line does not already state the behavior the check must prove. Include no other story.
- The interface operation, data-model fields, migration step, boundary, or decision this task implements, quoted from `plan.md`, only when the task would be wrong without it. Leave out the rest of the plan, and any ADR that does not constrain this task.

The assignment tells the subagent to implement only that task, with test-driven development:

1. **Red.** Add or extend a failing test for the task's check. Run the command in the assignment and confirm it fails for the reason the task describes.
2. **Green.** Write only that task's production change. Rerun the same check and confirm it passes.
3. **Refactor.** Clean the code without changing behavior. The check still passes.

Name the test file in the assignment when the plan or a later task names one for that story. A later task that only adds that test file extends the tests still missing and runs them. It does not duplicate tests already added. A scaffold task with nothing to assert skips the red step and says so in its return.

The subagent reads and edits the code at the paths the assignment names, and follows the structure of that code. It does not open `spec.md`, `plan.md`, feature documents, or ADRs. It does not take work from other lines in `tasks.md`. It marks only that task `[x]` after the check passes. It returns the files changed, the command, and the result.

Start the next task only after that return. If the check failed, launch a new subagent for the same task with that same assignment plus the failure. Do not add the plan. Do not resume the subagent that failed.

## Review

After the last task, launch a new subagent. Do not resume an implementation subagent. The prompt tells it to follow the `review` skill and read its `SKILL.md`, and names the spec directory `.docs/specs/<feature-name>/`. It does not edit code. It returns the verdict, the findings, and the tests.

A positive result is **Approve** or **Approve with comments**. **Request changes** is not positive. Non-blocking notes do not start another implementation.

## Adjust

When the verdict is **Request changes**, launch one new subagent per blocking finding, in the order the review listed them. The prompt is that finding — file, line, subject, why, and the direction when the review gave one — the same red-green-refactor cycle, and the command. Leave out the plan, the spec, and the other findings. Do not resume the reviewer or any earlier implementer.

Then launch a new review subagent the same way. Repeat until the verdict is positive.

If a new review returns a blocking finding that the previous adjustment already claimed to fix, stop and report that finding to the user.

## Report

Report the verdict, the tasks completed, and the tests run. Do not commit unless the user asks.
