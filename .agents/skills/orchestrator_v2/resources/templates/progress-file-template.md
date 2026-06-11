# Progress File Template

Use this exact progress file structure.

```text
# Progress Report - <Nombre del Plan>

> Este archivo se genera en Fase 3, se actualiza durante Fases 4-5, y se completa en Fase 6.
> Las secciones de REPORTE se completan en Fase 6. Las secciones de LOG se escriben durante Fases 4-5.

--- REPORTE (se completa en Fase 6) ---

## Resumen Ejecutivo
- **Objetivo**: <qué se implementó>
- **Estado**: COMPLETADO | COMPLETADO CON OBSERVACIONES | FALLIDO
- **Tareas totales**: N | Completadas: X | Fallidas: Y | Omitidas: Z

## Información del Requerimiento
- **Requerimiento original**: <qué solicitó el usuario>
- **Objetivo del cambio**: <qué problema resuelve>

## Plan Ejecutado
- **Plan ID**: PLAN_XXX
- **Complejidad estimada**: <1-10>
- **Tareas ejecutadas**:
  - [✓] TASK-01: <título> - <estado>
  - [✓] TASK-02: <título> - <estado>
  - [!] TASK-03: <título> - <estado> (fallida, omitida)

## Cambios Realizados
- **Archivos creados**: N
- **Archivos modificados**: N
- **Archivos eliminados**: N
- **Líneas añadidas**: ~X
- **Líneas eliminadas**: ~Y

### Archivos Creados
| Archivo | Propósito |
|---------|-----------|
| /ruta/archivo.ts | <descripción> |

### Archivos Modificados
| Archivo | Cambios |
|---------|---------|
| /ruta/archivo.ts | <qué se modificó> |

### Archivos Eliminados (si aplica)
| Archivo | Razón |
|---------|-------|
| /ruta/archivo.ts | <por qué se eliminó> |

## Impacto y Side Effects
- **Archivos potencialmente afectados**: <lista>
- **Efectos secundarios identificados**: <lista>
- **Áreas que requieren atención**: <lista>

## Revisión Final
- **Veredicto**: APPROVED | NEEDS_IMPROVEMENT | REJECTED
- **Intentos de revisión totales**: N/3
- **Feedback aplicado**: <si aplica>

## Estado Final
<Descripción del estado actual del sistema tras los cambios>

## Recomendaciones (opcional)
- <recomendación 1>
- <recomendación 2>

--- LOG DE EJECUCIÓN (se escribe durante Fases 4-5) ---

## Metadata
- **Plan ID**: PLAN_XXX
- **Requerimiento**: <descripción corta>
- **Fecha inicio**: YYYY-MM-DD HH:MM
- **Fecha última actualización**: YYYY-MM-DD HH:MM

## Checkpoint
- **Fase actual**: [nombre]
- **Grupo actual**: [id o "ninguno"]
- **Tareas del grupo**: [id1, id2, ...]
- **Tareas completadas del grupo**: X/Y
- **Tareas totales completadas**: X/Y
- **Tareas en re-trabajo**: [id2 (intento 2/3)]
- **Tareas fallidas**: [id3]

## Log de Ejecución

### [TASK-XX] <título> — COMPLETED
- **Timestamp**: YYYY-MM-DD HH:MM
- **Agente**: coder_lite | coder_pro
- **Complejidad**: N
- **Resultado**: <resumen de lo implementado>
- **Archivos creados**:
  - `/ruta/archivo.ts`: <propósito>
- **Archivos modificados**:
  - `/ruta/archivo.ts`: <qué se cambió>
- **Decisiones tomadas**:
  - <decisión 1>: <justificación>
- **Hallazgos relevantes**:
  - <hallazgo 1>
- **Notas**: <observaciones del coder>

### [TASK-XX] <título> — REVIEW: APPROVED
- **Timestamp**: YYYY-MM-DD HH:MM
- **Agente**: reviewer
- **Veredicto**: APPROVED
- **Intentos**: 1
- **Feedback aplicado**: <si hubo feedback en intentos previos>
- **Notas del reviewer**: <comentarios relevantes>

### [TASK-XX] <título> — REVIEW: NEEDS_IMPROVEMENT
- **Timestamp**: YYYY-MM-DD HH:MM
- **Agente**: reviewer
- **Veredicto**: NEEDS_IMPROVEMENT
- **Intento**: 2/3
- **Feedback**:
  - <punto 1>
  - <punto 2>
- **Acción**: Re-asignado a coder_pro con mejoras solicitadas

### [TASK-XX] <título> — REVIEW: REJECTED
- **Timestamp**: YYYY-MM-DD HH:MM
- **Agente**: reviewer
- **Veredicto**: REJECTED
- **Razón**: <explicación del rechazo>
- **Acción**: Re-asignado a coder_pro con correcciones

### [TASK-XX] <título> — FAILED
- **Timestamp**: YYYY-MM-DD HH:MM
- **Agente**: coder_lite | coder_pro
- **Razón**: <por qué falló>
- **Intentos previos**: N
- **Acción**: <reintentado | omitido | escalado al usuario>

## Decisiones de Diseño
- **[TASK-XX]**: <decisión> → Justificación: <por qué>

## Hallazgos Relevantes
- **[TASK-XX]**: <hallazgo que podría afectar otras tareas o el sistema>
```

## Writing Rules

1. The report section is created as a placeholder in phase 3 and completed in phase 6.
2. In the log section:
   - `Log de Ejecución` is append-only.
   - `Checkpoint` is always overwritten with current state.
3. `Decisiones de Diseño` and `Hallazgos Relevantes` are append-only.
4. Use `YYYY-MM-DD HH:MM` timestamps consistently.
5. If a task has multiple attempts, record each attempt as a separate entry.
