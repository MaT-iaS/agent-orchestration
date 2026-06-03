---
name: bug-hunter
description: Esta habilidad se utiliza para el análisis, búsqueda y corrección de bugs  y errores, permitiendo identificar fallos, diagnosticar errores y aplicar soluciones efectivas para mejorar la estabilidad y funcionalidad del producto.
---

# Skill: Bug Hunter

Este flujo guía al agente para identificar, investigar y proponer soluciones a errores o bugs reportados por un usuario. Cada paso está diseñado para ser claro, estructurado y escalable.

---

## Flujo General de Trabajo

### FASE 1: Análisis Inicial

**Objetivo:**  
Recopilar y completar toda la información relevante sobre el problema o error reportado, en el archivo `progress`, para que el resto del proceso pueda avanzar con datos precisos.

**Pasos detallados:**

1. **Revisa la descripción proporcionada por el usuario**  
   - Examina cuidadosamente el mensaje o el reporte que el usuario ha enviado (por ejemplo, un error, una falla en el sistema, un comportamiento inesperado).  
   - Identifica los elementos clave: qué está fallando, cuándo ocurre, en qué contexto, qué mensajes aparecen, etc.

2. **Completa el archivo `progress` con la información disponible**  
   - Agrega los datos clave en el archivo `progress`.
   - Si el contenido del reporte es incompleto o ambiguo, **no asumas** nada que no esté claro.  
   
3. **Si faltan detalles importantes, usa la herramienta `questions`**  
   - Si el usuario no ha proporcionado información clave (por ejemplo, el entorno, el paso exacto, el tipo de dispositivo, el error o comportamiento esperado, etc), **usa la herramienta `questions`** para hacer preguntas interactivas.  
   - Ejemplos de preguntas:  
     - ¿En qué momento ocurre el error?
     - ¿Qué acción llevas a cabo justo antes de que ocurra el error?  
   - Espera a que el usuario responda antes de continuar.  
   - No avanzar sin tener esta información clave.

> **Importante:** Este paso es esencial para que el resto del proceso sea efectivo. Si no se completa bien, las siguientes investigaciones podrían estar basadas en suposiciones incorrectas.

---

### FASE-2: Exploración de Archivos y Recursos

**Objetivo:**  
Investigar qué archivos, componentes o registros podrían estar relacionados con el error o bug, usando un agente especializado para esta tarea.

**Pasos detallados:**

1. **Llama al agente de exploración**  
   - Usa el agente `@explorer` (ubicado en el archivo `.cursor/agents/explorer.md`) para que realice una búsqueda inteligente.  
   - El agente debe investigar los archivos, directorios, logs, configuraciones o scripts que podrían estar relacionados con el problema reportado.

2. **Especifica claramente qué está buscando**  
   - Puedes decir algo como:  
     *"Busca archivos o registros que tengan relación con el error que mencionaste, especialmente en el entorno de producción o en los logs de ejecución."*  
   - Incluye detalles como:  
     - Nombre del sistema o servicio afectado  
     - Tipos de archivos (logs, configuraciones, scripts, etc.)
     - Posibles ubicaciones (por ejemplo: `/var/log/app/`, `config/`, `dist/`)
     - bloques de codigos relacionados

3. **Revisa y resume los resultados del agente**  
   - El agente debe devolver una lista de archivos o recursos relevantes.  
   - Si hay múltiples resultados, ordenalos por probabilidad de estar relacionados con el error.  
   - Anota los nombres de los archivos, su ubicación y una breve descripción de su contenido o uso.

> 🔍 **Nota:** Este paso no debe ser automático ni genérico. Debe estar enfocado directamente en el error reportado. El agente debe actuar como un investigador experto, no como una herramienta de búsqueda general.

---

### FASE 3: Generación de Hipótesis

**Objetivo:**  
Basado en el análisis de los archivos y la descripción del error, proponer al menos 5 hipótesis sobre qué podría estar causando el problema.

**Pasos detallados:**

1. **Evalúa los hallazgos del paso anterior**  
   - Usa la información del análisis (del archivo `progress`) y los resultados del agente de exploración para formular posibles causas.  
   - Pregúntate: ¿Qué podría estar mal? ¿Qué cambios recientes ocurrieron? ¿Qué archivos podrían estar corruptos o mal configurados? ¿cual es el flujo normal y donde se interrumpe? ¿que esta bloqueando el flujo?


