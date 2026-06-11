# Complexity Scoring Examples

## Example 1: Agregar validacion JWT al login

| Criterio | Situación | Puntos | Ponderación | Total |
|---|---|---:|---:|---:|
| Archivos afectados | 1 nuevo + 1 existente (2 archivos) | 6 | 0.10 | 0.60 |
| Nivel de dependencias | Usa lib JWT existente, 0 nuevas | 1 | 0.20 | 0.20 |
| Tipo de cambio | Lógica en función existente | 6 | 0.15 | 0.90 |
| Riesgo de regresión | Afecta seguridad, módulos relacionados | 6 | 0.40 | 2.40 |
| Conocimiento del codebase | Área auth conocida | 1 | 0.15 | 0.15 |
| Total |  |  |  | 4.25 -> 4 -> Coder Lite |

## Example 2: Crear modulo de pagos con API externa

| Criterio | Situación | Puntos | Ponderación | Total |
|---|---|---:|---:|---:|
| Archivos afectados | 5+ archivos nuevos | 10 | 0.10 | 1.00 |
| Nivel de dependencias | API externa + SDK de pagos nuevos | 10 | 0.20 | 2.00 |
| Tipo de cambio | Arquitectura nueva | 10 | 0.15 | 1.50 |
| Riesgo de regresión | Funcionalidad core de facturación | 10 | 0.40 | 4.00 |
| Conocimiento del codebase | Múltiples áreas (front, back, db) | 6 | 0.15 | 0.90 |
| Total |  |  |  | 9.40 -> 9 -> Coder Pro |
