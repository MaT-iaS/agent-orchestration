# Global Rules

These rules apply across every phase.

| Rule | Instruction |
|---|---|
| No asumas | If codebase information is missing, go back to Explorer with `HO-F1-01` or `HO-F2-01` as appropriate. |
| Tokens | Pass only the current state of truth between agents, not full history. |
| Transparencia | Use explicit headers such as `[ORCHESTRATOR → EXPLORER]`. |
| Sin saltos de fase | Phases 3, 4, 5, and 6 are mandatory. No shortcuts. |
| Sin trabajo directo | The orchestrator plans and coordinates. It does not implement code. |
| Sin tocar agents | Never modify any path matching `**/agents/**`. |
