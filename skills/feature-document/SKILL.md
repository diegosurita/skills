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
.docs/feature/<feature-name>.md
```

`<feature-name>` is kebab-case. Example: `.docs/feature/register-user.md`.

Copy `template.md` from this skill into that path and replace every placeholder.

The file is Markdown. Each scenario's steps are Gherkin inside a fenced code block.

- The file is one isolated feature. Include every scenario it must satisfy: success, alternate paths, and failures.
- Scenarios state observable behavior. Do not name classes, modules, transport routes, storage layout, or framework details.
- Use `Background` only when every scenario in the file shares the same precondition. Otherwise omit it.
- Use `Scenario` for one case. Use `Scenario Outline` and `Examples` when the same behavior repeats with different data.
- Steps are `Given`, `When`, and `Then`, continued with `And` or `But`. One `When` per scenario.

When the feature changes, edit this file. Do not add a second file for the same feature, and do not put another feature's scenarios in this file.
