# 📘 Documentación del sistema ATS: LTI (Local Talent Intelligence)

## 🧠 Descripción general del producto

**LTI** es un sistema de seguimiento de candidatos (*Applicant Tracking System*) orientado a departamentos de RRHH de empresas de cualquier tamaño. Su objetivo principal es optimizar los procesos de selección, automatizar tareas repetitivas y reducir el *time-to-hire*. Se diseñará como un servicio **enterprise** personalizado, con foco en la **integración con LinkedIn y ERP internos**, cumpliendo además con el **RGPD**. Incorporará funcionalidades de inteligencia artificial para mejorar la eficiencia en la contratación.

---

## 🎯 Valor añadido y ventajas competitivas

### Funciones clave:
- Gestión centralizada de vacantes, candidatos y procesos.
- Parsing inteligente de CVs con extracción semántica.
- Matching automático entre candidatos y ofertas (IA).
- Feedback estructurado de entrevistas y comparativas.
- Dashboard con métricas como *time-to-hire*, *fit score*, y más.
- Publicación en LinkedIn e integración con ERP.
- Cumplimiento completo con el RGPD: consentimiento, auditoría y borrado.

### Ventajas competitivas:
- Enfoque enterprise y modular.
- Automatización profunda de tareas operativas.
- Integración bidireccional con ERP (no solo portales de empleo).
- Inteligencia artificial aplicada desde el diseño.
- Soporte europeo con cumplimiento RGPD por defecto.

---

## 🧩 Lean Canvas

| Sección               | Descripción                                                                                                                                 |
|------------------------|---------------------------------------------------------------------------------------------------------------------------------------------|
| **Problema**           | Procesos de selección largos, manuales y con baja visibilidad. Difícil conexión entre vacantes y talento interno.                          |
| **Segmentos cliente**  | Departamentos de RRHH de empresas medianas y grandes.                                                                                       |
| **Propuesta de valor** | ATS inteligente, automatizado e integrado que mejora la calidad y velocidad del proceso de contratación.                                   |
| **Solución**           | Plataforma con IA, flujos automatizados, integraciones ERP y LinkedIn, y métricas en tiempo real.                                          |
| **Ventaja diferencial**| Foco en ERP, RGPD, IA propietaria y personalización enterprise.                                                                             |
| **Canales**            | Ventas directas B2B, partnerships con consultoras de RRHH, eventos y ferias sectoriales.                                                    |
| **Ingresos**           | Licencia anual por empresa, onboarding personalizado, soporte premium.                                                                     |
| **Costes**             | Desarrollo, infraestructura cloud, mantenimiento, comercialización, legal/GDPR.                                                             |
| **Métricas clave**     | Nº de procesos gestionados, reducción de *time-to-hire*, % de candidatos recomendados por IA, % de integración ERP completada.             |

---

## 📚 Casos de uso principales

### 🧩 Caso 1: Publicar una vacante conectada al ERP

**Actor principal**: Responsable de RRHH  
**Objetivo**: Crear una vacante sincronizada con una necesidad del ERP.

**Flujo:**
1. El responsable accede al sistema y pulsa “Nueva vacante”.
2. Selecciona una necesidad del ERP (por ejemplo, puesto técnico abierto).
3. Se autocompletan campos como sede, departamento y tipo de contrato.
4. Se editan o añaden requisitos específicos.
5. Se publica en LinkedIn y/o en el portal interno.

---

### 🧩 Caso 2: Evaluar candidatos con IA y feedback colaborativo

**Actor principal**: Reclutador y entrevistadores  
**Objetivo**: Filtrar candidatos y colaborar en su evaluación.

**Flujo:**
1. El sistema puntúa automáticamente los candidatos recibidos.
2. El reclutador revisa y selecciona a los más prometedores.
3. Se agendan entrevistas directamente desde el sistema.
4. Los entrevistadores completan un formulario estandarizado.
5. Se calcula un *fit score* global y se muestran finalistas recomendados.

---

### 🧩 Caso 3: Cerrar proceso y enviar feedback automatizado

**Actor principal**: Responsable de RRHH  
**Objetivo**: Cerrar un proceso y comunicar resultados.

**Flujo:**
1. Se selecciona al candidato final.
2. Se marca la vacante como "cerrada".
3. Se genera feedback automatizado para candidatos no seleccionados.
4. Se sincroniza la información con el ERP para actualizar estructura interna.
5. Se guarda toda la información para métricas y auditoría.

---