2. **Formula al menos 5 hipótesis**  
   - Cada hipótesis debe ser clara, específica y basada en evidencia (no solo suposiciones).  
   - Ejemplos de hipótesis:  
     - El error ocurre porque el archivo `config.json` está mal formateado.  
     - El sistema no puede encontrar una librería crítica debido a una ruta incorrecta en el log.  
     - El error aparece después de una actualización, lo que sugiere un conflicto de versiones o uno de ultimos cambios aplicados lo genero.

3. **Ordena las hipótesis de la más probable a la menos probable**  
   - Justifica cada ordenación con razones lógicas:  
     - ¿Qué evidencia apoya esta hipótesis?  
     - ¿Es más fácil de probar o de verificar?  
     - ¿Está directamente relacionada con el error reportado?

4. **Escribe cada hipótesis con un número, título y breve explicación**  siguiendo la estructura definida en el `progress` file
   - Ejemplo:  
     1. El archivo `config.json` está mal formateado → Se observó en el log que se genera un error de sintaxis al cargar el archivo.  
     2. El sistema no encuentra la librería `libx` → El error aparece en una llamada a una función que depende de esa librería.  
     3. Hay un problema de permisos en el directorio `/tmp` → El log muestra un error de acceso denegado en ese directorio.

> 📌 **Importante:** No generes hipótesis generales o vagas. Cada una debe estar respaldada por datos del usuario o del análisis realizado.

---

### Fase 4: Verificación de hipótesis

Esta fase tiene como objetivo validar si una hipótesis que se formuló al inicio del proceso es verdadera o falsa. Para hacerlo de forma efectiva, sigue estos pasos detallados:

---

**Paso 1: Encontrar la causa raíz usando la metodologia "5 whys"**

- **¿Qué es el método "5 whys**  
  Es una técnica de análisis que consiste en preguntar "¿por qué?" consecutivamente, de forma recursiva, para ir profundizando en el problema y llegar a su causa raíz (es decir, la causa fundamental que explica el problema, no solo su síntoma).

- **Cómo aplicarlo paso a paso:**  
  1. Comienza con la observación del problema (por ejemplo: "El sistema no responde").  
  2. Pregúntate: *"¿Por qué no responde el sistema?"*  
  3. Respuesta → Si es una causa intermedia (por ejemplo, "Porque el servidor está lento"), vuelve a preguntar: *"¿Por qué el servidor está lento?"*  
  .  
  4. Repite esta pregunta hasta que llegues a una causa que no sea simplemente un error de operación, sino una falla fundamental (por ejemplo, "Porque el disco de almacenamiento está lleno").  
  5. Esta última causa es la **causa raíz**.

- **Importante:**  
  No se debe detener en la primera respuesta. Cada "por qué" debe ir más allá del síntoma. Esto ayuda a evitar soluciones superficiales que solo cubren el problema temporalmente.

---

**Paso 2: Proponer un plan de acción para verificar la hipótesis**

- Una vez que hayas identificado la causa raíz, debes diseñar un plan práctico para **comprobar si esa causa realmente explica el problema**.

- **Qué tipo de pruebas puedes sugerir:**  
  - **Pruebas rápidas:** Acciones simples que se pueden ejecutar en pocos minutos, como reiniciar un servicio, cambiar un parámetro de configuración o enviar una solicitud de prueba.  
  - **Logs de depuración (debug logs):** agregar y Revisar logs en momentos clave para ver si hay errores, advertencias o mensajes que apoyen o contradigan la hipótesis.  
  - **Cambios rápidos en el código:** Si es posible, realizar una modificación mínima (por ejemplo, un cambio en una función o un valor de tiempo de espera) y observar el resultado. 

- **Objetivo del plan:**  
  El plan debe ser claro, ejecutable y debe permitir al usuario **verificar directamente** si la hipótesis es verdadera o falsa. No se trata de hacer una gran investigación, sino de probar algo concreto.

---

**Paso 3: Esperar la respuesta del usuario para evaluar el resultado**

