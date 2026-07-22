# Entregable · Sesión 3 — Copilotos IA

- **Nombre / usuario:** Ruben Martinez Tapia
- **Fecha de entrega:** 19-julio-2026
- **Repo auditado en la Parte A** "front Gatsby, Proyecto de logistica"

---

## 1. Hallazgos de la auditoría (Parte A)

> 3-5 cosas que el agente **no pudo inferir** del código y que tendrías que decirle explícitamente.
> Redáctalas para que otra persona las entienda sin contexto adicional. **Sin código propietario ni secretos.**

1. No es preciso en las versiones de las dependencias que maneja el proyecto
- Gatsby 5.14.1, React 18.2.0, Material UI (MUI) v7.0.2, Redux Toolkit 2.8.2, react-hook-form v7.55.0, ESLint v7.32.0, Tailwind CSS v4.1.3

2. No lista los componentes dentro de components
── components/          # Componentes de UI reutilizables (wrappers MUI, inputs, tablas)
│   ├── button/          # Botón personalizado con efecto ripple
│   ├── customDatePicker/
│   ├── customSelect/    # Wrapper de Select MUI integrado con react-hook-form
│   ├── genericTable/    # Tabla genérica con paginación
│   ├── googleMapComponent/
│   ├── inputError/      # Muestra mensajes de error de validación de formulario
│   ├── modalComponent/  # Modales de asignación (ModalAgency, ModalCustomer, etc.)

3. No lista las paginas dentro de pageSections
├── pageSections/        # Secciones de página / vistas de funcionalidad
│   ├── login/
│   ├── users/
│   ├── unitsReport/
│   ├── unitsReportDetail/
│   ├── travelsAssignment/
│   ├── appointmentsAssignment/
│   ├── deliverysMonitoring/
│   ├── travelList/
│   ├── travels/
│   ├── travelListCarrier/
│   ├── appointmentListCarrier/

4. No menciona en la estructura a styles/global.sass
├── styles/              # Estilos globales SASS
│   └── global.sass

---

## 2. SKILL.md de la skill creada (Parte B)

> Pega aquí el contenido completo de tu `.claude/skills/<nombre-skill>/SKILL.md`
> (o enlaza al archivo en tu repositorio sandbox).

```markdown
---
name: borrar-ramas
description: Borra ramas locales y remotas de PRs ya mergueados del repositorio
disable-model-invocation: true
allowed-tools: Bash(gh *)
---

# Contexto
- Ramas remotas asociadas a PRs con estatus `merged` existentes en el repositorio
- Ramas locales asociadas a PRs con estatus `merged` existentes en local

# Instrucciones
- Borrar las ramas remotas del contexto
- Borrar las ramas locales del contexto
- Mostrar las ramas remotas y locales borradas
- En caso de no haber ramas remotas borradas mostrar el mensaje `No hay ramas remotas para borrar`
- En caso de no haber ramas locales borradas mostrar el mensaje `No hay ramas locales para borrar`

# Restricciones
- No borrar ramas `default`, `base`, `protected`, `current`
- Borrar solo ramas asociadas a PRs con estatus `merged` existentes
- El borrado debe ser seguro y no forzado
```

---

## 3. Diario de decisiones

*Skill creada:* `borrar-ramas` Borra ramas locales y remotas de PRs ya mergueados del repositorio

*Decisiones de diseño tomadas:*
- Decisión 1: elegir la funcionalidad, repetidamente hacia esto y desde cuando ya queria automatizar esto
- Decisión 2: decidir que instrucciones
- Decisión 3: decidir la secuencia de las instrucciones

*Qué me resultó fácil:*
- escoger la funcionalidad

*Qué me resultó ambiguo o difícil de decidir:*
- las instrucciones, no sabia como plasmar lo que ya tenia en mente

*Tiempo real invertido:*
- 2 horas

*Qué probarías si tuvieras más tiempo:*
- mas escenarios

*¿Usaste IA para crear la skill?* (qué partes generaste con IA y qué partes decidiste tú)
- No

### Resultado de la prueba (Paso 8)

- ¿Se activó cuando lo esperabas?
    - Si
- ¿El resultado fue el que querías?
    - No
- Si no, ¿qué crees que falló? (no la "arregles" — documenta el primer intento)
    - No exclui a las ramas base

- Salida
``` Markdown
Ramas remotas borradas
chore/npm-legacy-peer-deps
docs/yarn-install
fix/cita-detalle-viaje
fix/confirmar-sin-datos
fix/estatus-agendado-reporte
fix/estatus-cita
fix/ocultar-icono-agendar
(origin/develop se excluyó por decisión tuya, al ser una rama base y no una rama de feature)

Ramas locales borradas
No hay ramas locales para borrar
```