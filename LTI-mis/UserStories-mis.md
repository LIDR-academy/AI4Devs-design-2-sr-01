# 🗺️ Roadmap: Diseño de Historias de Usuario y Gestión del Backlog – ATS LTI

## Tabla de Contenidos
- [Objetivos](#objetivos)
- [Definición de Historias de Usuario](#definición-de-historias-de-usuario)
- [Construcción del Backlog de Producto](#construcción-del-backlog-de-producto)
- [Selección de Historia Crítica y Descomposición en Tickets](#selección-de-historia-crítica-y-descomposición-en-tickets)
- [Historias de Usuario Principales](#historias-de-usuario-principales-lti-applicant-tracking-system)
- [Backlog de Producto](#backlog-de-producto)
- [Descomposicion en Tickets – Historia US1](#descomposicion-en-tickets-historia-us1-crear-vacante-desde-panel-de-reclutador)
- [Estrategias de Estimacion](#estrategias-de-estimacion-comparativa-y-recomendacion)
- [Estimacion de Esfuerzo – Historia US1](#estimacion-de-esfuerzo-historia-us1-crear-vacante)
- [Sprint 1 – Crear Vacante](#sprint-1-lti-crear-vacante-desde-el-panel-de-reclutador)


## Objetivos
1. Generar las User Stories
2. Armar el Backlog de producto
3. Elegir la User Story más importante y generar los Tickets de trabajo
4. Estimar el esfuerzo de los tickets de trabajo

[Volver a Tabla de Contenidos](#tabla-de-contenidos)

---

## Definición de Historias de Usuario

**Objetivo:** Extraer funcionalidades clave desde el documento `LTI-mis.md` y redactarlas como User Stories siguiendo las buenas prácticas de `historiasdeusuario.md`.

### Tareas:
- Identificar los actores principales del sistema (Candidato, Reclutador, IA).
- Mapear funcionalidades clave del producto.
- Redactar User Stories con formato clásico:
  > Como [rol], quiero [acción], para [beneficio].
- Añadir criterios de aceptación para cada historia.
- Relacionar historias si están conectadas.

[Volver a Tabla de Contenidos](#tabla-de-contenidos)

---

## Construcción del Backlog de Producto

**Objetivo:** Organizar y priorizar todas las User Stories en una estructura de backlog priorizado.

### Tareas:
- Crear una lista o tabla con las siguientes columnas:
  - Título de la historia
  - Prioridad (Alta / Media / Baja)
  - Esfuerzo estimado (opcional en esta fase)
  - Dependencias
  - Estado (Por hacer, En progreso, Terminado)
- Agrupar historias por épicas o funcionalidades mayores:
  - Publicación de vacantes
  - Procesamiento de postulaciones
  - Gestión de entrevistas
  - Contratación y cierre

[Volver a Tabla de Contenidos](#tabla-de-contenidos)

---

## Selección de Historia Crítica y Descomposición en Tickets

**Objetivo:** Seleccionar la historia de mayor valor y descomponerla en tareas técnicas o tickets de trabajo.

### Tareas:
- Determinar la historia crítica considerando:
  - Valor para el negocio
  - Flujo de usuario

---

# Historias de Usuario Principales LTI Applicant Tracking System

## Épica: Publicación de Vacantes

### 🟢 Historia 1: Crear vacante desde panel de reclutador
**Como** reclutador,  
**quiero** crear y guardar una nueva vacante con detalles del puesto,  
**para que** pueda publicarla en diferentes canales y comenzar el proceso de selección.

**Criterios de Aceptación:**
- Dado que el reclutador accede al panel, cuando hace clic en "Nueva vacante", entonces podrá ingresar título, descripción, ubicación y tipo de contrato.
- Dado que se completa el formulario, cuando hace clic en "Publicar", entonces la vacante debe guardarse y mostrarse en la lista.
- Dado que la vacante se publica, cuando se activa la opción multicanal, entonces se replica automáticamente en portales externos (ej: LinkedIn, Indeed).

---

## Épica: Procesamiento de Postulaciones

### 🟢 Historia 2: Postulación de candidato
**Como** candidato,  
**quiero** enviar mi CV e información personal desde un portal web,  
**para que** pueda ser considerado para una vacante activa.

**Criterios de Aceptación:**
- Dado que el candidato accede a una vacante, cuando hace clic en "Postularme", entonces se despliega un formulario.
- Dado que completa el formulario con nombre, correo y CV, cuando lo envía, entonces la aplicación debe guardarse.
- Dado que se recibe la postulación, cuando se valida la información, entonces debe notificarse al reclutador correspondiente.

---

### 🟢 Historia 3: Evaluar candidatos automáticamente con IA
**Como** reclutador,  
**quiero** recibir un ranking de candidatos basado en el puntaje de su CV,  
**para que** pueda priorizar a los más relevantes rápidamente.

**Criterios de Aceptación:**
- Dado que se recibe una postulación, cuando la IA analiza el CV, entonces se debe generar un score numérico.
- Dado que hay varios candidatos, cuando se visualiza la lista, entonces deben estar ordenados por score descendente.
- Dado que el score no es suficiente, cuando se hace clic en el candidato, entonces se puede ver el análisis detallado del perfil.

---

## Épica: Entrevistas y Pruebas Online

### 🟢 Historia 4: Programar entrevista online
**Como** reclutador,  
**quiero** poder programar una entrevista virtual con un candidato,  
**para que** pueda evaluar sus competencias sin necesidad de presencialidad.

**Criterios de Aceptación:**
- Dado que el candidato ha sido preseleccionado, cuando se hace clic en "Programar entrevista", entonces se debe mostrar un calendario con fechas disponibles.
- Dado que se agenda la entrevista, cuando se confirme, entonces se debe enviar una notificación por correo al candidato.
- Dado que se realiza la entrevista, cuando finaliza, entonces se debe guardar el resultado (apto / no apto / observaciones).

---

### 🟢 Historia 5: Evaluar candidato con prueba técnica
**Como** reclutador,  
**quiero** asignar una prueba técnica en línea al candidato,  
**para que** pueda medir sus habilidades antes de avanzar a la contratación.

**Criterios de Aceptación:**
- Dado que se selecciona una prueba, cuando se asigna a un candidato, entonces se envía automáticamente por correo.
- Dado que el candidato presenta la prueba, cuando finaliza, entonces se debe guardar el resultado con puntaje.
- Dado que se recibe el resultado, cuando el reclutador accede al perfil, entonces puede ver un resumen del rendimiento.

---

## Épica: Contratación y Reportes

### 🟢 Historia 6: Contratar candidato y cerrar vacante
**Como** reclutador,  
**quiero** poder marcar un candidato como contratado,  
**para que** se cierre la vacante y se registre el éxito del proceso.

**Criterios de Aceptación:**
- Dado que un candidato supera todas las etapas, cuando se hace clic en "Contratar", entonces se debe marcar la vacante como cerrada.
- Dado que se contrata al candidato, cuando se registra, entonces se debe guardar la fecha de ingreso y el estado final.
- Dado que se cierra la vacante, cuando se revisa el dashboard, entonces se debe reflejar en las métricas de contratación.

---

### 🟢 Historia 7: Ver métricas en tiempo real
**Como** reclutador,  
**quiero** visualizar métricas como tiempo promedio de contratación y conversión de candidatos,  
**para que** pueda mejorar la eficiencia de mis procesos de selección.

**Criterios de Aceptación:**
- Dado que hay vacantes en curso, cuando se abre el dashboard, entonces debe mostrarse el tiempo promedio de cierre.
- Dado que hay postulaciones activas, cuando se filtra por vacante, entonces se deben mostrar los candidatos convertidos.
- Dado que se necesita analizar, cuando se exportan los datos, entonces se debe generar un archivo Excel o PDF.

---

## 🟢 Historia 8: Registro multicanal de postulaciones
**Como** reclutador,  
**quiero** recibir postulaciones desde diversos canales (LinkedIn, Web, Portales),  
**para que** el sistema centralice todos los candidatos automáticamente.

**Criterios de Aceptación:**
- Dado que una vacante está activa, cuando un candidato aplica desde un canal externo, entonces su aplicación debe registrarse automáticamente en LTI.
- Dado que se identifican duplicados, cuando un candidato ya existe, entonces se debe evitar la creación de registros repetidos.
- Dado que se visualiza la vacante, cuando se accede a postulaciones, entonces debe mostrarse el canal de origen.

---

# Backlog de Producto

> Estado inicial: backlog priorizado, sin esfuerzo aun estimado (eso se hara en el Paso 4)

| ID  | Título                                                   | Épica                         | Prioridad | Dependencias                     | Estado      |
|-----|-----------------------------------------------------------|-------------------------------|-----------|----------------------------------|-------------|
| US1 | Crear vacante desde panel de reclutador                  | Publicación de Vacantes       | Alta      | Ninguna                          | Por hacer   |
| US2 | Postulación de candidato                                 | Procesamiento de Postulaciones| Alta      | US1                              | Por hacer   |
| US3 | Evaluar candidatos automáticamente con IA                | Procesamiento de Postulaciones| Alta      | US2                              | Por hacer   |
| US4 | Programar entrevista online                              | Entrevistas y Pruebas Online  | Media     | US3                              | Por hacer   |
| US5 | Evaluar candidato con prueba técnica                     | Entrevistas y Pruebas Online  | Media     | US3                              | Por hacer   |
| US6 | Contratar candidato y cerrar vacante                     | Contratación y Reportes       | Alta      | US4, US5                         | Por hacer   |
| US7 | Ver métricas en tiempo real                              | Contratación y Reportes       | Baja      | US6                              | Por hacer   |
| US8 | Registro multicanal de postulaciones                     | Procesamiento de Postulaciones| Media     | US1                              | Por hacer   |

---

## Agrupación por Épicas

### 📌 Publicación de Vacantes
- US1: Crear vacante desde panel de reclutador

### 📌 Procesamiento de Postulaciones
- US2: Postulación de candidato
- US3: Evaluar candidatos automáticamente con IA
- US8: Registro multicanal de postulaciones

### 📌 Entrevistas y Pruebas Online
- US4: Programar entrevista online
- US5: Evaluar candidato con prueba técnica

### 📌 Contratación y Reportes
- US6: Contratar candidato y cerrar vacante
- US7: Ver métricas en tiempo real

---

## 🗂️ Consideraciones

- Se considera **crítica la historia US1 (Crear vacante)** como punto de partida funcional.
- Las historias US2 y US3 completan el **flujo mínimo viable** para iniciar la operación básica.
- Las historias US4 y US5 pueden trabajarse en paralelo si los módulos de entrevistas y pruebas están desacoplados.

[Volver a Tabla de Contenidos](#tabla-de-contenidos)

---

# Descomposicion en Tickets Historia US1: Crear vacante desde panel de reclutador

> Historia de Usuario Base:
> **Como** reclutador,  
> **quiero** crear y guardar una nueva vacante con detalles del puesto,  
> **para que** pueda publicarla en diferentes canales y comenzar el proceso de seleccion.

---

## 🎨 Tareas de UI/UX

### 🟡 TKT-01: Diseñar formulario para creación de vacante
- Diseñar interfaz con campos: título, descripción, ubicación, tipo de contrato, fecha límite.
- Validación básica de campos obligatorios.
- UX intuitiva y responsive.

### 🟡 TKT-02: Implementar pantalla de resumen/listado de vacantes creadas
- Mostrar vacantes del usuario actual con estado (borrador/publicado).
- Opción de editar y eliminar.

---

## 🛠️ Tareas de Backend/API

### 🔵 TKT-03: Crear endpoint REST POST `/jobs` para registrar una nueva vacante
- Validaciones de esquema.
- Guardado en base de datos.
- Asociar ID del reclutador.

### 🔵 TKT-04: Crear endpoint GET `/jobs` para recuperar vacantes del reclutador
- Filtrado por estado.
- Soporte para paginación y ordenamiento.

### 🔵 TKT-05: Crear lógica de validación y sanitización de datos del formulario
- Campos requeridos.
- Longitudes máximas.
- Validación semántica (ej. fechas futuras).

---

## 🗃️ Tareas de Base de Datos

### 🔴 TKT-06: Crear tabla `JOB` y modelo ORM correspondiente
- Campos: id, title, description, location, contract_type, created_at, status, recruiter_id.
- FK hacia tabla `RECRUITER`.

---

## 🔗 Tareas de Integración

### 🟣 TKT-07: Conectar publicación automática en portales externos (simulación)
- Simular integración con LinkedIn / Indeed.
- Mostrar notificación de éxito o error.

---

## ✅ Tareas de QA y Validación

### 🟢 TKT-08: Escribir pruebas unitarias para validación del formulario
- Comprobación de reglas de negocio.

### 🟢 TKT-09: Escribir pruebas de integración para creación de vacante vía API
- Validación de respuesta esperada, código HTTP, errores comunes.

### 🟢 TKT-10: Validación end-to-end del flujo de creación → publicación
- Prueba funcional con interfaz + backend + base de datos.

---

## 📋 Resumen de Tickets Generados

| ID       | Descripción                                              | Tipo           |
|----------|----------------------------------------------------------|----------------|
| TKT-01   | Diseñar formulario de creación de vacante                | UI/UX          |
| TKT-02   | Implementar listado de vacantes creadas                  | UI/UX          |
| TKT-03   | Endpoint POST `/jobs` para crear vacante                 | Backend/API    |
| TKT-04   | Endpoint GET `/jobs` para listar vacantes                | Backend/API    |
| TKT-05   | Validaciones de datos en backend                         | Backend/API    |
| TKT-06   | Creación de tabla JOB y modelo ORM                       | Base de datos  |
| TKT-07   | Integración simulada con portales externos               | Integración    |
| TKT-08   | Pruebas unitarias de validación de formulario            | QA             |
| TKT-09   | Pruebas de integración para creación de vacante          | QA             |
| TKT-10   | Pruebas end-to-end del flujo completo                    | QA             |

[Volver a Tabla de Contenidos](#tabla-de-contenidos)

---

# Estrategias de Estimacion Comparativa y Recomendacion

## 📊 Comparación de Estrategias de Estimación

| Estrategia                     | Precisión         | Velocidad         | Ideal para                           | Comentario clave                                                  |
|-------------------------------|-------------------|-------------------|--------------------------------------|-------------------------------------------------------------------|
| **Fibonacci (Story Points)**  | Alta en agilidad  | Media             | Equipos Scrum, planificación iterativa | Buena para medir *complejidad relativa* e incertidumbre. No traduce directamente en horas. |
| **Tallas de camiseta (XS–XL)**| Media             | Alta              | Primeros sprints, MVP, poca info técnica | Rápida, visual y útil para comparar tareas sin sobreanalizar.     |
| **Horas Hombre**              | Alta (aparente)   | Baja              | Planificación de cronogramas, contratos | Puede ser engañosa si hay incertidumbre. Genera falsa sensación de exactitud en fases tempranas. |

---

## ✅ Recomendación

### 🎯 Estrategia sugerida: **Tallas de camiseta (XS, S, M, L, XL)**

### 💡 Justificación:

1. **Estamos en etapa temprana** del desarrollo del producto.
2. **Los tickets son funcionales y modulares**, fácilmente clasificables sin sobreanálisis.
3. **Evita sobreplanificación temprana**, manteniendo agilidad sin comprometer el roadmap.
4. **Escalable y adaptable**, puedes traducir luego a puntos de historia o tiempo si lo necesitas.

[Volver a Tabla de Contenidos](#tabla-de-contenidos)

---

# Estimacion de Esfuerzo Historia US1 (Crear vacante)

> Método de estimación: **Tallas de camiseta**
> Criterios considerados: complejidad técnica, nivel de incertidumbre, dependencia externa, esfuerzo esperado.

| ID       | Descripción                                              | Tipo           | Talla Estimada |
|----------|----------------------------------------------------------|----------------|----------------|
| TKT-01   | Diseñar formulario de creación de vacante                | UI/UX          | S              |
| TKT-02   | Implementar listado de vacantes creadas                  | UI/UX          | M              |
| TKT-03   | Endpoint POST `/jobs` para crear vacante                 | Backend/API    | M              |
| TKT-04   | Endpoint GET `/jobs` para listar vacantes                | Backend/API    | M              |
| TKT-05   | Validaciones de datos en backend                         | Backend/API    | S              |
| TKT-06   | Creación de tabla JOB y modelo ORM                       | Base de datos  | S              |
| TKT-07   | Integración simulada con portales externos               | Integración    | L              |
| TKT-08   | Pruebas unitarias de validación de formulario            | QA             | XS             |
| TKT-09   | Pruebas de integración para creación de vacante          | QA             | S              |
| TKT-10   | Pruebas end-to-end del flujo completo                    | QA             | M              |

---

## 🧠 Observaciones Generales

- La tarea **TKT-07** se considera más compleja por la simulación de integración con terceros, por eso tiene talla **L**.
- Las tareas de pruebas han sido desglosadas y clasificadas según su alcance.
- La combinación de tareas S/M permitiría ejecutar varias en paralelo si hay más de un desarrollador.

[Volver a Tabla de Contenidos](#tabla-de-contenidos)

---

# Sprint 1 LTI Crear Vacante desde el Panel de Reclutador

> Objetivo del Sprint: Implementar el flujo completo para permitir a los reclutadores crear, listar y publicar vacantes desde el sistema LTI.

## 📅 Duración sugerida: 2 semanas

---

## ✅ Historias de Usuario incluidas
- **US1**: Como reclutador, quiero crear y guardar una nueva vacante con detalles del puesto, para que pueda publicarla en diferentes canales y comenzar el proceso de selección.

---

## 📋 Tickets del Sprint

| ID       | Descripción                                              | Tipo           | Talla Estimada | Responsable | Estado Inicial |
|----------|----------------------------------------------------------|----------------|----------------|-------------|----------------|
| TKT-01   | Diseñar formulario de creación de vacante                | UI/UX          | S              | UI/UX Lead   | Por hacer       |
| TKT-02   | Implementar listado de vacantes creadas                  | UI/UX          | M              | UI Dev       | Por hacer       |
| TKT-03   | Endpoint POST `/jobs` para crear vacante                 | Backend/API    | M              | Backend Dev  | Por hacer       |
| TKT-04   | Endpoint GET `/jobs` para listar vacantes                | Backend/API    | M              | Backend Dev  | Por hacer       |
| TKT-05   | Validaciones de datos en backend                         | Backend/API    | S              | Backend Dev  | Por hacer       |
| TKT-06   | Creación de tabla JOB y modelo ORM                       | Base de datos  | S              | DB Engineer  | Por hacer       |
| TKT-07   | Integración simulada con portales externos               | Integración    | L              | Backend Dev  | Por hacer       |
| TKT-08   | Pruebas unitarias de validación de formulario            | QA             | XS             | QA Engineer  | Por hacer       |
| TKT-09   | Pruebas de integración para creación de vacante          | QA             | S              | QA Engineer  | Por hacer       |
| TKT-10   | Pruebas end-to-end del flujo completo                    | QA             | M              | QA Engineer  | Por hacer       |

---

## 📦 Criterio de Éxito del Sprint
- El reclutador puede:
  - Iniciar sesión (simulado)
  - Crear una vacante desde un formulario
  - Ver el listado de vacantes creadas
  - Ver mensaje de publicación simulada en portales externos

- Toda la funcionalidad está validada con pruebas unitarias e integración.
- El flujo de principio a fin es testeable y navegable.

---

## 🚧 Riesgos a Considerar
- Integración externa simulada puede requerir cambios de diseño posterior.
- La validación y el modelo de datos deben definirse de forma consistente para futuras historias.

---

## 🛠 Herramientas sugeridas
- **Frontend**: React / Vue / HTML con Tailwind
- **Backend**: Node.js con Express o Python FastAPI
- **Base de Datos**: PostgreSQL (modelo ya definido)
- **Testing**: Jest / Pytest / Postman
- **Gestión**: Jira / Notion / Trello

[Volver a Tabla de Contenidos](#tabla-de-contenidos)

---



