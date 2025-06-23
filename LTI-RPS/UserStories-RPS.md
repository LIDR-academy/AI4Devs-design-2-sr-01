# User Story – Gestión centralizada de candidatos

**Como** recruiter o hiring manager,  
**quiero** visualizar, filtrar y gestionar todos los candidatos en un pipeline centralizado y personalizable,  
**para que pueda** organizar eficientemente el proceso de selección, acceder a información completa de cada candidato y facilitar la colaboración con el equipo:contentReference[oaicite:0]{index=0}.

## Caso de Uso: Gestión centralizada de candidatos

### 1. Descripción General

**Propósito:**  
Permitir a los usuarios responsables de selección (recruiters y hiring managers) gestionar y organizar candidatos en un pipeline centralizado y configurable, facilitando el acceso a información detallada de cada perfil, el cambio de estado en el proceso de selección y la colaboración con el equipo:contentReference[oaicite:0]{index=0}.

**Alcance:**  
Módulo de gestión de candidatos / Proceso de selección.

**Actores principales:**
- Recruiter
- Hiring Manager
- Sistema LTI (automatizaciones y notificaciones)

**Precondiciones:**
- El usuario debe tener credenciales válidas y acceso al módulo de gestión de procesos de selección.
- Deben existir procesos de selección activos y candidatos registrados en el sistema.

**Postcondiciones:**
- Los candidatos pueden haber cambiado de estado en el pipeline.
- Se actualiza el historial y se notifican los cambios a los actores implicados.
- La información y actividades de cada candidato quedan centralizadas y actualizadas en su perfil.

---

### 2. Flujo Principal (Camino Feliz)

1. El recruiter/hiring manager accede al pipeline de un proceso de selección.
2. Visualiza la lista de candidatos organizados por etapas del proceso (ej. nuevo, en revisión, entrevista, oferta, rechazado).
3. Utiliza filtros o búsqueda avanzada para localizar candidatos por nombre, estado, puntuación IA, tags o fuente de reclutamiento.
4. Selecciona un candidato específico y accede a su perfil unificado.
5. Revisa los datos personales, CV y documentos adjuntos, historial de actividades, evaluaciones de entrevistas y notas asociadas.
6. Cambia el estado del candidato en el pipeline (por ejemplo, de “en revisión” a “entrevista”).
7. Añade comentarios o asigna tareas relacionadas a otros miembros del equipo.
8. El sistema LTI registra las acciones, actualiza el historial del candidato y notifica automáticamente a los actores relevantes (equipo y candidato, según configuración).

---

### 3. Flujos Alternativos

- El candidato es movido automáticamente a una etapa superior tras recibir una puntuación IA elevada.
- El sistema detecta duplicados y propone fusión o limpieza de candidatos.
- El recruiter marca a un candidato como “stand-by” para futuras oportunidades, sin sacarlo del sistema.

---

### 4. Flujos de Excepción (Errores)

- El usuario no tiene permisos suficientes para mover candidatos de etapa: el sistema bloquea la acción y muestra un mensaje de error.
- El candidato seleccionado no existe o ha sido archivado: el sistema muestra una alerta y retorna al pipeline.
- Error de comunicación con servicios externos (ej. integración de calendario): el sistema informa del fallo y permite reintentar la acción.
- Intento de eliminación directa de candidato: el sistema informa que solo se puede archivar o marcar como duplicado.

---

### 5. Requisitos Técnicos

**Requisitos funcionales:**
- Visualización de pipeline centralizado y configurable por etapas.
- Búsqueda y filtrado avanzado de candidatos.
- Acceso a perfil unificado de candidato con historial completo.
- Cambio de estado y registro en historial.
- Posibilidad de añadir comentarios y asignar tareas.
- Notificaciones automáticas a actores implicados.
- Registro de acciones para auditoría.

---

### 6. Criterios de Validación (Pruebas del Desarrollo)

**Pruebas técnicas:**
- Validar que todos los candidatos del proceso aparecen en el pipeline correspondiente.
- Confirmar la correcta visualización de datos en el perfil del candidato.
- Verificar el funcionamiento de los filtros y búsquedas avanzadas.
- Confirmar que el cambio de estado de un candidato actualiza el historial y dispara notificaciones apropiadas.
- Probar que los comentarios y tareas quedan registrados y accesibles en el perfil del candidato.

