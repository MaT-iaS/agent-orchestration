# Handoff Templates

Use these templates exactly when invoking or validating subagents.

## Index

| ID | Phase | Direction | When to use |
|---|---|---|---|
| HO-F1-01 | 1 | Orchestrator -> Explorer | Need high-level codebase context to define requirements |
| HO-F2-01 | 2 | Orchestrator -> Explorer | Need detailed exploration for planning |
| HO-F2-02 | 2 | Explorer -> Orchestrator | Explorer detailed report response |
| HO-F4-01 | 4 | Orchestrator -> Coder Lite | Task complexity 1-5 |
| HO-F4-02 | 4 | Orchestrator -> Coder Pro | Task complexity 6-10 |
| HO-F4-03 | 4 | Coder -> Orchestrator | Implementation report |
| HO-F5-01 | 4-5 | Orchestrator -> Reviewer | Task review request |
| HO-F5-02 | 4-5 | Reviewer -> Orchestrator | Review verdict |
| HO-F6-01 | 6 | Orchestrator -> Usuario | Final delivery summary |

## HO-F1-01: Orchestrator -> Explorer

Phase 1 - Exploracion general

```text
[ORCHESTRATOR → EXPLORER]
---
Tipo: EXPLORACIÓN GENERAL
Requerimiento: <qué pide el usuario>
Necesito: entender el proyecto a alto nivel para definir los requerimientos
Buscar: estructura general, tecnologías, frameworks, módulos principales
```

## HO-F2-01: Orchestrator -> Explorer

Phase 2 - Exploracion detallada

```text
[ORCHESTRATOR → EXPLORER]
---
Tipo: EXPLORACIÓN DETALLADA
Requerimiento: <especificación del requerimiento>
Áreas de enfoque: ["src/modules/...", "src/shared/..."]
Necesito: rutas exactas, imports, firmas de funciones, dependencias, patrones
          de código para planificar la implementación

[OPTIONAL]
- Áreas a excluir: [...]
- Tecnologías preferidas: [...]
```

## HO-F2-02: Explorer -> Orchestrator

Phase 2 - Response contract

```text
[EXPLORER → ORCHESTRATOR]
---
Formato: Usa el formato definido en `.agents/agents/explorer.md`
```

## HO-F4-01: Orchestrator -> Coder Lite

Phase 4 - Complexity 1-5

```text
[ORCHESTRATOR → CODER_LITE]
---
Plan ID: <id>
Tarea asignada: <id> - <título>
Contexto: <frameworks, patrones, convenciones>
Reporte Explorer: <archivos, dependencias, patrones>
Estado del sistema: <qué existe después de grupos previos>
```

## HO-F4-02: Orchestrator -> Coder Pro

Phase 4 - Complexity 6-10

```text
[ORCHESTRATOR → CODER_PRO]
---
Plan ID: <id>
Tarea asignada: <id> - <título> (<descripción>)
Contexto: <frameworks, patrones, convenciones>
Reporte Explorer: <archivos, dependencias, patrones>
Estado del sistema: <qué existe después de grupos previos>
```

## HO-F4-03: Coder -> Orchestrator

Phase 4 - Response contract

```text
[CODER → ORCHESTRATOR]
---
Formato: Usa el formato definido en `.agents/agents/coder_lite.md` o `.agents/agents/coder_pro.md` según corresponda
```

## HO-F5-01: Orchestrator -> Reviewer

Phase 4-5 - Review request

```text
[ORCHESTRATOR → REVIEWER]
---
Diff: <cambios realizados>
Tarea: <id> - <requerimientos>
Contexto: <frameworks, patrones, convenciones>

[OPTIONAL]
- Estado esperado: <qué debería pasar>
- Estado actual: <qué está pasando>
```

## HO-F5-02: Reviewer -> Orchestrator

Phase 4-5 - Response contract

```text
[REVIEWER → ORCHESTRATOR]
---
Formato: Usa el formato definido en `.agents/agents/reviewer.md`
```

## HO-F6-01: Orchestrator -> Usuario

Phase 6 - Final delivery

```text
[ORCHESTRATOR → USUARIO]
---
Progress file finalizado: `~/.cursor/.orchestrator/<req>-<guid>-<date>/progress-<req>-<guid>-<date>.md`

Resumen:
- Estado: COMPLETADO
- Archivos: N creados, M modificados
- Decisiones: N importantes

Veredicto final: APPROVED
```
