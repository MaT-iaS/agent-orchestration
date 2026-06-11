# Plan Example

```text
Plan Id: PLAN_LOGIN
Descripción: Crear flujo de autenticación con email/password
Complejidad estimada: 7
Tareas:
  - AUTH-01: UI formulario login
  - AUTH-02: Validación inputs cliente
  - AUTH-03: API login

Parallel Groups:
  - Grupo 1: [AUTH-01, AUTH-03]
  - Grupo 2: [AUTH-02]

### AUTH-01
- **Tarea**: Crear UI del formulario de login
- **Descripción**: Componente React para ingreso de credenciales
- **Objetivo**: Formulario reutilizable con email, password y botón submit
- **Complejidad**: 4

**Pasos concretos:**
1. Crear archivo `/src/components/auth/LoginForm.tsx`
2. Importar `useState` de React
3. Definir estado: `email`, `password`, `error`, `loading`
4. Crear función `handleSubmit` que valide email (regex) y passwords (no vacío)
5. Renderizar `<form>` con:
   - `<input type="email" name="email" required>`
   - `<input type="password" name="password" required>`
   - `<button type="submit">Iniciar sesión</button>`
6. Mostrar error debajo del campo correspondiente cuando falle validación
7. Agregar `disabled={loading}` al botón durante submit

**Archivos:**
- `/src/components/auth/LoginForm.tsx`: Crear componente
- `/src/components/auth/LoginForm.module.css`: Crear estilos

**Input esperado**: Archivos no existen
**Output esperado**: Archivos creados con componente exportado por defecto

**Requisitos:**
- Input email con validación de formato (regex: `/^[^\s@]+@[^\s@]+\.[^\s@]+$/`)
- Input password (type="password")
- Botón "Iniciar sesión"
- Mensajes de error debajo de cada campo
- Loading state: mostrar texto "Cargando..." cuando `loading=true`
- Accesibilidad: label asociado con `htmlFor`, aria-live para errores

**Riesgos a evitar:**
- Validaciones solo en frontend sin feedback visual
- Inputs no controlados (usar useState)
- Sin labels (accesibilidad)

**Restricciones:**
- React + TypeScript
- Sin librerías externas de UI
- CSS Modules (no styled-components)
- Usar función `onSubmit` del form, no `onClick` del botón

**Dependencias**: -
```
