# implement

Implement a named spec one task at a time, then review until the verdict is positive.

## Purpose

Run each unchecked task in `.docs/specs/<feature-name>/tasks.md` with test-driven development, in its own subagent, then review the change and adjust blocking findings until the review approves it.

## How to use

Ask the agent to implement a spec and name the spec directory. The agent does not commit unless you ask.

## Install

`implement` follows `review`. Install both:

```bash
npx skills add diegosurita/skills --skill implement --skill review
```
