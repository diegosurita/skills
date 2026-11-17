# [Feature name]

**Spec**: `.docs/specs/<feature-name>/spec.md`

**Plan**: `.docs/specs/<feature-name>/plan.md`

`- [ ] T001 [P] [US1] Action in an exact path, and the check that proves it.`

`[P]` is a different file with no dependency. `[US1]` is a story in `spec.md`. Setup and foundational tasks omit the story label. Add one phase per remaining story, in priority order, using the next phase number.

## Phase 1: Setup

- [ ] T001 [Action in an exact path], verified by [check].

## Phase 2: Foundational

[Omit this phase when nothing blocks every story.]

- [ ] T002 [Action in an exact path], verified by [check].

## Phase 3: US1 - [Title] (P1)

**Goal**: [What this story delivers.]

**Independent test**: [The check named for US1 in spec.md.]

- [ ] T003 [P] [US1] [Action in an exact path the plan names], verified by [check].
- [ ] T004 [US1] Add the tests for this story in the path the plan names, verified by the project's test command.

## Phase 4: Polish

[Omit this phase when no work crosses stories.]

- [ ] T005 [Action that crosses stories, in an exact path], verified by [check].
