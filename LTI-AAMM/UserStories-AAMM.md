# Historias de Usuario – LTI ATS

## Objetivo del Producto

Crear una plataforma SaaS de reclutamiento inteligente que combine automatización con inteligencia artificial y colaboración en tiempo real para facilitar todo el ciclo de atracción y selección de talento.

---

## User Stories

### US1 – Publicación Centralizada de Vacantes

Como reclutador, quiero crear y publicar vacantes en múltiples plataformas desde un solo lugar, para ahorrar tiempo y mantener una gestión centralizada.

Criterios de Aceptación:
	•	La vacante debe incluir campos como título, descripción, requisitos y beneficios.
	•	Debe permitirse seleccionar uno o varios canales de publicación externos.
	•	La publicación debe reflejarse correctamente en plataformas como LinkedIn o portales corporativos.
	•	El estado de la vacante debe poder cambiar entre “abierta”, “pausada” y “cerrada”.

---

### US2 – Evaluación Colaborativa de Candidatos

Como hiring manager, quiero poder ver y comentar los perfiles de candidatos compartidos por el reclutador, para colaborar en su evaluación de manera eficiente.

Criterios de Aceptación:
	•	Debe poderse acceder a una lista de candidatos compartidos.
	•	El sistema debe permitir agregar comentarios y una calificación numérica de 1 a 5.
	•	Los comentarios deben ser visibles para todos los evaluadores del proceso.
	•	Se debe registrar el historial de interacciones para trazabilidad.

---

### US3 – Priorización de Candidatos con IA

Como reclutador, quiero recibir una lista de candidatos priorizada por IA, para enfocarme solo en los perfiles más prometedores.

Criterios de Aceptación:
	•	El sistema debe procesar automáticamente los CVs recibidos.
	•	Se debe generar un puntaje IA visible en cada perfil.
	•	Los criterios de evaluación deben incluir habilidades, experiencia, y fit cultural.
	•	El usuario debe poder aceptar, rechazar o marcar para revisión manual desde la lista priorizada.

---

### US4 – Registro de Evaluaciones y Auditoría

Como usuario del sistema, quiero que todas las acciones (comentarios, evaluaciones, decisiones) queden registradas con trazabilidad, para garantizar transparencia y cumplimiento.

Criterios de Aceptación:
	•	Cada evaluación debe tener timestamps y versionado.
	•	El sistema debe generar eventos de auditoría (evaluation.created, evaluation.updated).
	•	Los cambios deben poder ser consultados por administradores en un historial.

---

### US5 – Colaboración en Tiempo Real

Como miembro del equipo de reclutamiento, quiero poder interactuar en tiempo real con mis colegas dentro de la plataforma, para evitar retrasos en la toma de decisiones.

Criterios de Aceptación:
	•	Deben activarse notificaciones automáticas al compartir un candidato o recibir feedback.
	•	Las actualizaciones deben reflejarse instantáneamente mediante WebSockets.
	•	Los comentarios en evaluaciones deben aparecer sin necesidad de recargar la página.


# 📝 Backlog de Producto – LTI ATS

## Criterios de Priorización

Las historias se ordenan con base en:
	•	Valor de negocio directo (impacto en reclutadores y adopción temprana).
	•	Viabilidad técnica inmediata (según arquitectura y componentes descritos).
	•	Diferenciadores clave frente a ATS tradicionales.

## Mapa de Historias de Usuario
### Mapa de Historias de Usuario [Mapa de Historias](./imagenes/mapa%20de%20historias%20de%20usuario.png)    

## Sprint 1 (MVP) – Alta Prioridad

### US1 – Publicación Centralizada de Vacantes
- Implementar interfaz para creación de vacantes.
- Soporte para publicar en LinkedIn y portales personalizados vía API.
- Gestión del estado de vacantes (abierta, pausada, cerrada).
- Recepción de postulaciones integradas en el sistema.

### US2 – Evaluación Colaborativa de Candidatos
- Comentarios abiertos y puntuación (1-5) visibles entre reclutadores y managers.
- Compartición de perfiles y notificaciones de actividad.
- Acceso unificado al historial de evaluaciones por candidato.

### US3 – Priorización de Candidatos con IA
- Integración del módulo de IA para procesar CVs entrantes.
- Scoring basado en criterios definidos por reclutador.
- Visualización de candidatos ordenados por puntaje IA.

### US4 – Registro de Evaluaciones y Auditoría
- Eventos `evaluation.created` y `evaluation.updated`.
- Registro de versiones con timestamp por evaluación.
- Historial auditable accesible por administrador.

### US5 – Colaboración en Tiempo Real
- WebSocket para notificaciones en vivo de cambios en evaluaciones.
- Actualización automática de vista al recibir nuevos comentarios.
- Visualización de indicadores de “usuario está evaluando”.

---

## Sprint 2 – Iteración Media

### US6 – Personalización de Criterios de IA
- Interfaz para definir ponderaciones personalizadas en el algoritmo.
- Guardado de presets por usuario o equipo.

### US7 – Visualización de Historial de Feedback
- Timeline con cambios de evaluación y comentarios por candidato.
- Comparación de versiones.

