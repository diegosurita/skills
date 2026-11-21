# review

Review a change for correctness, design, security, and tests.

## Purpose

Judge a diff, branch, or pull request against code health. One part checks behavior against the feature document, spec, or change description. The other checks defects: design, security, performance, and compatibility. The review does not edit code unless you ask.

## How to use

Ask the agent to review a change, a diff, a branch, or a pull request. It reviews behavior and defects, then returns a verdict: Approve, Approve with comments, or Request changes.

## Install

```bash
npx skills add diegosurita/skills --skill review
```
