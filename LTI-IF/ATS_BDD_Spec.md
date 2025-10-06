# ATS — Especificación BDD
Fecha: 2025-10-02

> Este documento reúne escenarios BDD (Gherkin) por **Feature**, alineados a las User Stories y tickets (< 4 h c/u).  
> Convención: `@tenant`, `@auth`, `@api`, `@ui`, `@regression`, `@smoke` como tags de ejecución.

---

## Feature: R1 — Pipeline editable y drag & drop (@ui @api)
Como **Reclutador**, quiero configurar y reordenar etapas para gestionar el pipeline.

### Background
Dado que existe una vacante "Backend Engineer" con pipeline por defecto
Y que estoy autenticado como "reclutador@tenant.com"

### Scenario: Crear y listar etapas
Cuando creo una etapa "Screening" y otra "Entrevista Técnica"
Entonces el sistema devuelve la lista de etapas con orden correlativo
Y registra un evento "StageCreated" en el audit log

### Scenario: Reordenar etapas con persistencia
Dado que existen etapas "Screening", "Entrevista Técnica"
Cuando reordeno "Entrevista Técnica" antes que "Screening"
Entonces el orden se persiste para la vacante
Y se registra el evento "StageReordered"
Y las automatizaciones vinculadas son re-mapeadas o se solicita confirmación

### Scenario: Mover candidato entre etapas (DnD)
Dado un candidato "C-123" en "Screening"
Cuando lo arrastro a "Entrevista Técnica"
Entonces el estado del candidato cambia a esa etapa con timestamp y usuario
Y se registra el evento "ApplicationStageChanged"

---

## Feature: R2 — Multiposting y tracking de fuente (@api @ui)
Como **Reclutador**, quiero publicar en múltiples portales y medir el source.

### Background
Dado que existe una vacante lista para publicar
Y que conecté el "Portal Genérico" en el Centro de Integraciones

### Scenario: Publicación en múltiples portales con resultado por portal
Cuando solicito publicar en ["Portal Genérico", "Portal B"]
Entonces cada portal devuelve estado (exitoso o error con detalle)
Y ante errores el sistema aplica hasta 3 reintentos y registra en EventLog

### Scenario: Tracking de fuente en aplicaciones
Dado que la vacante está publicada
Cuando el candidato aplica desde el "Portal Genérico" con UTM
Entonces la Application se guarda con `source=portal_generico` y utm normalizada

---

## Feature: R3 — Plantillas y automatizaciones por etapa (@api @ui)
Como **Reclutador**, quiero automatizar mensajes por cambio de etapa.

### Scenario: Envío automático al entrar en etapa
Dado una regla "al entrar en Entrevista Técnica → enviar email 'Invitación'"
Cuando muevo un candidato a "Entrevista Técnica"
Entonces se envía el email con ID de mensaje
Y se registra el resultado (éxito/fallo) en EventLog

### Scenario: Reintento manual de notificación fallida
Dado que un envío falló
Cuando presiono "Reintentar"
Entonces el sistema reintenta una vez con backoff
Y actualiza el estado del mensaje

---

## Feature: H1 — Scorecards y feedback (@ui @api)
Como **Hiring Manager**, quiero evaluar con scorecards y consolidar feedback.

### Scenario: Completar evaluación con campos requeridos
Dado un scorecard activo para "Backend Engineer"
Cuando completo todos los campos requeridos y guardo
Entonces el sistema valida y guarda la evaluación con autor y fecha

### Scenario: Consolidación multi-rol
Dado que existen evaluaciones de entrevistadores y del HM
Cuando consulto el resultado consolidado
Entonces veo promedio ponderado y quién evaluó cada dimensión

---

## Feature: H2 — Proponer horarios y agendar (@api @calendar @ui)
Como **Hiring Manager**, quiero proponer horarios y agendar entrevistas.

### Background
Dado que conecté Google Calendar con OAuth válido

### Scenario: Proponer slots válidos
Cuando solicito generar 3 slots para la próxima semana
Entonces recibo 3 opciones libres (free/busy)
Y se envían invitaciones tentativas a entrevistadores

### Scenario: Reprogramar con conflictos
Dado un evento tentativo creado
Cuando intento reprogramar a un horario que choca
Entonces el sistema sugiere alternativas y actualiza la invitación elegida

---

## Feature: H3 — Aprobar oferta y cerrar vacante (@api @ui @security)
Como **Hiring Manager**, quiero aprobar ofertas y cerrar vacantes.

### Scenario: Flujo de aprobación multi-actor
Dado una oferta en estado "pending"
Cuando los aprobadores autorizan en orden
Entonces la oferta pasa a "approved" y queda traza en auditoría

