# LTI - Applicant Tracking System del Futuro

## 1. 📘 Descripción del Software

**LTI** es un sistema ATS (Applicant Tracking System) moderno, inteligente y modular que facilita el proceso de reclutamiento de extremo a extremo: desde la creación de vacantes hasta la contratación final. LTI se diferencia al integrar automatización, IA y análisis en tiempo real para tomar decisiones más rápidas y eficientes.

### 🏆 Ventajas Competitivas
- Automatización inteligente del proceso de reclutamiento.
- Análisis de datos en tiempo real sobre candidatos y procesos.
- IA para screening automático de CVs y sugerencia de candidatos.
- Integración omnicanal: web, redes sociales, job boards.
- Experiencia amigable tanto para candidatos como para reclutadores.

### 🔑 Funciones Principales
1. Crear y publicar vacantes.
2. Recibir y analizar postulaciones automáticamente.
3. Realizar pruebas y entrevistas en línea.
4. Visualizar pipelines y métricas en tiempo real.
5. Contratar y generar informes automáticos.

---

## 2. 🧩 Lean Canvas (Modelo de Negocio)

### Herramienta recomendada: [https://canvanizer.com](https://canvanizer.com)

Contenido para pegar en Canvanizer:

```
Problem:
- Procesos manuales y lentos de reclutamiento
- Dificultad para evaluar miles de CVs
- Mala experiencia del candidato

Customer Segments:
- Startups tecnológicas
- Empresas medianas en expansión
- Consultoras de recursos humanos

Unique Value Proposition:
ATS inteligente que automatiza y optimiza todo el proceso de contratación con IA, pruebas integradas y dashboards.

Solution:
- Publicación multicanal
- Screening automático por IA
- Entrevistas y pruebas online
- Pipeline visual
- Análisis de candidatos

Channels:
- Web
- LinkedIn / Social media
- Partners de RRHH
- Marketplace de ATS

Revenue Streams:
- Licencia mensual SaaS
- Add-ons: analítica avanzada, integración con CRM

Cost Structure:
- Desarrollo y mantenimiento de plataforma
- Infraestructura cloud
- Marketing y ventas

Key Metrics:
- Tiempo medio de contratación
- Tasa de conversión de postulantes
- NPS del candidato y reclutador

Unfair Advantage:
- Algoritmo propio de scoring inteligente
- Experiencia UX optimizada
```

---

## 3. 🔄 Casos de Uso Principales

### 🎯 Crear Vacante
```mermaid
sequenceDiagram
    actor Recruiter
    participant LTI
    participant JobBoard

    Recruiter->>LTI: Ingresar detalles del puesto
    LTI->>LTI: Validar y guardar vacante
    LTI->>JobBoard: Publicar en portales (Indeed, LinkedIn, etc)
    JobBoard-->>LTI: Confirmación
```

### 📥 Procesar Aplicaciones
```mermaid
sequenceDiagram
    participant Applicant
    participant LTI
    participant AI Engine

    Applicant->>LTI: Enviar CV y datos
    LTI->>AI Engine: Analizar y puntuar CV
    AI Engine-->>LTI: Score y perfil
    LTI->>Recruiter: Mostrar candidatos ordenados
```

### 📅 Entrevistar y Seleccionar
```mermaid
sequenceDiagram
    participant Recruiter
    participant LTI
    participant InterviewTool

    Recruiter->>LTI: Seleccionar candidatos para entrevista
    LTI->>InterviewTool: Programar entrevista online
    InterviewTool-->>LTI: Resultados y grabaciones
    LTI->>Recruiter: Mostrar evaluación
    Recruiter->>LTI: Contratar candidato
```

---

## 4. 🧬 Modelo de Datos

```mermaid
erDiagram
    JOB ||--o{ APPLICATION : has
    APPLICATION ||--|| CANDIDATE : submitted_by
    APPLICATION ||--o{ INTERVIEW : includes
    INTERVIEW ||--o{ TEST : contains
    CANDIDATE ||--o{ TEST_RESULT : gets
    RECRUITER ||--o{ JOB : creates

    JOB {
        string id
        string title
        string description
        string location
        datetime created_at
        string status
    }

    APPLICATION {
        string id
        string job_id
        string candidate_id
        datetime applied_at
        string status
    }

    CANDIDATE {
        string id
        string full_name
        string email
        string phone
        text resume_url
        string status
    }

    INTERVIEW {
        string id
        string application_id
        datetime scheduled_at
        string mode
        string result
    }

    TEST {
        string id
        string title
        string type
        int duration_minutes
    }

    TEST_RESULT {
        string id
        string candidate_id
        string test_id
        float score
        datetime completed_at
    }

    RECRUITER {
        string id
        string name
        string email
        string role
    }
```

---

## 5. 🏗️ Diseño de Alto Nivel

```mermaid
graph TD
    A[Web Frontend - Candidato/Reclutador]
    B[API Backend REST]
    C[DB PostgreSQL]
    D[AI Engine - Scoring/Parsing CV]
    E[Workflow Engine]
    F[External APIs - LinkedIn, Email, Video]
    
    A --> B
    B --> C
    B --> D
    B --> E
    E --> F
```

---

## 6. 🧱 Diagrama C4

### 🧭 Contexto
```mermaid
graph TD
    User((Reclutador/Candidato))
    System[LTI - Applicant Tracking System]
    JobBoards[LinkedIn / Indeed / API externas]

    User --> System
    System --> JobBoards
```

### 🧱 Contenedores
```mermaid
flowchart TD
    subgraph LTI_System
        Web[Frontend Web]
        API[API Backend]
        DB[(DB PostgreSQL)]
        AI[AI Scoring Service]
        Scheduler[Workflow Engine]
    end
    User --> Web
    Web --> API
    API --> DB
    API --> AI
    API --> Scheduler
```


### ⚙️ Componentes (API Backend)
```mermaid
graph TD
    API[API Backend]
    Auth[AuthController]
    Jobs[JobController]
    Apps[ApplicationController]
    Interview[InterviewController]
    Service[ScoringService]

    API --> Auth
    API --> Jobs
    API --> Apps
    API --> Interview
    API --> Service
```

### 💻 Código - ScoringService
```python
# scoring_service.py
import spacy

class ScoringService:
    def __init__(self, job_desc):
        self.job_desc = job_desc
        self.nlp = spacy.load("en_core_web_sm")

    def compute_score(self, resume_text):
        jd_doc = self.nlp(self.job_desc)
        res_doc = self.nlp(resume_text)
        score = jd_doc.similarity(res_doc)
        return round(score * 100, 2)
```