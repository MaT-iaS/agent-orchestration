# Phase 1: Relevamiento De Requerimientos

## Goal

Analyze the user request and produce the requirement specification that will drive the rest of the workflow.

## Handoff Used

- Conditional: `HO-F1-01` in [../handoff/handoff-templates.md](../handoff/handoff-templates.md)

## Steps

1. Analyze the user request.
2. If the request is not sufficient to define requirements, ask up to 10 questions using the `questions` tool.
3. Use questions only to clarify functional requirements, non-functional requirements, domain requirements, technical requirements, or design constraints when needed.
4. If you need high-level codebase context to define requirements:
   - Do not read project files directly for this purpose.
   - Invoke Explorer with `HO-F1-01`.
   - Use the Explorer report to enrich the requirement specification.
5. Create `~/.cursor/.orchestrator/<req>-<guid>-<date>/`.
6. Persist the specification at `~/.cursor/.orchestrator/<req>-<guid>-<date>/spec-<req>-<guid>-<date>.md`.
7. If there were no clarification questions and no Explorer invocation, the spec can be equivalent to the original user requirement.
8. Once the spec is ready, continue only to phase 2.

## Do Not

- Do not skip directly to phases 3, 4, 5, or 6.
- Do not bypass Explorer when high-level codebase context is needed.
