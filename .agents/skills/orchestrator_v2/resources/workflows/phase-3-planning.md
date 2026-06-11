# Phase 3: Planificacion

## Goal

Produce a detailed plan and initialize the progress file before any execution starts.

## Inputs You May Use

- Original user requirement
- Formal spec from phase 1
- Explorer general-context report from phase 1, if present
- Explorer detailed report from phase 2

Use whatever is available. Do not wait for sources that do not exist.

## Steps

1. Build a detailed plan using the available inputs.
2. Split the work into bite-sized, verifiable tasks.
3. For each task, include everything needed to execute it:
   - Exact file paths
   - Example code when helpful
   - Function, method, variable, or config names
   - Concrete execution steps
4. Score each task using [../reference/complexity-criteria.md](../reference/complexity-criteria.md).
5. Define parallel groups:
   - Tasks in the same group must not depend on each other.
   - Tasks in the same group must not modify the same files.
   - Dependencies may only flow from earlier groups to later groups.
6. Persist the plan at `~/.cursor/.orchestrator/<req>-<guid>-<date>/plan-<req>-<guid>-<date>.md`.
7. Initialize the progress file at `~/.cursor/.orchestrator/<req>-<guid>-<date>/progress-<req>-<guid>-<date>.md`.
8. Use the exact structures from:
   - [../templates/plan-template.md](../templates/plan-template.md)
   - [../templates/progress-file-template.md](../templates/progress-file-template.md)
9. Show the plan to the user and explain what it contains.
10. Tell the user they may edit the plan file if needed.
11. Stop and wait. Ask for explicit confirmation with the `questions` tool using: `¿Confirmas el plan para continuar con la ejecución?`
12. Before phase 4, re-read the plan if the user modified it.

## Blocking Rule

Do not continue to phase 4 unless all of these are true:

- The plan was generated on disk.
- The progress file was initialized.
- The plan was shown to the user.
- The user explicitly confirmed execution.

## Plan Structure

Use the exact structure in [../templates/plan-template.md](../templates/plan-template.md).

## Example

See [../examples/plan-example.md](../examples/plan-example.md).