**Pruebas de integración:**
- Validar la integración con servicios externos de notificaciones y calendarios.
- Comprobar que la automatización de movimientos por IA funciona correctamente.

---

### 7. Definition of Done

- Todos los flujos principales, alternativos y de excepción están implementados y probados.
- Se cumplen los requisitos técnicos y funcionales definidos.
- La visualización y filtrado de candidatos es clara, eficiente y robusta.
- Todas las acciones relevantes quedan registradas para auditoría.
- El sistema notifica correctamente a todos los actores implicados.
- Documentación de usuario y técnica actualizada.
- Pruebas automatizadas (unitarias y de integración) superadas con éxito.
- Estimación: **8 Story Points**.

---

# User Story – IA en el proceso de selección

**Como** recruiter o hiring manager,  
**quiero** aprovechar la inteligencia artificial para analizar currículums, generar rankings de candidatos y recibir sugerencias automatizadas,  
**para que pueda** optimizar la toma de decisiones, identificar perfiles compatibles de manera más eficiente y automatizar la redacción de feedback y preguntas de entrevista:contentReference[oaicite:0]{index=0}.

## Caso de Uso: IA en el proceso de selección

### 1. Descripción General

**Propósito:**  
Permitir a los recruiters y hiring managers optimizar y acelerar el proceso de selección mediante la aplicación de algoritmos de inteligencia artificial, que analizan currículums, generan rankings automáticos de candidatos, sugieren perfiles compatibles y asisten en la redacción de evaluaciones, feedbacks y preguntas de entrevista:contentReference[oaicite:0]{index=0}.

**Alcance:**  
Módulo de selección asistida por IA.

**Actores principales:**
- Recruiter
- Hiring Manager
- Sistema LTI (IA)

**Precondiciones:**
- El usuario debe estar autenticado y tener acceso al módulo de selección.
- Existen candidatos registrados y ofertas de empleo activas en el sistema.
- Los candidatos cuentan con currículums y datos estructurados suficientes para análisis IA.

**Postcondiciones:**
- Los candidatos han sido puntuados y ordenados en un ranking.
- El sistema ha generado y mostrado sugerencias y textos asistidos para los usuarios.
- Se registra toda intervención y edición realizada sobre los resultados automáticos.

---

### 2. Flujo Principal (Camino Feliz)

1. Un nuevo candidato aplica a una oferta o es agregado al sistema.
2. El sistema analiza automáticamente su currículum y lo compara con:
    - Los requisitos del puesto.
    - El historial de candidatos exitosos previos.
    - Palabras clave y experiencia relevante.
3. El candidato es puntuado y ubicado en un ranking automatizado para esa oferta.
4. El recruiter accede al panel de IA y revisa el ranking generado.
5. El sistema sugiere perfiles adicionales en la base de datos compatibles con la oferta.
6. El recruiter selecciona uno o varios candidatos del ranking o sugeridos.
7. El sistema asiste en la generación de preguntas de entrevista personalizadas y feedback preliminar.
8. El recruiter o hiring manager revisa y edita los textos generados antes de utilizarlos o enviarlos.

---

### 3. Flujos Alternativos

- El sistema detecta que un nuevo candidato supera a los existentes y lo destaca con una alerta prioritaria.
- El recruiter puede reentrenar el modelo de IA introduciendo feedback y decisiones recientes para mejorar su precisión futura.
- El sistema sugiere ajustes en la descripción del puesto si detecta incoherencias entre los candidatos mejor posicionados y el perfil buscado.

---

### 4. Flujos de Excepción (Errores)

- El candidato no cuenta con información suficiente para ser analizado por la IA: el sistema alerta al usuario y sugiere completar los datos.
- Error en el procesamiento IA (por carga excesiva, fallo de servicio, etc.): el sistema informa del incidente y permite reintentar o continuar el proceso de manera manual.
- Las recomendaciones de la IA son incoherentes: el usuario puede desestimar sugerencias y reportar incidencias para revisión técnica.

---

### 5. Requisitos Técnicos

**Requisitos funcionales:**
- Procesamiento automático de currículums y comparación con requisitos.
- Generación y visualización de rankings de candidatos.
- Sugerencia automatizada de perfiles compatibles en la base de datos.
- Generación asistida de preguntas de entrevista y feedback.
- Registro de todas las acciones e intervenciones manuales sobre los resultados automáticos.
- Capacidad de aprendizaje de la IA a partir del feedback recibido.

