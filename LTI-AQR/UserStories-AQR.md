LTI – Documentación Inicial de Implementación
=============================================

_(Generado: 24 jun 2025)_

> 👋 **Nota:** Este documento consolida Historias de Usuario, Backlog priorizado y Tickets técnicos con estimación de esfuerzo para el MVP de _LTI_. Está listo para usarse en grooming y planificación de sprints.

* * *

Tabla de Contenidos
-------------------

1. [Historias de Usuario](#historias-de-usuario)

2. [Backlog de Producto](#backlog-de-producto)

3. [Tickets Técnicos y Estimaciones](#tickets-t%C3%A9cnicos-y-estimaciones)

4. [Diagramas ASCII](#diagramas-ascii)

* * *

Historias de Usuario
--------------------

### 1. Crear Vacante

_Como_ **Recruiter**,  
_quiero_ registrar una nueva vacante con sus atributos clave (título, departamento, nivel, SLA),  
_para que_ el proceso de contratación arranque y los candidatos puedan postularse.

**Criterios de Aceptación**

1. El formulario permite capturar título, ubicación, departamento, tipo de contrato y rango salarial.

2. Validación obligatoria de campos requeridos y formato (p. ej., rango salarial numérico).

3. Al guardar, se genera un ID único de `JOB_REQUISITION`, estado “Abierta” y se publica el evento `job.created`.

4. La vacante queda visible inmediatamente en el tablero de posiciones abiertas.

**Notas Adicionales**

* Regla de negocio: solo usuarios con rol _Recruiter_ o superior pueden crear vacantes.

**Historias de Usuario Relacionadas**

* Aplicar a Vacante

* AI‑Screening Express

* * *

### 2. Aplicar a Vacante

_Como_ **Candidato**,  
_quiero_ cargar mi CV y postularme a una vacante abierta,  
_para que_ el equipo de reclutamiento me considere en el proceso.

**Criterios de Aceptación**

1. Puedo arrastrar‑y‑soltar PDF/DOCX (máx. 10 MB) o pegar link de LinkedIn.

2. Si el archivo excede el tamaño o formato, el sistema muestra error contextual.

3. Se crea un `APPLICATION` con estado “Applied” y se emite `candidate.created`.

4. Email de confirmación automático se envía al candidato.

**Notas Adicionales**

* El CV original se almacena en S3/MinIO; extracto y embeddings van a `pgvector`.

**Historias de Usuario Relacionadas**

* AI‑Screening Express

* Programar Entrevista Automática

* * *

### 3. AI‑Screening Express

_Como_ **Hiring Manager**,  
_quiero_ ver un ranking automático de candidatos con puntaje de ajuste y alertas de sesgo,  
_para que_ pueda priorizar entrevistas con los perfiles más prometedores de forma objetiva.

**Criterios de Aceptación**

1. El sistema muestra lista paginada con **score** (0‑100), semáforo de sesgo y match cultural (%).

2. El ranking se actualiza en menos de 15 s tras la llegada de un nuevo CV.

3. Puedo ordenar, filtrar por score y descargar CSV.

4. Cada score incluye botón “Explain” que despliega factores clave (explicabilidad).

**Notas Adicionales**

* Si el Bias Detector marca alerta roja, la tarjeta se resalta y exige doble revisión.

**Historias de Usuario Relacionadas**

* Feedback Colaborativo en Tiempo Real

* Dashboard Analítico

* * *

### 4. Feedback Colaborativo en Tiempo Real

_Como_ **Entrevistador**,  
_quiero_ capturar notas y calificaciones durante la entrevista en modo colaborativo,  
_para que_ el equipo tome decisiones rápidas basadas en información unificada.

**Criterios de Aceptación**

1. Edición simultánea estilo Google Docs (WebSocket/Subscriptions) entre entrevistadores.

2. Cada feedback queda ligado al `INTERVIEW` y registra autor + timestamp.

3. Scorecard admite logros‑contra‑competencias con escala 1‑5 y comentarios libres.

4. Al cerrar la entrevista, se consolida un snapshot “solo‑lectura” visible a Recruiter y Hiring Manager.

**Notas Adicionales**

* Conflictos de edición se resuelven con _last‑writer‑wins_ y registro de historial.

**Historias de Usuario Relacionadas**

* Programar Entrevista Automática

* Generar y Firmar Oferta

* * *

### 5. Programar Entrevista Automática

_Como_ **Recruiter**,  
_quiero_ que el sistema agende automáticamente un slot de Zoom y envíe recordatorios,  
_para que_ ahorre tiempo y evite cuellos de botella al coordinar entrevistas.

**Criterios de Aceptación**

1. Al mover al candidato a “Entrevista 1”, se dispara regla del **Automation Engine**.

2. El motor busca disponibilidad en Google Calendar del entrevistador asignado.

3. Se crea un evento con link de Zoom y se notifican participante(s) por email/Slack.

4. Si no hay disponibilidad en 24 h, el sistema registra alerta en el tablero.

**Notas Adicionales**

* Configuración “no‑code” editable por HR sin intervención de devs.

**Historias de Usuario Relacionadas**

* Feedback Colaborativo en Tiempo Real

* Generar y Firmar Oferta

* * *

### 6. Generar y Firmar Oferta

_Como_ **Recruiter**,  
_quiero_ generar la carta de oferta y capturar firma electrónica del candidato,  
_para que_ oficialice su contratación sin papeleo físico.

**Criterios de Aceptación**

1. Plantilla de oferta rellena automáticamente nombre, puesto, salario y fecha de inicio.

2. El candidato recibe link seguro (token único) para firmar vía e‑signature (p. ej., DocuSign).

3. Tras la firma, el `OFFER` pasa a estado “Accepted” y se dispara `offer.accepted`.

4. Copia PDF queda almacenada en S3 y vinculada al expediente del candidato.

**Notas Adicionales**

* Tiempo máximo de carga de documento: < 3 s (80.º percentil).

**Historias de Usuario Relacionadas**

* Onboarding Automático

* Dashboard Analítico

* * *

### 7. Onboarding Automático

_Como_ **IT Ops Manager**,  
_quiero_ que, tras aceptar la oferta, se creen tareas de onboarding (hardware, payroll, access),  
_para que_ el nuevo empleado tenga todo listo desde el día 1.

**Criterios de Aceptación**

1. `offer.accepted` desencadena flujo del **Automation Engine** con plantillas predefinidas.

2. Se generan tasks en Jira/ServiceNow para cada departamento implicado.

3. El nuevo empleado recibe correo “Welcome” con checklist y fechas límite.

4. El flujo puede monitorearse en tablero de onboarding con % de progreso.

**Notas Adicionales**

* SLA genérico: todas las tareas deben cerrarse antes de la fecha de inicio.

**Historias de Usuario Relacionadas**

* Generar y Firmar Oferta

* * *

### 8. Dashboard Analítico

_Como_ **HR Director**,  
_quiero_ visualizar métricas clave (time‑to‑hire, funnel drop‑off, diversidad),  
_para que_ pueda identificar cuellos de botella y mejorar el proceso.

**Criterios de Aceptación**

1. Panel muestra KPIs con filtros por rango de fechas, departamento y recruiter.

2. Gráficas se actualizan en near‑real‑time (≤ 5 min de retraso) usando **Reporting Service**.

3. Cada métrica tiene tooltip con fórmula y objetivo (benchmark).

4. Exportación a CSV y enlaces a insights detallados.

**Notas Adicionales**

* Acceso restringido a roles _HR Director_ y _C‑level_.

**Historias de Usuario Relacionadas**

* AI‑Screening Express

* * *

### 9. Definir Regla de Automatización No‑Code

_Como_ **Recruiter Avanzado**,  
_quiero_ crear reglas “if‑this‑then‑that” mediante interfaz drag‑and‑drop,  
_para que_ personalice el flujo sin depender de desarrollo.

**Criterios de Aceptación**

1. Paleta de disparadores (evento, webhook, cron) y acciones (email, Slack, etapa) disponible.

2. Validación de regla antes de activar: sintaxis correcta y prueba en sandbox.

3. Las reglas activas se listan con estado (on/off) y fecha de última ejecución.

4. Todo cambio genera versión y audit‑trail.

**Notas Adicionales**

* Diseñado para escalar ≥ 1000 reglas sin degradar performance.

**Historias de Usuario Relacionadas**

* Programar Entrevista Automática

* * *

### 10. Integración HRIS via API

_Como_ **Integrations Engineer**,  
_quiero_ sincronizar empleados y vacantes con nuestro HRIS corporativo (BambooHR / Workday),  
_para que_ los datos se mantengan consistentes sin captura doble.

**Criterios de Aceptación**

1. API REST/GraphQL soporta OAuth 2.0 y scopes granularizados.

2. Sincronización bidireccional incremental cada 15 min via **Integration Hub**.

3. Conflictos de escritura se resuelven con estrategia _source‑of‑truth_ configurable.

4. Logs de integración accesibles y exportables para auditoría.

**Notas Adicionales**

* Debe cumplir GDPR y cifrado en tránsito (TLS 1.3) y reposo (AES‑256).

**Historias de Usuario Relacionadas**

* Crear Vacante

* Onboarding Automático

* * *

Backlog de Producto
-------------------



### ÉPICA 1 – Core Hiring Flow _(Must Have)_

| Rank | PBI ID | Historia base              | Prioridad | Nota de WSJF*                          |
| ---- | ------ | -------------------------- | --------- | -------------------------------------- |
| 1    | 1.1    | US-1 Crear Vacante         | **M**     | Alto (CoD alto, job size pequeño)      |
| 2    | 1.2    | US-2 Aplicar Vacante       | **M**     | Alto                                   |
| 3    | 1.5    | US-5 Programar Entrevista  | **M**     | Medio-alto                             |
| 4    | 1.6    | US-6 Generar/Firmar Oferta | **M**     | Medio-alto                             |
| 5    | 1.3    | US-3 AI-Screening          | **S**     | Medio (beneficio alto, tamaño mediano) |
| 6    | 1.4    | US-4 Feedback Colab.       | **S**     | Medio                                  |
| 7    | 1.7    | US-7 Onboarding Auto.      | **S**     | Medio-bajo                             |

### ÉPICA 2 – Automation & Workflow _(Should Have)_

| Rank | PBI ID | Historia base                | Prioridad | WSJF       |
| ---- | ------ | ---------------------------- | --------- | ---------- |
| 8    | 2.1    | US-9 Motor No-Code Rules     | **M**     | Medio-alto |
| 9    | 2.2    | Spike – Plantillas de Reglas | **C**     | Bajo       |

### ÉPICA 3 – Analytics & Reporting _(Should)_

| Rank | PBI ID | Historia base             | Prioridad | WSJF  |
| ---- | ------ | ------------------------- | --------- | ----- |
| 10   | 3.1    | US-8 Dashboard KPIs       | **S**     | Medio |
| 11   | 3.2    | PBI – Export & Drill-down | **C**     | Bajo  |

### ÉPICA 4 – Integraciones _(Must/Should)_

| Rank | PBI ID | Historia base            | Prioridad | WSJF       |
| ---- | ------ | ------------------------ | --------- | ---------- |
| 12   | 4.1    | US-10 HRIS Sync          | **M**     | Medio-alto |
| 13   | 4.2    | PBI – Slack & Zoom hooks | **S**     | Bajo-medio |

### ÉPICA 5 – Plataforma & Seguridad _(Foundation – Must)_

| Rank | PBI ID | Descripción              | Prioridad | WSJF  |
| ---- | ------ | ------------------------ | --------- | ----- |
| 14   | 5.1    | Data Model + RBAC        | **M**     | Alto  |
| 15   | 5.2    | Event Bus + WebSockets   | **M**     | Alto  |
| 16   | 5.3    | Storage Layer (S3/MinIO) | **M**     | Medio |
| 17   | 5.4    | CI/CD Pipeline inicial   | **M**     | Medio |

*WSJF preliminar (Cost of Delay ÷ Job Size). Valores exactos se calculan en planning con el equipo.

* * *

### Cómo leer el backlog

* **Rank**: orden de entrega sugerido.

* **PBI ID**: identificador único; facilita traza con Jira/ADO.

* **Prioridad (M/S/C/W)**: MoSCoW para alinear expectativas de negocio.

* **Épicas** agrupan funcionalidades coherentes; dentro, las Historias (User Stories) o Spikes se entregan en incrementos que caben en 1 sprint.

* * *

Desglose de Tickets Técnicos y Estimaciones
-------------------------------

> **Convenciones usadas**
> 
> * **IDs**: `LTI-###` secuenciales.
> 
> * **Story Points**: escala Fibonacci modificada 1-2-3-5-8-13 porque ofrece saltos perceptivos claros y evita falsa precisión ([mountaingoatsoftware.com](https://www.mountaingoatsoftware.com/blog/why-the-fibonacci-sequence-works-well-for-estimating?utm_source=chatgpt.com "Agile Estimation: Why The Fibonacci Sequence Works")).
> 
> * **DoD genérico**: código mergeado a `main`, revisado, tests unit ≥ 80 % cov, integración en CI verde, docs actualizadas, feature flag detrás de config, cumple seguridad básica OWASP + linters + scan SCA ([atlassian.com](https://www.atlassian.com/agile/project-management/definition-of-done?utm_source=chatgpt.com "Definition Of Done (DoD) Explained for Agile Teams - Atlassian")).

* * *

### Épica 1 – Core Hiring Flow _(Sprint 1-3 foco producto)_

| Ticket      | Story                     | Componente              | Descripción técnica                                                                                                     | SP  | Depende de |
| ----------- | ------------------------- | ----------------------- | ----------------------------------------------------------------------------------------------------------------------- | --- | ---------- |
| **LTI-101** | US-1 Crear Vacante        | **Frontend**            | Formulario React + Zod validation, Tailwind, campos `title/department/location/salary`, llamadas a GraphQL `createJob`. | 3   | —          |
| **LTI-102** | US-1                      | **Job Svc**             | Resolver `createJob`, DTO/mapper → `JOB_REQUISITION` tabla, publish `job.created` in Kafka.                             | 5   | 101, 501   |
| **LTI-103** | US-1                      | **DB**                  | Migration Liquibase: tabla `JOB_REQUISITION` con índices `status`, `owner_id`.                                          | 2   | 501        |
| **LTI-104** | US-1                      | **E2E/QA**              | Cypress flujo “Recruiter crea vacante y ve en tablero”.                                                                 | 3   | 101-103    |
| **LTI-111** | US-2 Aplicar              | **Frontend**            | Drag-&-drop CV, LinkIn scrape; upload a S3 presigned URL; progress bar.                                                 | 5   | 101        |
| **LTI-112** | US-2                      | **Candidate Svc**       | Endpoint `applyToJob`, guardar `APPLICATION`, publicar `candidate.created`.                                             | 5   | 103        |
| **LTI-113** | US-2                      | **Storage / Vector DB** | Lambda worker: parse CV → embeddings → `pgvector` `resume_vector`                                                       | 8   | 112        |
| **LTI-114** | US-3 AI-Screening         | **Matching AI Svc**     | Consumer `candidate.created` + `job.created`, similarity search, score calc, emit `match.completed`.                    | 8   | 113        |
| **LTI-115** | US-3                      | **Frontend**            | Tabla ranking con WebSocket subscription `match.completed`, orden & filtros.                                            | 3   | 114        |
| **LTI-121** | US-5 Programar Entrevista | **Automation Engine**   | Rule template “→ createZoomEvent”, calendars OAuth flow, persistence JSON DSL                                           | 8   | 112        |
| **LTI-122** | US-5                      | **Integration Hub**     | Connector Zoom + Google Calendar; outbox pattern; retries.                                                              | 5   | 121        |
| **LTI-123** | US-5                      | **Notification Svc**    | Email & Slack reminders (templating Handlebars).                                                                        | 3   | 122        |
| **LTI-131** | US-4 Feedback             | **Frontend**            | Live scorecard (QuillJS + Yjs CRDT) for co-editing.                                                                     | 5   | 115        |
| **LTI-132** | US-4                      | **Interview Svc**       | WebSocket room, conflict resolution (_last-writer-wins_).                                                               | 8   | 131        |
| **LTI-141** | US-6 Generar Oferta       | **Offer Svc**           | Docx template merge, DocuSign API, store PDF in S3, state machine `OFFER.status`                                        | 8   | 112        |
| **LTI-142** | US-6                      | **Frontend**            | Wizard para revisar oferta, disparar firma, mostrar tracking.                                                           | 3   | 141        |

* * *



### Épica 5 – Plataforma & Seguridad _(Sprint 0-1, habilitador)_

| Ticket      | Componente        | Descripción                                                                      | SP  |
| ----------- | ----------------- | -------------------------------------------------------------------------------- | --- |
| **LTI-501** | **Infra-CI/CD**   | Pipeline GitHub Actions → Docker build → push ECR → Argo CD sync (K8s)           | 5   |
| **LTI-502** | **RBAC Gateway**  | OPA policies: `Recruiter`, `HM`, `Interviewer`, `Admin`. JWT middleware GraphQL. | 5   |
| **LTI-503** | **Event Bus**     | Kafka topics (`job.*`, `candidate.*`, `match.*`), shared Avro schema registry.   | 3   |
| **LTI-504** | **Observability** | OpenTelemetry SDK + Grafana Tempo/Loki helm charts, service templates.           | 5   |
| **LTI-505** | **SecOps**        | Trivy scan in CI, mTLS certificates via cert-manager & Vault.                    | 3   |

* * *



### Épica 4 – Integraciones _(Sprint 3-4)_

| Ticket      | Story            | Descripción                                                                                     | SP  |
| ----------- | ---------------- | ----------------------------------------------------------------------------------------------- | --- |
| **LTI-401** | US-10 HRIS Sync  | BambooHR connector: OAuth, delta sync cron 15 min, conflict strategy “external-source-of-truth” | 8   |
| **LTI-402** | US-10            | Webhook listener for employee updates → publish `employee.changed`.                             | 5   |
| **LTI-403** | Slack/Zoom hooks | Publish notifications to Slack channel & create Zoom links generic util.                        | 3   |

* * *

### Resumen de esfuerzo (Story Points totales)

* Core Hiring Flow: **69 SP**

* Plataforma & Seguridad: **21 SP**

* Integraciones iniciales: **16 SP**

> **Capacidad inicial**: si el equipo tiene _velocity_ target ~25 SP por sprint, cubriríamos_Sprint 0-1_: 501-505 + 101-104 (base para UI y Job flow)._Sprint 2-3_: 111-115 + 121-123._Sprint 4_: 131-132 + 141-142 + 401-403.Ajustaremos al medir velocity real.

***

> 🔢 **Capacidad inicial sugerida**: Velocity ~25 SP/sprint → cobertura estimada en 4‑5 sprints.

* * *

Diagramas ASCII
---------------

### Flujo principal de contratación

    graph TD
        A[Crear Vacante] --> B[Aplicar Candidato]
        B --> C[AI‑Screening]
        C --> D[Programar Entrevista]
        D --> E[Feedback Colaborativo]
        E --> F[Generar Oferta]
        F --> G[Onboarding]

### Vista de componentes (simplificada)

    +--------------+        Kafka         +------------------+
    |  Frontend    |  <-----------------> |   Event Bus      |
    +--------------+                     +------------------+
           | GraphQL                               |  ⬇ events
           v                                        |
    +--------------+   gRPC   +------------------+  |
    |  Job Service | <------> | Candidate Service | |
    +--------------+         +------------------+  |  
           |                                        |
           v                                        v
      PostgreSQL / pgvector                Storage (S3)

* * *

# 
