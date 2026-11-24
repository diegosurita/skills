---
name: manage-adr
description: >-
  Record an architecture decision as a Markdown ADR under .docs/ADR/ using
  Michael Nygard's template. Use when making or documenting an architecture
  decision, or when the user asks for an ADR.
---

# Architecture decision records

Write an ADR for a decision that is hard to reverse or that sets a boundary for later work: stack, module split, persistence, or a cross-module contract. Skip small implementation choices.

Create one file per decision:

```
.docs/ADR/NNNN-<decision-name>.md
```

`<decision-name>` is kebab-case. `NNNN` is the next number in `.docs/ADR/`. Example: `.docs/ADR/0001-use-postgresql-as-system-of-record.md`.

Every Markdown file this skill writes under `.docs/ADR/` starts with that numeric prefix. The heading inside the file has no number.

Before creating a file, list `.docs/ADR/`. If you cannot list it, ask. Do not guess a number. Create a missing directory and start at `0001`.

The next number is one greater than the highest numeric prefix in that directory, compared as an integer (`0009` is 9, `0010` is 10). Files that do not start with digits do not count. `.docs/ADR/` and `.docs/feature/` do not share a counter. Write the number with at least four digits. Past `9999`, write the full integer (`10000-…`). Never renumber an existing file, so a deleted number stays a gap. If that path is already taken, increment until the path is free.

A file matches `<decision-name>` when the kebab slug matches exactly. Strip one leading `<digits>-` before comparing. An unnumbered file matches on its whole basename. `use-postgresql` does not match `0001-use-postgresql-as-system-of-record`. No match: create the file at the next number. One match: do not create a second file for that slug. Two matches: stop and ask which file to use.

Copy `template.md` from this skill into that path and replace every placeholder.

- The title is a short noun phrase stating the decision (`Use PostgreSQL as the system of record`).
- Status is one of: Proposed, Accepted, Rejected, Deprecated, Superseded by `.docs/ADR/NNNN-<other-decision>.md`. Status is one value for the whole record.
- Context states the forces in neutral prose.
- Decision is active voice (`We will …`).
- Consequences include what becomes easier and what becomes harder.

When the record contains more than one choice, give each choice the same `###` heading under Context, Decision, and Consequences, in the same order. A heading is a short noun phrase for a choice the record already makes. Under that heading, put only the forces, the decision, and the consequences that belong to that choice. A record with one choice stays prose in those three sections.

Do not rewrite an accepted decision in place. Supersede it with a new ADR, a new slug, and the next number. Leave the old filename in place and point the old Status at the new numbered path.
