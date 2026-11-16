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
.docs/ADR/<decision-name>.md
```

`<decision-name>` is kebab-case. Example: `.docs/ADR/use-postgresql-as-system-of-record.md`.

Copy `template.md` from this skill into that path and replace every placeholder.

- The title is a short noun phrase stating the decision (`Use PostgreSQL as the system of record`).
- Status is one of: Proposed, Accepted, Rejected, Deprecated, Superseded by `.docs/ADR/<other-decision>.md`. Status is one value for the whole record.
- Context states the forces in neutral prose.
- Decision is active voice (`We will …`).
- Consequences include what becomes easier and what becomes harder.

When the record contains more than one choice, give each choice the same `###` heading under Context, Decision, and Consequences, in the same order. A heading is a short noun phrase for a choice the record already makes. Under that heading, put only the forces, the decision, and the consequences that belong to that choice. A record with one choice stays prose in those three sections.

Do not rewrite an accepted decision in place. Supersede it with a new ADR and point the old Status at the new file.