---

### 6. Criterios de Validación (Pruebas del Desarrollo)

**Pruebas técnicas:**
- Verificar que el sistema analiza y puntúa los currículums correctamente frente a diferentes perfiles de oferta.
- Comprobar la exactitud y utilidad del ranking y las sugerencias de perfiles compatibles.
- Validar la generación automática de textos (preguntas y feedback) y su edición posterior.
- Probar la capacidad de registrar y auditar todas las intervenciones manuales.

**Pruebas de integración:**
- Validar la integración entre el módulo de IA, la base de datos de candidatos y el frontend del usuario.
- Probar la interoperabilidad con otros módulos como notificaciones y reporting.

---

### 7. Definition of Done

- Todos los flujos principales, alternativos y de excepción implementados y probados.
- Cumplimiento de requisitos funcionales y técnicos.
- Rankings y sugerencias IA accesibles y comprensibles para los usuarios.
- Edición y registro de feedback y preguntas generadas asistidas por IA.
- Sistema auditable y documentado.
- Pruebas automatizadas (unitarias e integración) superadas con éxito.
- Estimación: **13 Story Points**.

---

# User Story – Experiencia del candidato

**Como** candidato,  
**quiero** acceder a un portal donde pueda seguir el estado de mi postulación, recibir notificaciones personalizadas y completar encuestas de satisfacción,  
**para que pueda** tener visibilidad y control sobre el proceso de selección, recibir información clara y aportar feedback que ayude a mejorar mi experiencia:contentReference[oaicite:0]{index=0}.

## Caso de Uso: Experiencia del candidato

### 1. Descripción General

**Propósito:**  
Ofrecer a los candidatos un portal moderno y accesible para hacer seguimiento de su postulación, recibir notificaciones claras y personalizadas sobre el estado de su proceso y participar en encuestas automáticas de satisfacción, mejorando así la transparencia y la calidad de la experiencia durante el proceso de selección:contentReference[oaicite:0]{index=0}.

**Alcance:**  
Módulo de portal del candidato y comunicaciones personalizadas.

**Actores principales:**
- Candidato
- Recruiter
- Sistema LTI

**Precondiciones:**
- El candidato ha sido registrado en el sistema y tiene una postulación activa o ha sido invitado a un proceso.
- Existen ofertas y procesos de selección activos configurados para la interacción con el portal del candidato.

**Postcondiciones:**
- El candidato ha accedido al portal, visualizado su estado y recibido notificaciones personalizadas.
- El candidato puede haber subido documentación adicional y/o completado encuestas de satisfacción.
- Las respuestas de feedback quedan registradas y accesibles para los recruiters.

---

### 2. Flujo Principal (Camino Feliz)

1. El candidato aplica a una oferta o es invitado formalmente a un proceso de selección.
2. El sistema crea automáticamente un perfil visible en el portal del candidato.
3. El candidato accede al portal, donde puede:
   - Visualizar el estado actual de su postulación.
   - Revisar los siguientes pasos previstos en el proceso.
   - Subir documentación adicional si se solicita.
4. Conforme el proceso avanza, el sistema envía notificaciones personalizadas, incluyendo:
   - Confirmación de recepción de candidatura.
   - Convocatorias a entrevistas o pruebas.
   - Cambios de estado relevantes (avance, rechazo, oferta).
5. Al finalizar el proceso, el sistema envía una encuesta automática de satisfacción al candidato.
6. Las respuestas a la encuesta son recogidas y quedan accesibles para el equipo de reclutamiento para su análisis y mejora del proceso.

---

### 3. Flujos Alternativos

- El candidato accede al portal mediante un enlace directo sin haber sido invitado formalmente; el sistema le guía a través de un proceso seguro de autenticación.
- El candidato no responde a una notificación; el sistema reenvía recordatorios automáticos hasta un límite configurado.
- Si el candidato completa una encuesta con feedback negativo, se genera una alerta para revisión manual por parte del equipo de reclutamiento.

---

### 4. Flujos de Excepción (Errores)

- El candidato intenta acceder al portal con credenciales inválidas o enlace caducado: el sistema informa del error y ofrece opciones de recuperación o contacto.
- Error en la entrega de notificaciones (por ejemplo, email no entregado): el sistema lo registra y permite reintentar el envío.
- El candidato no completa la encuesta: el sistema registra la ausencia, pero no bloquea el acceso a futuras funcionalidades.

