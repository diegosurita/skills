---
name: feature-document
description: >-
  Write an isolated feature as a Markdown document under .docs/feature/. Use
  when specifying a feature, adding or changing scenarios, or when the user
  asks for a feature document.
---

# Feature documents

Write one file per feature. The file is a reference for agents. It holds every scenario the feature must satisfy.

Create the file at:

```
.docs/feature/NNNN-<feature-name>.md
```

`<feature-name>` is kebab-case. `NNNN` is the next number in `.docs/feature/`. Example: `.docs/feature/0001-register-user.md`.

Every Markdown file this skill writes under `.docs/feature/` starts with that numeric prefix. The heading inside the file has no number.

Before creating a file, list `.docs/feature/`. If you cannot list it, ask. Do not guess a number. Create a missing directory and start at `0001`.

The next number is one greater than the highest numeric prefix in that directory, compared as an integer (`0009` is 9, `0010` is 10). Files that do not start with digits do not count. `.docs/ADR/` and `.docs/feature/` do not share a counter. Write the number with at least four digits. Past `9999`, write the full integer (`10000-…`). Never renumber an existing file, so a deleted number stays a gap. If that path is already taken, increment until the path is free.

A file matches `<feature-name>` when the kebab slug matches exactly. Strip one leading `<digits>-` before comparing. An unnumbered file matches on its whole basename. `register-user` does not match `0001-register-user-extra`. No match: create the file at the next number. One match: edit that file and keep its filename, including a legacy unnumbered name. Two matches: stop and ask which file to use.

Copy `template.md` from this skill into that path and replace every placeholder.

The file is Markdown. Each scenario's steps are Gherkin inside a fenced code block.

- The file is one isolated feature. Include every scenario it must satisfy: success, alternate paths, and failures.
- Scenarios state observable behavior. Do not name classes, modules, transport routes, storage layout, or framework details.
- Use `Background` only when every scenario in the file shares the same precondition. Otherwise omit it.
- Use `Scenario` for one case. Use `Scenario Outline` and `Examples` when the same behavior repeats with different data.
- Steps are `Given`, `When`, and `Then`, continued with `And` or `But`. One `When` per scenario.

When the feature changes, edit the one matching file and keep its filename. Do not add a second file for the same feature, and do not put another feature's scenarios in this file.
