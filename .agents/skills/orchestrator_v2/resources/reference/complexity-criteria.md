# Complexity Criteria

Use these exact scoring levels and weights.

## Criteria Table

| Criterio | Ponderación | 1 punto | 6 puntos | 10 puntos |
|---|---:|---|---|---|
| Archivos afectados | 10% | 1 archivo | 2-3 archivos | 4+ archivos |
| Nivel de dependencias | 20% | 0 nuevas | 1-2 menores (utils, helpers) | 3+ o dependencias mayores (frameworks, APIs) |
| Tipo de cambio | 15% | Visual/puntual (UI, texto, estilos) | Lógica compleja o refactor menor | Arquitectura nueva o refactor mayor |
| Riesgo de regresión | 40% | Bajo (cambio aislado) | Medio (afecta módulos relacionados) | Alto (funcionalidad core/crítica) |
| Conocimiento del codebase | 15% | Área conocida | Múltiples áreas del proyecto | Código legacy/arquitectura compleja |

## Formula

```text
Score = Σ(puntos_criterio × ponderación)
```

Round to the nearest integer.

## Agent Assignment

| Rango de score | Agente | Handoff |
|---|---|---|
| 1-5 | Coder Lite | `HO-F4-01` |
| 6-10 | Coder Pro | `HO-F4-02` |

## Examples

See [../examples/complexity-scoring-examples.md](../examples/complexity-scoring-examples.md).
