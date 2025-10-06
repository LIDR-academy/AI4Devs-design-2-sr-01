# ATS — Tickets empaquetados

Este paquete contiene un archivo Markdown por ticket (< 4 h cada uno).

## Índice

### R1

Dado un pipeline de una vacante, cuando agrego/quito/reordeno etapas y muevo candidatos con drag-and-drop, entonces el pipeline se actualiza y se registran eventos/auditoría.

- [ATS-R1-01 — Modelo "Stage" por vacante](./ATS-R1-01%20-%20Modelo%20"Stage"%20por%20vacante.md)
- [ATS-R1-02 — API reordenar etapas](./ATS-R1-02%20-%20API%20reordenar%20etapas.md)
- [ATS-R1-03 — UI Kanban básico por vacante](./ATS-R1-03%20-%20UI%20Kanban%20básico%20por%20vacante.md)
- [ATS-R1-04 — Drag&Drop de candidato entre etapas](./ATS-R1-04%20-%20Drag&Drop%20de%20candidato%20entre%20etapas.md)
- [ATS-R1-05 — Remapeo de automatizaciones al editar etapas](./ATS-R1-05%20-%20Remapeo%20de%20automatizaciones%20al%20editar%20etapas.md)

### R2

Dada una vacante lista, cuando publico en múltiples portales, entonces cada portal devuelve estado y las aplicaciones guardan `source` correcto.

- [ATS-R2-01 — Conector stub "Portal Genérico"](./ATS-R2-01%20-%20Conector%20stub%20"Portal%20Genérico".md)
- [ATS-R2-02 — Endpoint publicar en múltiples portales](./ATS-R2-02%20-%20Endpoint%20publicar%20en%20múltiples%20portales.md)
- [ATS-R2-03 — Tracking de `source` en Application](./ATS-R2-03%20-%20Tracking%20de%20`source`%20en%20Application.md)
- [ATS-R2-04 — UI de publicación y estado por portal](./ATS-R2-04%20-%20UI%20de%20publicación%20y%20estado%20por%20portal.md)
- [ATS-R2-05 — Alertas de fallo de publicación](./ATS-R2-05%20-%20Alertas%20de%20fallo%20de%20publicación.md)

### R3

Dado un cambio de etapa, cuando el candidato entra a una etapa con automatización, entonces se envía la plantilla correspondiente y queda rastro en EventLog.

- [ATS-R3-01 — CRUD de plantillas de comunicación](./ATS-R3-01%20-%20CRUD%20de%20plantillas%20de%20comunicación.md)
- [ATS-R3-02 — Motor de triggers por evento de etapa](./ATS-R3-02%20-%20Motor%20de%20triggers%20por%20evento%20de%20etapa.md)
- [ATS-R3-03 — Envío de email con registro](./ATS-R3-03%20-%20Envío%20de%20email%20con%20registro.md)
- [ATS-R3-04 — Reintento manual de notificación fallida](./ATS-R3-04%20-%20Reintento%20manual%20de%20notificación%20fallida.md)
- [ATS-R3-05 — Auditoría de automatizaciones](./ATS-R3-05%20-%20Auditoría%20de%20automatizaciones.md)

### H1

Dado un candidato, cuando completo el scorecard con campos requeridos, entonces se guarda feedback y se consolida multi‑rol con autor y fecha.

- [ATS-H1-01 — Modelo de scorecard por rol](./ATS-H1-01%20-%20Modelo%20de%20scorecard%20por%20rol.md)
- [ATS-H1-02 — UI de evaluación (entrevistador/HM)](<./ATS-H1-02%20-%20UI%20de%20evaluación%20(entrevistador-HM).md>)
- [ATS-H1-03 — Consolidación de feedback](./ATS-H1-03%20-%20Consolidación%20de%20feedback.md)
- [ATS-H1-04 — Permisos de visibilidad de feedback](./ATS-H1-04%20-%20Permisos%20de%20visibilidad%20de%20feedback.md)
- [ATS-H1-05 — EventLog de evaluaciones](./ATS-H1-05%20-%20EventLog%20de%20evaluaciones.md)

### H2

Dado OAuth de calendario conectado, cuando propongo horarios y hay conflictos, entonces recibo slots válidos/sugerencias y se envían invitaciones tentativas.

