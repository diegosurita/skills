# [Feature name]

**Spec**: `.docs/specs/<feature-name>/spec.md`

## Summary

[The approach the plan decided.]

## Technical context

[Only what this change uses, from the repository: language, storage, tests, and local environment.]

## Structure

- **Areas**: [Paths or components this change touches.]
- **Boundaries**: [How this change respects rules the project already has, or none.]

[Omit the list below when the change follows every project rule.]

- **Departure**: [Rule]
  - **Why needed**: [Reason]
  - **Simpler alternative rejected**: [Alternative]

## Decisions

### [Short noun phrase stating the decision]

[We will …]

**Why**: [Reason from the plan.]

**Rejected**: [Alternative the plan rejected.]

**ADR**: [`.docs/ADR/NNNN-<decision-name>.md`, or none.]

[Omit a snippet unless the plan already contains one that states a state machine, schema, or type shape more precisely than prose. When you include it, note that it came from the plan and trim it to this decision. Leave it out of every other section.]

## Data model

[Omit this section when the plan has no persistence change. Otherwise record the records, fields, and relationships the plan decided.]

## Interface contract

[Omit this section when the plan has no external interface change. Otherwise record the operations, results, and error behavior the plan decided.]

## Migration

[Omit this section when the plan has no migration. Otherwise record the deploy and rollback steps the plan decided.]

## Risks

[Omit this section when the plan names none.]

- **[Risk]** — [Mitigation the plan decided.]

## Open questions

[Omit this section when none. Include only an unknown that leaves the spec, the approach, and the task list unchanged.]

- [Deferrable unknown.]
