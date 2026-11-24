# feature-document

Write an isolated feature as a Markdown document under `.docs/feature/`.

## Purpose

Record every scenario a feature must satisfy, as Gherkin, so agents can use the file as the behavior reference.

## How to use

Ask the agent to specify a feature, add or change scenarios, or write a feature document. The agent copies `template.md` to `.docs/feature/NNNN-<feature-name>.md` and fills it in.

## Install

```bash
npx skills add diegosurita/skills --skill feature-document
```
