# [Feature name]

**Spec**: `.docs/specs/<feature-name>/spec.md`

**Plan**: `.docs/specs/<feature-name>/plan.md`

`- [ ] T001 [P] [US1] Action in an exact path, and the check that proves it.`

`[P]` is a different file with no dependency. `[US1]` is a story in `spec.md`. Setup, foundational tasks, and tasks for a structural decision omit the story label. Add one phase per remaining story, in priority order, using the next phase number. When the plan states no new or changed outcome, omit `[USn]` and replace the story phases with the decision phase. When some outcomes change and others do not, keep the story phases, and keep the decision phase for structural tasks that block no story.

## Phase 1: Setup

- [ ] T001 [Action in an exact path], verified by [check].

## Phase 2: Foundational

[Omit this phase when nothing blocks every story. When the plan has no stories, omit it when nothing blocks the decision. Structural tasks that block every story stay in this phase and omit the story label.]

- [ ] T002 [Action in an exact path], verified by [check].

## Phase 3: US1 - [Title] (P1)

[Omit this phase when the plan states no new or changed outcome for a user or caller.]

**Goal**: [What this story delivers.]

**Independent test**: [The check named for US1 in spec.md.]

- [ ] T003 [P] [US1] [Action in an exact path the plan names], verified by [check].
- [ ] T004 [US1] Add the tests for this story in the path the plan names, verified by the project's test command.

## Phase 4: [Decision name]

[Omit this phase when no structural task remains outside Setup, Foundational, and the story phases. When no caller-visible outcome changes, this phase replaces the story phases. Omit the story label.]

- [ ] T005 [Action in an exact path the plan names], verified by [the check the plan named].

## Phase 5: Polish

[Omit this phase when no work crosses stories. When the plan has no stories, omit it when the plan has no cross-cutting work.]

- [ ] T006 [Action that crosses earlier phases, in an exact path], verified by [check].