---

### 5. Requisitos Técnicos

**Requisitos funcionales:**
- Creación y acceso seguro al portal del candidato.
- Visualización clara y actualizada del estado del proceso.
- Envío y gestión de notificaciones personalizadas por múltiples canales.
- Posibilidad de subida de documentación adicional.
- Envío automático y recogida de encuestas de satisfacción.
- Registro y acceso a los resultados de feedback por parte del equipo de reclutamiento.
- Cumplimiento de normativa RGPD y consentimiento para el uso de datos.

---

### 6. Criterios de Validación (Pruebas del Desarrollo)

**Pruebas técnicas:**
- Validar que los candidatos pueden acceder correctamente al portal con diferentes escenarios de invitación.
- Confirmar la visualización y actualización del estado del proceso en tiempo real.
- Verificar la correcta entrega de notificaciones personalizadas (email, in-app, push).
- Comprobar la funcionalidad de subida de documentos adicionales.
- Validar el envío y recogida de encuestas de satisfacción y el acceso de los recruiters a los resultados.

**Pruebas de integración:**
- Probar la integración del portal del candidato con el backend, módulo de notificaciones y base de datos.
- Comprobar la interoperabilidad entre las encuestas, el registro de feedback y los informes de calidad del proceso.

---

### 7. Definition of Done

- Todos los flujos principales, alternativos y de excepción están implementados y probados.
- Cumplimiento de requisitos técnicos y funcionales.
- El portal es accesible, seguro y amigable para el candidato.
- Las notificaciones y encuestas funcionan correctamente y los resultados son accesibles para recruiters.
- Cumplimiento de la normativa de protección de datos (RGPD).
- Pruebas automatizadas y documentación completadas.
- Estimación: **8 Story Points**.

---

# Backlog de Tickets – LTI Plataforma de Gestión de Talento

## Épica 1: Gestión centralizada de candidatos

### Frontend

- **Ticket 1.1:** Maquetación del pipeline visual de candidatos (por etapas del proceso)
   - Desarrollar vista de pipeline configurable y responsive para visualizar candidatos por estado.
   - **Story Points:** 5

- **Ticket 1.2:** Implementación de filtros y búsqueda avanzada en la vista de pipeline
   - Filtros por nombre, estado, puntuación IA, tags, fuente.
   - **Story Points:** 3

- **Ticket 1.3:** Perfil unificado del candidato
   - Maquetar y desarrollar el perfil de candidato: datos personales, CV, historial, evaluaciones y comentarios.
   - **Story Points:** 3

- **Ticket 1.4:** UI para cambio de estado de candidato en el pipeline
   - Interfaz para mover candidatos entre etapas con retroalimentación visual.
   - **Story Points:** 2

- **Ticket 1.5:** Sección de comentarios y tareas colaborativas
   - Maquetación de comentarios y sistema de asignación de tareas dentro del perfil del candidato.
   - **Story Points:** 2

### Backend

- **Ticket 1.6:** API para gestión de candidatos y pipeline
   - CRUD candidatos, definición de etapas, cambio de estado, registro en historial.
   - **Story Points:** 5

- **Ticket 1.7:** API de búsqueda y filtrado avanzado
   - Endpoints para búsqueda multifiltro y paginada.
   - **Story Points:** 3

- **Ticket 1.8:** Lógica de automatización de cambios por IA y reglas de negocio
   - Mover candidatos automáticamente, detección de duplicados, “stand-by”, restricciones de permisos.
   - **Story Points:** 5

- **Ticket 1.9:** Registro de acciones y auditoría en el historial de candidatos
   - Log completo de movimientos, acciones y comentarios.
   - **Story Points:** 2

### Integración

- **Ticket 1.10:** Integración frontend-backend para visualización y acciones en el pipeline
   - Conexión de las vistas del frontend con APIs para CRUD, filtros, comentarios y cambios de estado.
   - **Story Points:** 3

- **Ticket 1.11:** Integración con sistema de notificaciones internas y externas
   - Disparo de notificaciones a equipo/candidatos según cambios y reglas.
   - **Story Points:** 2

---

## Épica 2: IA en el proceso de selección

### Frontend

- **Ticket 2.1:** Panel de ranking y sugerencias IA
   - Vista para revisar rankings automáticos y sugerencias de perfiles compatibles.
   - **Story Points:** 3