- [ATS-H2-01 — Integración Calendario: OAuth + conexión de cuenta](./ATS-H2-01%20-%20Integración%20Calendario:%20OAuth%20+%20conexión%20de%20cuenta.md)
- [ATS-H2-02 — Lectura de disponibilidad (free/busy)](<./ATS-H2-02%20-%20Lectura%20de%20disponibilidad%20(free-busy).md>)
- [ATS-H2-03 — Propuesta de slots y envío de invitaciones](./ATS-H2-03%20-%20Propuesta%20de%20slots%20y%20envío%20de%20invitaciones.md)
- [ATS-H2-04 — Resolución de conflicto y sugerencias](./ATS-H2-04%20-%20Resolución%20de%20conflicto%20y%20sugerencias.md)
- [ATS-H2-05 — Reprogramación y notificaciones](./ATS-H2-05%20-%20Reprogramación%20y%20notificaciones.md)

### H3

Dada una oferta ‘pending’, cuando los aprobadores autorizan y el candidato acepta, entonces la oferta pasa a ‘approved’ y la vacante queda ‘closed’ con KPIs actualizados.

- [ATS-H3-01 — Flujo de aprobación de oferta (multi-actor)](<./ATS-H3-01%20-%20Flujo%20de%20aprobación%20de%20oferta%20(multi-actor).md>)
- [ATS-H3-02 — Generación de carta de oferta (plantilla)](<./ATS-H3-02%20-%20Generación%20de%20carta%20de%20oferta%20(plantilla).md>)
- [ATS-H3-03 — Envío seguro al candidato + tracking](./ATS-H3-03%20-%20Envío%20seguro%20al%20candidato%20+%20tracking.md)
- [ATS-H3-04 — Cierre de vacante y actualización de KPIs](./ATS-H3-04%20-%20Cierre%20de%20vacante%20y%20actualización%20de%20KPIs.md)
- [ATS-H3-05 — Revocación/rollback de oferta](./ATS-H3-05%20-%20Revocación-rollback%20de%20oferta.md)

### I1

Dado un interview kit, cuando completo mi evaluación y cumplo requeridos, entonces se guarda y participa del consolidado multi‑entrevistador.

- [ATS-I1-01 — Modelo de evaluación y validaciones](./ATS-I1-01%20-%20Modelo%20de%20evaluación%20y%20validaciones.md)
- [ATS-I1-02 — Form de evaluación con autosave](./ATS-I1-02%20-%20Form%20de%20evaluación%20con%20autosave.md)
- [ATS-I1-03 — Consolidación multi-entrevistador](./ATS-I1-03%20-%20Consolidación%20multi-entrevistador.md)
- [ATS-I1-04 — Permisos de lectura/escritura de evaluaciones](./ATS-I1-04%20-%20Permisos%20de%20lectura-escritura%20de%20evaluaciones.md)
- [ATS-I1-05 — EventLog y métricas de evaluación](./ATS-I1-05%20-%20EventLog%20y%20métricas%20de%20evaluación.md)

### I2

Dado mi rol, cuando accedo al interview kit de un candidato, entonces veo sólo datos necesarios según RBAC/tenant y con historial de cambios.

- [ATS-I2-01 — Definición de "Interview Kit"](./ATS-I2-01%20-%20Definición%20de%20"Interview%20Kit".md)
- [ATS-I2-02 — Vista de kit previa a la entrevista](./ATS-I2-02%20-%20Vista%20de%20kit%20previa%20a%20la%20entrevista.md)
- [ATS-I2-03 — Control de acceso (mínima PII)](<./ATS-I2-03%20-%20Control%20de%20acceso%20(mínima%20PII).md>)
- [ATS-I2-04 — Actualizaciones y avisos del kit](./ATS-I2-04%20-%20Actualizaciones%20y%20avisos%20del%20kit.md)
- [ATS-I2-05 — Kit offline (fallback)](<./ATS-I2-05%20-%20Kit%20offline%20(fallback).md>)

### I3

Dada mi disponibilidad, cuando acepto/declino invitaciones o cambia la agenda, entonces se actualizan estados y notificaciones con auditoría.

- [ATS-I3-01 — Gestión de disponibilidad del entrevistador](./ATS-I3-01%20-%20Gestión%20de%20disponibilidad%20del%20entrevistador.md)
- [ATS-I3-02 — Aceptar/declinar invitaciones](./ATS-I3-02%20-%20Aceptar-declinar%20invitaciones.md)
- [ATS-I3-03 — Reglas de re-asignación automática](./ATS-I3-03%20-%20Reglas%20de%20re-asignación%20automática.md)
- [ATS-I3-04 — Sincronización ventana/latencia](./ATS-I3-04%20-%20Sincronización%20ventana-latencia.md)
- [ATS-I3-05 — Auditoría de agenda (trail completo)](<./ATS-I3-05%20-%20Auditoría%20de%20agenda%20(trail%20completo).md>)

