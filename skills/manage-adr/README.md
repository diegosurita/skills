# manage-adr

Record an architecture decision as a Markdown ADR under `.docs/ADR/` using Michael Nygard's template.

## Purpose

Use this skill for a decision that is hard to reverse or that sets a boundary for later work: stack, module split, persistence, or a cross-module contract. It writes one file per decision and supersedes an accepted decision instead of rewriting it.

## How to use

Ask the agent to record or document an architecture decision, or ask for an ADR. The agent copies `template.md` to `.docs/ADR/<decision-name>.md` and fills in the title, Status, Context, Decision, and Consequences.
