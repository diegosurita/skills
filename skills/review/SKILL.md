---
name: review
description: >-
  Review implemented code for correctness, design, security, and tests.
  Use when reviewing a change, a diff, a branch, or a pull request, or when
  the user asks for a code review.
---

# Review

Review the change. Do not edit code unless the user asks to apply the findings.

The bar is code health. The change passes when it improves the system and has no blocking defect. Non-blocking notes do not hold it back. Where several designs are equally valid, accept the author's. Facts and the project's existing design outweigh preference.

Comment on the code, not the author. Explain why. Give a direction only when it unblocks a fix. Do not redesign the change in the review.

Do not comment on formatting or lint the project's format and lint tools would flag. Discover those commands from the project.

## Diff

Choose the diff before reading code:

- A pull request: `gh pr diff`.
- A branch: `git diff <base>...HEAD`. The default base is `main`.
- Otherwise: the working tree (`git diff` and `git diff --cached`) and commits on the branch that are not on `main`.

Review at most about 400 lines of changed code in one pass. Split a larger diff by module or commit. Say what each pass covered and what remains.

Read intent before lines: the change description, then tests, then production code. Design and correctness come before nits.

When a feature document or spec belongs to the change, read it and judge the code against that behavior. Feature documents live under `.docs/feature/`. Specs live under `.docs/specs/`.

## What to look for

Look for omissions. Do not nit every line.

1. Design and boundaries. The change fits the part of the system that owns it and follows boundaries the repository already uses.
2. Behavior and edge cases. The code does what the change claims, including empty input, missing records, and failure paths.
3. Security, answered from the diff. New entry points check authorization. Input is validated at the boundary. Data access is parameterized. Secrets and personal data stay out of code, logs, and error messages. Failures fail closed. A new dependency is necessary.
4. Tests. Tests ship with the change. They assert behavior and edge cases, not only the absence of an error.
5. Complexity and naming. Another developer can understand the code later. Names match the language of the code around them. Comments explain why, and only when the code cannot.
6. Documentation. Relevant docs, feature documents, and specs match the change.

A schema change includes a migration when the project uses migrations.

## Tests

Read the tests, then run them. Run the test command the project documents. Run the project's end-to-end command when externally observable behavior changes. If the project documents no command, say so instead of inventing one. Report the result, or say why they were not run.

## Findings

One finding per item. Name the file and line. Use Conventional Comments:

```text
issue (blocking): path:line — subject

Why, and the direction only when it unblocks the fix.
```

Labels:

- `issue` is blocking. A security finding is an `issue` and stays blocking.
- `suggestion`, `nitpick`, `question`, `note`, and `praise` are non-blocking unless marked `(blocking)`.
- Leave `praise` only when it is true.
- `question` is an uncertain concern, not a disguised demand.

Example:

```text
issue (blocking): orders/handler.ts:42 — This entry point accepts an order id and loads it with no authorization check.

A caller who knows the id can read another account's order. Check the caller against the order's owner before returning it.
```

## Verdict

End with one verdict:

- **Approve** — the change improves the system and has no findings.
- **Approve with comments** — only non-blocking notes.
- **Request changes** — one or more blocking findings.

Then a short summary, the findings, the tests run, and any slice not reviewed.