## 🗃️ Modelo de datos inicial (simplificado)

```sql
-- Tabla de candidatos
CREATE TABLE Candidate (
  CandidateId UUID PRIMARY KEY,
  FullName TEXT,
  Email TEXT,
  Phone TEXT,
  LinkedInURL TEXT,
  CV TEXT, -- URL o blob
  GDPRConsentDate DATE,
  CreatedAt TIMESTAMP
);

-- Tabla de vacantes
CREATE TABLE JobPosting (
  JobId UUID PRIMARY KEY,
  Title TEXT,
  Department TEXT,
  Location TEXT,
  ERPReferenceId TEXT,
  Status TEXT, -- Open, Closed, Draft
  PublishedAt TIMESTAMP,
  CreatedBy UUID -- FK a User
);

-- Aplicaciones de candidatos a vacantes
CREATE TABLE Application (
  ApplicationId UUID PRIMARY KEY,
  CandidateId UUID REFERENCES Candidate(CandidateId),
  JobId UUID REFERENCES JobPosting(JobId),
  Source TEXT, -- LinkedIn, Manual, Referral
  FitScore FLOAT,
  AppliedAt TIMESTAMP,
  Status TEXT -- New, Interviewing, Rejected, Hired
);

-- Entrevistas realizadas
CREATE TABLE Interview (
  InterviewId UUID PRIMARY KEY,
  ApplicationId UUID REFERENCES Application(ApplicationId),
  InterviewerId UUID REFERENCES User(UserId),
  ScheduledAt TIMESTAMP,
  Score INTEGER,
  Comments TEXT
);

-- Usuarios del sistema
CREATE TABLE User (
  UserId UUID PRIMARY KEY,
  Name TEXT,
  Email TEXT,
  Role TEXT -- HR, Interviewer, Admin
);

# 📐 Diseño del sistema LTI – Alto Nivel

LTI (Local Talent Intelligence) es un sistema ATS (Applicant Tracking System) que optimiza los procesos de selección y reduce el time-to-hire. Está diseñado como una solución SaaS modular, cloud-native, y orientada a empresas que desean integrar su flujo de contratación con plataformas como LinkedIn y sus propios ERPs.

## 🧱 Componentes principales

| Componente                | Descripción                                                                                                                                   |
|---------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| Frontend Web              | Aplicación SPA (React) para el equipo de RRHH, entrevistadores y administradores.                                                            |
| API REST (LTI API)        | Servicio backend principal. Expone todos los endpoints funcionales, gestiona seguridad, lógica de negocio y validaciones.                   |
| Base de datos             | PostgreSQL o SQL Server. Contiene la información de usuarios, vacantes, candidatos, entrevistas, etc.                                        |
| Motor de IA               | Microservicio (FastAPI o Flask) encargado del matching semántico, análisis de CV y priorización de candidatos.                              |
| Módulo LinkedIn           | Sincroniza ofertas y candidaturas a través de la API oficial de LinkedIn.                                                                   |
| Conector ERP              | Servicio que intercambia información de procesos y personas con sistemas ERP (SAP, Dynamics, etc.).                                          |
| Servicio de autenticación| Azure AD B2C o IdentityServer4 para login, gestión de usuarios y roles.                                                                     |
| Registro RGPD             | Servicio que audita eventos relacionados con el tratamiento de datos personales.                                                             |
| Event Bus (opcional)      | Permite comunicación desacoplada entre servicios y ejecución de tareas asincrónicas (notificaciones, logging, etc.).                        |

---

# 🧭 C4 - Nivel 1: Diagrama de Contexto

## Actores externos

- **Responsable de RRHH**: Crea ofertas, revisa candidatos, programa entrevistas.
- **Entrevistador**: Evalúa candidatos asignados y registra observaciones.
- **Candidato**: Aplica a vacantes a través de LinkedIn o canales corporativos.
- **ERP corporativo**: Envía y recibe datos relacionados con vacantes, contrataciones y personas.
- **LinkedIn**: Fuente de candidatos y canal de publicación.

## Sistema central (LTI)

El sistema LTI actúa como núcleo de gestión de procesos de selección, comunicándose con todos los actores y fuentes externas, garantizando cumplimiento legal (RGPD) y proporcionando trazabilidad, inteligencia y automatización.

---

# 🧱 C4 - Nivel 2: Diagrama de Contenedores

| Contenedor               | Tecnología                | Funcionalidad                                                                 |
|--------------------------|---------------------------|------------------------------------------------------------------------------|
| Frontend Web             | React + TypeScript        | Interfaz principal para usuarios internos.                                  |
| LTI API REST             | .NET Core / Node.js       | Capa central de negocio, acceso a datos y lógica de procesos.               |
| Base de datos            | PostgreSQL / SQL Server   | Almacén persistente de entidades de negocio y logs.                         |
| Motor de IA              | Python + FastAPI          | Scoring semántico de candidaturas y sugerencias automáticas.                |
| Módulo LinkedIn          | Node.js / Python           | Publicación de ofertas y recepción de candidaturas desde LinkedIn.          |
| Conector ERP             | .NET / Java               | Sincronización con ERP interno.                                             |
| Servicio de autenticación| Azure AD B2C / IdentitySrv| Gestión de usuarios, permisos y sesiones seguras.                           |
| Event Bus (opcional)     | Azure Service Bus / Kafka | Comunicación entre servicios para tareas asincrónicas.                      |

---

# ⚙️ C4 - Nivel 3: Componentes internos de la API LTI

| Componente              | Función                                                                                      |
|-------------------------|-----------------------------------------------------------------------------------------------|
| `AuthController`        | Inicio/cierre de sesión, gestión de roles y permisos.                                         |
| `CandidateController`   | Alta, baja y modificación de candidatos. Manejo de CVs y consentimiento RGPD.                |
| `JobController`         | Creación, edición, publicación y cierre de vacantes.                                          |
| `ApplicationController` | Registro de candidaturas, asignación de estado, obtención de scoring IA.                     |
| `InterviewController`   | Planificación de entrevistas, carga de evaluaciones.                                          |
| `ERPService`            | Obtención y sincronización de datos con el ERP.                                               |
| `LinkedInService`       | Envío y recepción de información desde la plataforma de LinkedIn.                             |
| `MatchingEngineClient`  | Comunicación con el motor de IA para obtener FitScore o recomendaciones.                      |
| `GDPRLogger`            | Registro de acciones sensibles según normativa de protección de datos.                        |
| `Repository Layer`      | Abstracción de acceso a la base de datos (repositories, UoW).                                 |
| `NotificationService`   | Publicación de eventos y notificaciones (entrevistas, candidaturas, recordatorios, alertas). |

---

## 🔹 C4 - Nivel 4: `MatchingEngine` (Motor de IA)

### 📌 Contenedor: `MatchingEngine`

> Subcomponente interno del sistema LTI encargado de calcular el grado de compatibilidad entre candidatos y ofertas laborales mediante procesamiento de lenguaje natural e inteligencia artificial.

---

### 🧱 Componentes internos

| Componente              | Tecnología                | Descripción                                                                 |
|--------------------------|---------------------------|-----------------------------------------------------------------------------|
| `Scoring API`            | Python (FastAPI)          | Expone los endpoints REST para solicitar el cálculo de compatibilidad.     |
| `CV Parser`              | spaCy / PyPDF2            | Extrae y limpia texto desde CVs en PDF, Word u otros formatos.             |
| `Embeddings Generator`   | Transformers (HuggingFace) | Convierte texto en vectores semánticos usando modelos como BERT/SBERT.     |
| `Job Matching Core`      | Python puro               | Calcula la similitud entre vectores de CV y oferta mediante similitud de coseno. |
| `Matching DataStore`     | MongoDB                   | Guarda embeddings y resultados de matching históricos.                     |
| `IA Audit Log`           | Logging interno           | Registra toda actividad del motor, garantizando trazabilidad y cumplimiento (RGPD). |

---

### 🔁 Flujo de ejecución

1. **Petición de scoring**:
   - La API REST del sistema LTI o un sistema externo invoca el endpoint de `Scoring API`, proporcionando el CV y la oferta.

2. **Procesamiento del CV**:
   - `Scoring API` pasa el archivo a `CV Parser`, que extrae texto plano y lo normaliza.

3. **Generación de embeddings**:
   - El texto procesado del CV y la descripción de la oferta se envían a `Embeddings Generator`, que genera vectores semánticos.

4. **Cálculo de compatibilidad**:
   - `Job Matching Core` recibe los embeddings y calcula una **puntuación de afinidad** (por ejemplo, usando similitud de coseno).

5. **Persistencia**:
   - El resultado se guarda en `Matching DataStore` para análisis posterior o reutilización.
   - `IA Audit Log` registra el proceso completo (inputs, outputs, decisión) para garantizar trazabilidad.

---