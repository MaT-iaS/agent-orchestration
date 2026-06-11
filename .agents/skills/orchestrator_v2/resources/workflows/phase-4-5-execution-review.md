# Phases 4-5: Ejecucion Y Revision

Phase 5 runs inside the phase 4 execution loop. Treat them as a single control cycle.

## Goals

- Phase 4: Execute the plan by parallel group.
- Phase 5: Review every implemented task before it counts as complete.

## Handoffs Used

- `HO-F4-01`
- `HO-F4-02`
- `HO-F4-03`
- `HO-F5-01`
- `HO-F5-02`

See [../handoff/handoff-templates.md](../handoff/handoff-templates.md).

## Coder Selection

- Complexity `1-5` -> `Coder Lite` with `HO-F4-01`
- Complexity `6-10` -> `Coder Pro` with `HO-F4-02`

Use the scoring rules in [../reference/complexity-criteria.md](../reference/complexity-criteria.md).

## Execution Loop

1. Read the parallel groups from the plan.
2. Process groups in order.
3. For each task in the current group:
   - Pick the coder by complexity.
   - Build an individual handoff for that task only, plus shared context.
4. Launch all tasks in the group in parallel.
5. Wait for all coder responses and validate them against `HO-F4-03`.
6. For each completed implementation:
   - Append the implementation entry to the progress file log.
   - Capture timestamps, agent, result, files, decisions, and findings.
   - Send that task to Reviewer with `HO-F5-01`.
7. Launch all reviews for the group in parallel.
8. Wait for all reviewer responses and validate them against `HO-F5-02`.
9. After each review result:
   - Append the review entry to the progress file log.
   - Update checkpoint status.
10. For each task with `NEEDS_IMPROVEMENT` or `REJECTED`:
   - Reassign to the appropriate coder with reviewer feedback.
   - Re-implement and re-review.
   - Limit each task to 3 attempts.
11. When all tasks in the group are either `APPROVED` or out of attempts:
   - Update the checkpoint for the completed group.
   - Move to the next group.
12. When no groups remain, continue to phase 6.

## Failure Handling

If a coder reports `FAILED`:

1. Record the failure in the progress file with reason and prior attempts.
2. If the task has 2 or fewer prior attempts, reassign it to the correct coder.
3. If the task exceeds 2 prior attempts, mark it as failed.
4. Evaluate whether dependent later-group tasks can continue or must stop.

## Non-Negotiable Review Rule

- Never mark a task complete based only on coder output.
- Never advance the group until review outcomes were processed.
- Never close with the user from this phase.