- **Ticket 2.2:** Interfaz para generación y edición de preguntas/feedback por IA
   - UI para mostrar textos generados y permitir su edición.
   - **Story Points:** 2

### Backend

- **Ticket 2.3:** Microservicio de análisis y ranking de candidatos por IA
   - Procesamiento de CVs, comparación con ofertas, aprendizaje automático.
   - **Story Points:** 8

- **Ticket 2.4:** API para sugerencias de perfiles compatibles y feedback IA
   - Endpoints para recomendaciones y generación de preguntas/feedback.
   - **Story Points:** 5

- **Ticket 2.5:** Lógica para reentrenamiento y registro de feedback en IA
   - Recogida y uso de feedback humano para mejorar modelo.
   - **Story Points:** 3

### Integración

- **Ticket 2.6:** Integración frontend-backend para panel IA y sugerencias
   - Llamadas al backend para mostrar rankings, sugerencias y preguntas generadas.
   - **Story Points:** 2

- **Ticket 2.7:** Integración del módulo IA con el registro de acciones/auditoría
   - Log de intervenciones manuales y resultados automáticos.
   - **Story Points:** 1

---

## Épica 3: Experiencia del candidato

### Frontend

- **Ticket 3.1:** Maquetación del portal del candidato
   - Vista accesible y responsive para seguimiento del proceso.
   - **Story Points:** 3

- **Ticket 3.2:** Visualización de estado y próximos pasos del proceso
   - Mostrar estado actualizado, fechas, y pasos pendientes.
   - **Story Points:** 2

- **Ticket 3.3:** UI para subida de documentación y gestión de notificaciones
   - Formulario para anexar documentos y sección de notificaciones personalizadas.
   - **Story Points:** 2

- **Ticket 3.4:** Sección de encuestas de satisfacción y feedback
   - Mostrar y recoger encuestas automáticas post-proceso.
   - **Story Points:** 2

### Backend

- **Ticket 3.5:** API de gestión del portal del candidato y estados
   - Endpoints para estados, uploads de documentos y consultas de avance.
   - **Story Points:** 3

- **Ticket 3.6:** Backend de gestión y envío de notificaciones
   - Lógica para notificaciones multicanal y personalizadas.
   - **Story Points:** 3

- **Ticket 3.7:** API para encuestas automáticas y registro de feedback
   - Endpoints para generación, recogida y consulta de encuestas de satisfacción.
   - **Story Points:** 2

### Integración

- **Ticket 3.8:** Integración frontend-backend del portal del candidato
   - Conexión de vistas y acciones con APIs de backend.
   - **Story Points:** 2

- **Ticket 3.9:** Integración de feedback y reporting para equipo de recruiters
   - Permitir acceso y análisis a resultados de encuestas y feedback recibido.
   - **Story Points:** 1

---

# Resumen de Epicas y Tickets

| Épica                                    | Tickets de Frontend | Tickets de Backend | Tickets de Integración | Total SP (aprox.) |
|-------------------------------------------|---------------------|--------------------|-----------------------|-------------------|
| 1. Gestión centralizada de candidatos     | 5                   | 4                  | 2                     | 30                |
| 2. IA en el proceso de selección          | 2                   | 3                  | 2                     | 24                |
| 3. Experiencia del candidato              | 4                   | 3                  | 2                     | 17                |

> **Notas**:
> - Los tickets pueden ser refinados y divididos según evolución y feedback del equipo.
> - Se recomienda priorizar la entrega incremental por épica, empezando por el core de cada flujo y las integraciones mínimas viables.
> - Las Story Points se pueden ajustar en planificación final de sprint según criterio de equipo.

---

# Planificación de Sprints – Backlog LTI

## Sprint 1
**Objetivo:** MVP de pipeline centralizado de candidatos (visualización básica y estructura API)

- **Frontend**
  - Ticket 1.1: Maquetación pipeline visual (5 SP)
  - Ticket 1.4: UI para cambio de estado en pipeline (2 SP)
  - Ticket 1.5: Sección de comentarios y tareas (2 SP)
- **Backend**
  - Ticket 1.6: API para gestión de candidatos y pipeline (5 SP)
  - Ticket 1.9: Registro de acciones y auditoría (2 SP)
  - Ticket 1.7: API de búsqueda y filtrado avanzado (3 SP)