### C1

Dado que subo mi CV, cuando el parser pre‑llena el formulario con baja confianza en algunos campos, entonces debo confirmar antes de enviar la aplicación.

- [ATS-C1-01 — Endpoint de subida de CV](./ATS-C1-01%20-%20Endpoint%20de%20subida%20de%20CV.md)
- [ATS-C1-02 — Adaptador parser de CV (stub)](<./ATS-C1-02%20-%20Adaptador%20parser%20de%20CV%20(stub).md>)
- [ATS-C1-03 — Pre-llenado de formulario](./ATS-C1-03%20-%20Pre-llenado%20de%20formulario.md)
- [ATS-C1-04 — Manejo de baja confianza](./ATS-C1-04%20-%20Manejo%20de%20baja%20confianza.md)
- [ATS-C1-05 — Auditoría de carga y parseo](./ATS-C1-05%20-%20Auditoría%20de%20carga%20y%20parseo.md)

### C2

Dada mi postulación, cuando consulto el portal, entonces veo la etapa actual, el timeline y recibo notificaciones por cambios.

- [ATS-C2-01 — API "Mi Postulación: estado y timeline"](./ATS-C2-01%20-%20API%20"Mi%20Postulación:%20estado%20y%20timeline".md)
- [ATS-C2-02 — UI Portal: vista de estado](./ATS-C2-02%20-%20UI%20Portal:%20vista%20de%20estado.md)
- [ATS-C2-03 — Servicio de notificaciones por cambio de etapa](./ATS-C2-03%20-%20Servicio%20de%20notificaciones%20por%20cambio%20de%20etapa.md)
- [ATS-C2-04 — Mensaje de rechazo respetuoso + sugerencias](./ATS-C2-04%20-%20Mensaje%20de%20rechazo%20respetuoso%20+%20sugerencias.md)
- [ATS-C2-05 — Preferencias de comunicación del candidato](./ATS-C2-05%20-%20Preferencias%20de%20comunicación%20del%20candidato.md)

### C3

Dado un set de slots firmados, cuando elijo uno válido, entonces se bloquea en agendas y recibo confirmación; puedo cancelar dentro de la ventana permitida.

- [ATS-C3-01 — API listar slots elegibles](./ATS-C3-01%20-%20API%20listar%20slots%20elegibles.md)
- [ATS-C3-02 — Selección de slot y confirmación](./ATS-C3-02%20-%20Selección%20de%20slot%20y%20confirmación.md)
- [ATS-C3-03 — Cancelación con ventana mínima](./ATS-C3-03%20-%20Cancelación%20con%20ventana%20mínima.md)
- [ATS-C3-04 — Expiración y regeneración de slots](./ATS-C3-04%20-%20Expiración%20y%20regeneración%20de%20slots.md)
- [ATS-C3-05 — UI de auto-agendado](./ATS-C3-05%20-%20UI%20de%20auto-agendado.md)

### A1

Dado SSO/Auth0, cuando un usuario inicia sesión y tiene rol por tenant, entonces se aplica RBAC por recurso y queda auditado.

- [ATS-A1-01 — Modelo Tenant y vinculación de usuarios](./ATS-A1-01%20-%20Modelo%20Tenant%20y%20vinculación%20de%20usuarios.md)
- [ATS-A1-02 — Integración SSO/Auth0 (claims básicas)](<./ATS-A1-02%20-%20Integración%20SSO-Auth0%20(claims%20básicas).md>)
- [ATS-A1-03 — Guardia de permisos por recurso](./ATS-A1-03%20-%20Guardia%20de%20permisos%20por%20recurso.md)
- [ATS-A1-04 — Selector de tenant en UI](./ATS-A1-04%20-%20Selector%20de%20tenant%20en%20UI.md)
- [ATS-A1-05 — Audit log de cambios de roles](./ATS-A1-05%20-%20Audit%20log%20de%20cambios%20de%20roles.md)

### A2

Dado el Centro de Integraciones, cuando conecto Slack/webhooks/portales y configuro branding, entonces veo estado de salud y se aplica el tema en portal/emails.