- **No debes emitir un veredicto hasta que el usuario haya realizado las pruebas sugeridas.**  
- **Qué esperar del usuario:**  
  - ¿Qué resultado obtuvo al ejecutar las pruebas?  
  - ¿El problema sigue ocurriendo?  
  - ¿Se vieron errores en los logs?  
  - ¿El cambio en el código tuvo efecto?  

- **Tu rol:**  
  Ser un observador activo. No asumir resultados. Debes esperar que el usuario te responda con los datos reales obtenidos.

---

**Paso 4: Si la hipótesis se descarta, volver a la fase 4 con la siguiente hipótesis**

- Si las pruebas muestran que **la causa raíz propuesta no es correcta** (por ejemplo, el problema no se resuelve al hacer el cambio o los logs no muestran el error esperado), entonces **la hipótesis debe ser descartada**.

- En ese caso:  
  - **Vuelve a la Fase 4**  
  Selecciona la **siguiente hipótesis** en la lista  
  Repite todos los pasos desde el Paso 1 (hasta el Paso 3)  
  Continúa hasta que una hipótesis sea confirmada o se agoten las posibilidades

- **Importante:**  
  Cada vez que se descarta una hipótesis, se gana un paso más de conocimiento. Esto ayuda a acotar el problema y a enfocar mejor la solución final.

---
---

## Archivo de progreso
### generacion
el archivo `progress` se genera con la info obtenida al final de FASE 1 con este nombre y path  `.cursor/artifacts/bugs-hunter/bug-progress-{bugDesc}-{guid}.md`. donde guid es un identificador unico hexadecimal de 8 bits.

### Actualizacion del archivo
el archivo se debe actualizar en diferentes puntos del proceso siguiendo esta logica

- **FASE 2:** se actualiza la seccion de archivos relevantes encontrados
- **FASE 3:** se actualiza la seccion de hipotesis
- **FASE 4:** se actualizan las acciones del plan de accion en cada iteracion, con una descripcion del resultado de la accion ej (analisis de logs, resultados de pruebas, etc), se actualizan tambien la cadena de preguntas que llevaron la causa raiz 

**Estructura Header:**
```markdown
# 🐞 INFORMACIÓN DEL BUG

## Título
> <Título del bug>  
*(Debe ser claro, conciso y descriptivo. Ej: "Error al guardar cambios en formulario de usuario")*

## Descripción
> <Descripción detallada del comportamiento incorrecto, incluyendo contexto, efectos y escenarios comunes.>  
*(Máximo 150 palabras. Debe ser claro, objetivo y sin tecnicismos innecesarios.)*

## Pre-requisitos para reproducción
> - <Configuraciones iniciales>  
> - <Escenarios de uso>  
> - <Estado de sistema o datos iniciales>  
*(Ej: "El usuario debe estar autenticado con rol 'admin', y el sistema debe tener al menos 3 registros activos")*

## Pasos para reproducir el bug
1. <Acción 1>  
2. <Acción 2>  
...  
*(Cada paso debe ser claro, ejecutable y verificable.)*
```

**Estructura del cuerpo:**
```markdown
## Archivos relevantes
- `{filepath}` → [Nombre del archivo o componente]  
  *(Ej: `src/components/UserForm.js`, `api/v1/users.js`)*  
- Notas: <¿Qué se sabe sobre estos archivos?>  

## Hipótesis del bug
1. **Hipótesis 1**  
   - Descripción: <Explicación breve de por qué se cree que ocurre el bug>  
   - Hallazgos: <¿Qué se ha observado o verificado? ¿Qué evidencia hay?>  
   - Probabilidad: [1-100%] → [Alta / Media / Baja]  
   - Estado: [pending / confirmed / discard]  
   - Plan de acción:  
        [ ] - <Prueba sugerida para confirmar>
        [ ] - <Logs sugeridos para debug>
        [ ] - <Acción a realizar>  
        ...

2. **Hipótesis 2**  
   *(Si aplica, se puede agregar más hipótesis.)*  
   - Descripción: ...  
   - Hallazgos: ...  
   - Probabilidad: ...  
   - Estado: ...  
   - Plan de acción: ...  

## Plan de corrección (Estructura general)
1. **Análisis inicial**  
   - Verificar hipótesis  
   - Revisar logs y archivos

2. **Corrección técnica**  
   - Modificar código / configuración / API  
   - Aplicar cambios en entorno de desarrollo  

3. ... *(se puede extender según necesidad)*  

```