### Scenario: Cerrar vacante y actualizar KPIs
Dado una oferta aceptada por el candidato
Cuando cierro la vacante
Entonces el Job pasa a "closed" y se recalculan KPIs (time-to-hire)

---

## Feature: I1 — Evaluaciones de entrevista (@ui)
Como **Entrevistador**, quiero enviar evaluaciones estructuradas.

### Scenario: Autosave y bloqueo por incompletitud
Dado un formulario de evaluación abierto
Cuando intento finalizar con campos requeridos vacíos
Entonces el sistema bloquea el envío e indica los faltantes

---

## Feature: I2 — Interview Kit (@ui @security)
Como **Entrevistador**, quiero acceder al kit con mínima PII.

### Scenario: Acceso controlado al kit
Dado que tengo rol de Entrevistador
Cuando abro el kit de "C-123"
Entonces veo sólo datos necesarios (CV, rol, pautas) según RBAC del tenant

---

## Feature: I3 — Disponibilidad y aceptar/declinar (@ui @calendar)
Como **Entrevistador**, quiero gestionar disponibilidad y RSVP.

### Scenario: Aceptar invitación desde enlace firmado
Dado una invitación con token válido
Cuando acepto la invitación
Entonces el estado del evento cambia y se notifica a organizadores

---

## Feature: C1 — Parseo de CV y pre-llenado (@api @privacy)
Como **Candidato**, quiero subir CV y pre-llenar formulario.

### Scenario: Pre-llenado con umbral de confianza
Dado que subo un CV
Cuando el parser devuelve confianza baja en "teléfono"
Entonces el sistema solicita confirmación explícita antes de continuar

---

## Feature: C2 — Portal de estado y notificaciones (@ui @api)
Como **Candidato**, quiero ver estado y recibir avisos.

### Scenario: Ver timeline de mi postulación
Dado que ingreso a "Mi Postulación"
Cuando consulto el estado de "C-123"
Entonces veo la etapa actual y el timeline de eventos

---

## Feature: C3 — Auto-agendado por el candidato (@ui @calendar)
Como **Candidato**, quiero elegir entre horarios disponibles.

### Scenario: Confirmar slot dentro de ventana válida
Dado 3 slots firmados y no expirados
Cuando selecciono uno
Entonces se bloquea en la agenda y recibo confirmación

---

## Feature: A1 — SSO y RBAC multitenant (@security @auth)
Como **Admin**, quiero roles por tenant y autenticación SSO/Auth0.

### Scenario: Enforce de permisos por recurso
Dado que soy usuario sin rol en el tenant
Cuando intento listar Applications
Entonces recibo 403 y se registra intento en audit log

---

## Feature: A2 — Integraciones y branding (@api @ui)
Como **Admin**, quiero configurar integraciones y branding.

### Scenario: Conectar Slack y probar salud
Cuando conecto Slack e inicio "probar conexión"
Entonces recibo status OK y un mensaje de prueba en el canal configurado

---

## Feature: A3 — Reglas y plantillas (@api)
Como **Admin**, quiero definir reglas con prioridad.

### Scenario: Ejecutar regla idempotente
Dado una regla "al mover a Entrevista Técnica → email Invitación"
Cuando muevo un candidato de forma repetida en menos de 1 minuto
Entonces sólo se ejecuta una vez gracias a la deduplicación

---

## Feature: B1 — Dashboards (funnel) (@ui @data)
Como **Analista**, quiero visualizar KPIs filtrables.

### Scenario: Aplicar filtros y exportar
Dado el dashboard de funnel
Cuando filtro por fecha y vacante y exporto a CSV
Entonces recibo datos con diccionario de columnas

---

## Feature: B2 — Alertas por desvío de KPIs (@api @notifications)
Como **Analista**, quiero alertas con umbrales.

### Scenario: Disparar alerta por caída de conversión
Dado una regla "conversion etapa N < 10% durante 7 días"
Cuando la condición se cumple
Entonces se envía alerta por Slack y queda incidente registrado

---

## Feature: B3 — Atribución y A/B testing (@data @experiments)
Como **Analista**, quiero atribución y experimentos por etapa.

### Scenario: Reporte de atribución multi-touch
Dado campañas activas con UTM
Cuando genero el reporte
Entonces veo resultados first/last-touch y lineal con explicación del método

### Scenario: Finalizar experimento con recomendación
Dado un experimento con tamaño de muestra suficiente
Cuando finalizo el experimento
Entonces obtengo significancia y recomendación de variante ganadora