### US8 – Exportación de Reportes de Evaluación
- Exportar a CSV o PDF desde módulo de candidatos/evaluaciones.
- Selección de campos relevantes.

---

## Sprint 3 – Funcionalidades Futuras / Avanzadas

### US9 – Entrenamiento Personalizado del Motor de IA
- Adaptación del modelo basado en decisiones pasadas.
- Aprendizaje supervisado con retroalimentación de los usuarios.

### US10 – Modo Colaborativo Simultáneo
- Edición en tiempo real de notas evaluativas (tipo Google Docs).
- Visualización de cursores de otros usuarios.

### US11 – Integración con Cumplimiento Legal (GDPR/EEOC)
- Borrado automático de datos sensibles tras tiempo definido.
- Consentimiento del candidato desde interfaz pública.

# Historia de Usuario: US3 – Priorización de Candidatos con IA

Como reclutador, quiero recibir una lista de candidatos priorizada por IA, para enfocarme solo en los perfiles más prometedores.

---

# Tickets Técnicos – Sprint Breakdown

## Epic: IA para Priorización de Candidatos

---

### TICKET 1 – Definir modelo de scoring IA basado en criterios reclutadores

- **Tipo:** Spike técnico / Backend  
- **Tareas:**
  - Documentar criterios base: habilidades, experiencia, cultura, seniority.
  - Estructurar `JobCriteriaProfile` para alimentar el modelo.
  - Definir reglas de ponderación personalizables.
- **Resultado esperado:** Documento técnico + estructura de entrada lista para desarrollo.

---

### TICKET 2 – Implementar motor de scoring semántico (NLP)

- **Tipo:** Backend / IA  
- **Tareas:**
  - Integrar librerías NLP (ej. spaCy, HuggingFace Transformers).
  - Extraer entidades clave desde CVs (skills, experiencia, tecnologías).
  - Calcular match score con la vacante objetivo.
- **Endpoint sugerido:** `POST /ai/score-candidate`  
- **Resultado esperado:** JSON con score IA por candidato.

---

### TICKET 3 – Endpoint REST para consumir lista priorizada

- **Tipo:** Backend  
- **Tareas:**
  - Crear endpoint `GET /jobs/{id}/ranked-candidates`
  - Implementar paginación y filtros.
  - Consultar `Applications` ordenadas por `puntaje_ia`.
- **Resultado esperado:** Lista paginada con puntaje IA y metadatos del candidato.

---

### TICKET 4 – Persistencia del puntaje IA en la base de datos

- **Tipo:** Backend / Data Layer  
- **Tareas:**
  - Agregar campo `puntaje_ia` al modelo `Application` (tipo `float`).
  - Crear migración SQL correspondiente.
  - Asegurar actualización tras scoring.
- **Resultado esperado:** Puntaje IA persistido y actualizado correctamente.

---

### TICKET 5 – Componente UI: Lista de candidatos priorizados

- **Tipo:** Frontend (React)  
- **Tareas:**
  - Crear componente `RankedCandidateList`.
  - Mostrar nombre, puntaje IA, fuente de aplicación, y acciones rápidas (avanzar, rechazar, revisar).
  - Visualización gráfica del score (barra de color o ícono).
- **Resultado esperado:** Componente funcional integrado al frontend.

---

### TICKET 6 – Validación manual y override de puntaje IA

- **Tipo:** Frontend + Backend  
- **Tareas:**
  - Agregar opción para editar score desde la UI (modal).
  - Endpoint: `PUT /applications/{id}/manual-score`
  - Registrar motivo del cambio.
- **Resultado esperado:** Puntaje modificado manualmente queda guardado y auditado.

---

### TICKET 7 – Notificaciones en tiempo real de nuevos candidatos con alto score

- **Tipo:** Backend + Tiempo real  
- **Tareas:**
  - Emitir evento WebSocket cuando un nuevo score supere el umbral (ej. 80+).
  - Canal: `job_room_{jobId}`.
  - Mensaje: “Nuevo candidato destacado: {nombre} – Score: {valor}”.
- **Resultado esperado:** Mensaje en vivo recibido por frontend.

---

### TICKET 8 – Testing E2E del flujo de ranking IA

- **Tipo:** QA / Automatización  
- **Tareas:**
  - Generar fixtures de candidatos y vacantes.
  - Validar el cálculo de scores y el orden de presentación.
  - Probar edición manual + sincronización en tiempo real.
- **Resultado esperado:** Pruebas funcionales completas y automatizadas.

---


# Estimación de Esfuerzo – US3: Priorización de Candidatos con IA

Estimación en horas hombre, aplicando metodología tipo Planning Poker adaptada a esfuerzo individual.

---

## Detalle por Ticket
### Detalle [Detalle](./imagenes/detalle%20tikets.png)    

---

## Resumen

- **Total estimado:** `70 horas hombre`

### Distribución aproximada por rol:

- **Backend:** 38 h
- **Frontend:** 20 h
- **QA / Testing:** 10 h
- **Spike / Análisis técnico:** 6 h (complementarias)

---

## Recomendaciones

- Ideal para sprint de 5 días con equipo de 3 personas (frontend, backend, QA).
- Puede dividirse en 2 entregas: motor de IA + integración visual.