**Total aprox.**  
Frontend: 9 SP  
Backend: 10 SP

---

## Sprint 2
**Objetivo:** Completar funcionalidades avanzadas de pipeline y comenzar IA

- **Frontend**
  - Ticket 1.2: Filtros y búsqueda avanzada en pipeline (3 SP)
  - Ticket 1.3: Perfil unificado del candidato (3 SP)
  - **Si hay margen:** Documentar feedback/bugs de UI pipeline
- **Backend**
  - Ticket 1.8: Lógica de automatización por IA y reglas (5 SP)
  - Ticket 2.3: Microservicio IA para análisis y ranking (8 SP)

**Total aprox.**  
Frontend: 6 SP  
Backend: 13 SP (puede extenderse a Sprint 3 si es necesario)

---

## Sprint 3
**Objetivo:** Integración pipeline, finalizar IA backend y comenzar panel IA frontend

- **Frontend**
  - Ticket 1.10: Integración frontend-backend del pipeline (3 SP)
  - Ticket 2.1: Panel de ranking y sugerencias IA (3 SP)
- **Backend**
  - Ticket 2.4: API para sugerencias de perfiles compatibles y feedback IA (5 SP)
  - Ticket 2.5: Lógica de reentrenamiento/feedback de IA (3 SP)

**Total aprox.**  
Frontend: 6 SP  
Backend: 8 SP

---

## Sprint 4
**Objetivo:** Integración IA, generación de preguntas y comenzar portal del candidato

- **Frontend**
  - Ticket 2.2: Interfaz para generación/edición de preguntas y feedback IA (2 SP)
  - Ticket 3.1: Maquetación portal del candidato (3 SP)
- **Backend**
  - Ticket 3.5: API de gestión portal candidato y estados (3 SP)
  - Ticket 3.6: Backend de gestión y envío de notificaciones (3 SP)
- **Integración**
  - Ticket 2.6: Integración panel IA y sugerencias (2 SP)
  - Ticket 2.7: Integración módulo IA y registro de acciones (1 SP)

**Total aprox.**  
Frontend: 5 SP  
Backend: 6 SP  
Integración: 3 SP (principalmente trabajo conjunto)

---

## Sprint 5
**Objetivo:** Portal del candidato, encuestas y feedback

- **Frontend**
  - Ticket 3.2: Visualización de estado y próximos pasos (2 SP)
  - Ticket 3.3: UI subida de documentación y gestión notificaciones (2 SP)
  - Ticket 3.4: Sección encuestas de satisfacción y feedback (2 SP)
- **Backend**
  - Ticket 3.7: API para encuestas y feedback (2 SP)

**Total aprox.**  
Frontend: 6 SP  
Backend: 2 SP

---

## Sprint 6
**Objetivo:** Integraciones finales y reporting

- **Frontend**
  - Ticket 3.8: Integración frontend-backend portal candidato (2 SP)
  - Ticket 3.9: Integración feedback/reporting recruiters (1 SP)
- **Backend**
  - Revisión/refactor final, solución de bugs, documentación API.

---

## Sprint 7 (buffer)
**Objetivo:** QA, ajustes, soporte, refinamiento UI/UX, entrega, documentación y retrospectiva.

---

# Resumen visual de la distribución

| Sprint  | Frontend (SP) | Backend (SP) | Integración (SP) | Objetivo principal                          |
|---------|---------------|--------------|------------------|---------------------------------------------|
| 1       | 9             | 10           | 0                | Pipeline visual y estructura API            |
| 2       | 6             | 13           | 0                | Funciones avanzadas pipeline / IA backend   |
| 3       | 6             | 8            | 0                | Integración pipeline, panel IA              |
| 4       | 5             | 6            | 3                | Integración IA y arranque portal candidato  |
| 5       | 6             | 2            | 0                | Portal candidato, encuestas/feedback        |
| 6       | 3             | -            | 3                | Integración final y reporting               |
| 7       | buffer        | buffer       | buffer           | QA, soporte, docs, entrega                  |

---

> **Notas**:
> - Algunos tickets de backend pueden solaparse en varios sprints si requieren mayor desarrollo (especialmente IA).
> - Si algún ticket resulta más complejo, puede partirse o extenderse al siguiente sprint.
> - El buffer en Sprint 7 permite absorber ajustes, QA y retrospectivas.
> - La integración siempre sigue a la finalización de backend de su épica.