- [ATS-A2-01 — Centro de Integraciones (UI + API)](<./ATS-A2-01%20-%20Centro%20de%20Integraciones%20(UI%20+%20API).md>)
- [ATS-A2-02 — Gestión segura de credenciales](./ATS-A2-02%20-%20Gestión%20segura%20de%20credenciales.md)
- [ATS-A2-03 — Webhooks por eventos clave](./ATS-A2-03%20-%20Webhooks%20por%20eventos%20clave.md)
- [ATS-A2-04 — Integración Slack (notificaciones)](<./ATS-A2-04%20-%20Integración%20Slack%20(notificaciones).md>)
- [ATS-A2-05 — Branding por tenant (logo/colores)](<./ATS-A2-05%20-%20Branding%20por%20tenant%20(logo-colores).md>)

### A3

Dado el catálogo de eventos, cuando defino reglas con prioridad y plantillas versionadas, entonces el motor ejecuta idempotente y reporta conflictos.

- [ATS-A3-01 — Catálogo de eventos y acciones](./ATS-A3-01%20-%20Catálogo%20de%20eventos%20y%20acciones.md)
- [ATS-A3-02 — Editor de reglas con prioridad y condiciones](./ATS-A3-02%20-%20Editor%20de%20reglas%20con%20prioridad%20y%20condiciones.md)
- [ATS-A3-03 — Motor de ejecución idempotente](./ATS-A3-03%20-%20Motor%20de%20ejecución%20idempotente.md)
- [ATS-A3-04 — Versionado de plantillas (email/SMS)](<./ATS-A3-04%20-%20Versionado%20de%20plantillas%20(email-SMS).md>)
- [ATS-A3-05 — Resolución de conflictos entre reglas](./ATS-A3-05%20-%20Resolución%20de%20conflictos%20entre%20reglas.md)

### B1

Dado el dashboard de funnel, cuando aplico filtros y exporto, entonces veo KPIs recalculados y descargo CSV con diccionario de columnas.

- [ATS-B1-01 — Esquema de métricas y materialized views](./ATS-B1-01%20-%20Esquema%20de%20métricas%20y%20materialized%20views.md)
- [ATS-B1-02 — Filtros (fecha, vacante, etapa, fuente, tenant)](<./ATS-B1-02%20-%20Filtros%20(fecha,%20vacante,%20etapa,%20fuente,%20tenant).md>)
- [ATS-B1-03 — UI de dashboards](./ATS-B1-03%20-%20UI%20de%20dashboards.md)
- [ATS-B1-04 — Exportación CSV/JSON documentada](./ATS-B1-04%20-%20Exportación%20CSV-JSON%20documentada.md)
- [ATS-B1-05 — Indicador de frescura de datos](./ATS-B1-05%20-%20Indicador%20de%20frescura%20de%20datos.md)

### B2

Dadas reglas de umbral, cuando una métrica se desvía, entonces se dispara alerta (email/Slack) con historial y posibilidad de silenciamiento.

- [ATS-B2-01 — Motor de umbrales y condiciones](./ATS-B2-01%20-%20Motor%20de%20umbrales%20y%20condiciones.md)
- [ATS-B2-02 — Notificaciones (email/Slack) de alertas](<./ATS-B2-02%20-%20Notificaciones%20(email-Slack)%20de%20alertas.md>)
- [ATS-B2-03 — UI de reglas de alerta](./ATS-B2-03%20-%20UI%20de%20reglas%20de%20alerta.md)
- [ATS-B2-04 — Correlación básica entre KPIs](./ATS-B2-04%20-%20Correlación%20básica%20entre%20KPIs.md)
- [ATS-B2-05 — Silenciamiento temporal (maintenance window)](<./ATS-B2-05%20-%20Silenciamiento%20temporal%20(maintenance%20window).md>)

### B3

Dadas campañas con UTM, cuando genero atribución y ejecuto un A/B, entonces obtengo first/last‑touch, lineal y recomendación con significancia.

- [ATS-B3-01 — Captura de UTM/portal/referral en intake](./ATS-B3-01%20-%20Captura%20de%20UTM-portal-referral%20en%20intake.md)
- [ATS-B3-02 — Modelo de campañas y costos](./ATS-B3-02%20-%20Modelo%20de%20campañas%20y%20costos.md)
- [ATS-B3-03 — Reporte de atribución multi-touch (básico)](<./ATS-B3-03%20-%20Reporte%20de%20atribución%20multi-touch%20(básico).md>)
- [ATS-B3-04 — Experimentos A/B por etapa](./ATS-B3-04%20-%20Experimentos%20A-B%20por%20etapa.md)
- [ATS-B3-05 — Cálculo de significancia y recomendación](./ATS-B3-05%20-%20Cálculo%20de%20significancia%20y%20recomendación.md)
