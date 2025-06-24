# LTI - A Smarter ATS for Modern Hiring Teams

**LTI** is a next-generation Applicant Tracking System designed for speed, simplicity, and fairness. Built for fast-growing companies and modern hiring teams, LTI removes friction from recruitment while empowering collaboration, intelligent screening, and diversity-conscious hiring.

---

## 🚀 Added Value

- **Intelligent automation** that streamlines repetitive tasks.
- **Bias-reducing tools** that promote fairer hiring.
- **Zero-friction UX** for both candidates and hiring teams.
- **Fast deployment** and seamless integrations with your existing stack.

---

## 🏆 Competitive Advantages

| Feature Area            | LTI Advantage                                           |
| ----------------------- | ------------------------------------------------------- |
| **Candidate Screening** | Skills-first matching engine with explainable AI.       |
| **Collaboration**       | Real-time feedback, async review, Slack-native.         |
| **DEI & Compliance**    | Built-in bias filters, anonymized reviews, GDPR tools.  |
| **Usability**           | Role-specific UI: recruiter, hiring manager, candidate. |
| **Extensibility**       | Open API and modular architecture.                      |

---

## 🧰 Core Functionalities

- **Job & Pipeline Management**

  - Drag-and-drop hiring pipelines
  - Multi-stage workflows with templates

- **Smart Candidate Screening**

  - AI-powered shortlisting (customizable)
  - Knockout questions and scorecards

- **Collaborative Hiring Tools**

  - Inline notes, mentions, and reminders
  - Interview scheduling with calendar sync

- **Candidate Experience**

  - One-click apply, branded pages
  - Mobile-friendly and accessible UI

- **Reporting & Analytics**

  - Time-to-hire, funnel health, DEI metrics
  - Source effectiveness tracking

- **Compliance & Privacy**
  - GDPR/EEO workflows and consent management
  - Data export, audit logs

---

## 📋 Lean Canvas

<table>
<tr>
<td colspan="2" align="center">

### 🎯 **UNIQUE VALUE PROPOSITION**

**"Hire better, faster, and fairer."**

Modern ATS with intelligent automation, built-in DEI tools, and seamless team collaboration.

</td>
<td rowspan="2" align="center">

### 🚀 **UNFAIR ADVANTAGE**

🔹 **Explainable AI** with skills-first matching  
🔹 **Native DEI** and compliance-first design  
🔹 **Real-time, async collaboration** built into hiring workflow  
🔹 **Slack-native** and modular by design

</td>
<td colspan="2" align="center">

### 👥 **CUSTOMER SEGMENTS**

🏢 **Fast-growing companies**  
💻 **Modern, tech-savvy hiring teams**  
🎯 **HR managers and recruiters**  
🌍 **DEI-conscious organizations**

</td>
</tr>
<tr>
<td align="center">

### ⚡ **KEY METRICS**

📊 Time-to-hire reduction  
📉 Candidate drop-off rates  
🎯 Adoption and engagement per feature  
🌈 DEI compliance and diversity funnel metrics

</td>
<td align="center">

### 💡 **SOLUTION**

🧠 Skills-first, explainable AI screening  
💬 Slack-native, async collaboration tools  
✨ Zero-friction UX for candidates and teams  
🛡️ DEI-first workflows and compliance tools

</td>
<td align="center">

### 🚧 **PROBLEM**

⏱️ Hiring processes are slow and inefficient  
🚫 Unconscious bias negatively impacts DEI goals  
💬 Collaboration between hiring teams is fragmented  
🗿 Legacy ATS tools are clunky and unintuitive

</td>
<td align="center">

### 📈 **CHANNELS**

📝 Inbound marketing (content, SEO, webinars)  
🤝 HR tech partnerships & marketplaces  
📞 Direct sales to startups and scaleups  
🔗 Slack and ATS integration platforms

</td>
</tr>
<tr>
<td colspan="3" align="center">

### 💰 **REVENUE STREAMS**

💳 **Subscription-based SaaS** (tiered by team size/features)  
🔧 **Add-ons** for advanced analytics, integrations, and compliance modules

</td>
<td colspan="2" align="center">

### 💸 **COST STRUCTURE**

⚙️ Product development (engineering, AI)  
🎧 Customer support and onboarding  
📢 Marketing and sales  
🔒 Infrastructure and data compliance (e.g., GDPR)

</td>
</tr>
</table>

## 📝 Use cases

Based on the LTI ATS documentation, here are the 3 principal use cases:

### 1. **🤖 Intelligent Candidate Screening & Matching**

This use case focuses on automating and improving the initial candidate evaluation process through AI-powered screening that reduces bias and focuses on skills-first matching.

```mermaid
flowchart TD
    A[Job Posted] --> B[Candidates Apply]
    B --> C[AI Skills-First Screening]
    C --> D{Knockout Questions}
    D -->|Pass| E[AI Scoring & Ranking]
    D -->|Fail| F[Auto-Reject with Feedback]
    E --> G[Bias Filter Applied]
    G --> H[Explainable AI Results]
    H --> I[Shortlist Generated]
    I --> J[Recruiter Review]
    J --> K[Move to Interview Stage]
```

### 2. **🤝 Collaborative Hiring & Team Coordination**

This use case addresses the need for seamless collaboration between hiring team members through real-time feedback, async reviews, and integrated communication tools.

```mermaid
flowchart TD
    A[Candidate in Pipeline] --> B[Hiring Manager Review]
    B --> C[Add Inline Notes & Mentions]
    C --> D[Slack Notification to Team]
    D --> E[Team Members Async Review]
    E --> F[Scorecard Completion]
    F --> G[Interview Scheduling]
    G --> H[Calendar Sync Integration]
    H --> I[Interview Conducted]
    I --> J[Real-time Feedback Collection]
    J --> K[Team Decision Meeting]
    K --> L{Hire Decision}
    L -->|Yes| M[Offer Extended]
    L -->|No| N[Rejection with Feedback]
```

### 3. **🌈 DEI-Focused Hiring & Compliance Management**

This use case centers on promoting fair hiring practices through built-in bias reduction tools, anonymized reviews, and comprehensive compliance tracking.These three use cases represent the core value propositions of LTI:

```mermaid
flowchart TD
    A[Job Posting Created] --> B[DEI Guidelines Applied]
    B --> C[Candidate Pool Analysis]
    C --> D[Diversity Metrics Tracking]
    D --> E[Anonymized Resume Review]
    E --> F[Bias Filter Screening]
    F --> G[Diverse Interview Panel]
    G --> H[Structured Interview Process]
    H --> I[EEO Data Collection]
    I --> J[GDPR Consent Management]
    J --> K[Decision Audit Trail]
    K --> L[DEI Reporting Dashboard]
    L --> M[Compliance Export]
    M --> N[Continuous Improvement]
```

## 🗄️ Data model

```mermaid
erDiagram
    %% Core User Management
    User {
        string id PK
        string email
        string first_name
        string last_name
        string phone
        enum role "recruiter|hiring_manager|admin|interviewer"
        datetime created_at
        datetime updated_at
        boolean is_active
    }

    %% Company/Organization
    Company {
        string id PK
        string name
        string domain
        json branding_settings
        json compliance_settings
        datetime created_at
        datetime updated_at
    }

    %% Job Postings
    Job {
        string id PK
        string company_id FK
        string created_by_user_id FK
        string title
        text description
        text requirements
        string location
        enum employment_type "full_time|part_time|contract|internship"
        enum status "draft|active|paused|closed"
        json salary_range
        datetime posted_at
        datetime expires_at
        datetime created_at
        datetime updated_at
    }

    %% Hiring Pipeline Templates
    PipelineTemplate {
        string id PK
        string company_id FK
        string name
        text description
        json stages_config
        boolean is_default
        datetime created_at
        datetime updated_at
    }

    %% Pipeline Stages
    PipelineStage {
        string id PK
        string pipeline_template_id FK
        string name
        text description
        int order_index
        enum stage_type "screening|phone|interview|assessment|offer|hired|rejected"
        json automation_rules
        datetime created_at
        datetime updated_at
    }

    %% Candidates
    Candidate {
        string id PK
        string email
        string first_name
        string last_name
        string phone
        text resume_text
        string resume_file_url
        json skills
        json experience
        text cover_letter
        enum source "job_board|referral|direct|linkedin|other"
        string source_details
        json gdpr_consent
        datetime created_at
        datetime updated_at
    }

    %% Job Applications
    Application {
        string id PK
        string job_id FK
        string candidate_id FK
        string current_stage_id FK
        enum status "new|screening|in_progress|offer|hired|rejected|withdrawn"
        json application_data
        decimal ai_score
        json screening_answers
        datetime applied_at
        datetime last_activity_at
        datetime created_at
        datetime updated_at
    }

    %% Application Stage History
    ApplicationStageHistory {
        string id PK
        string application_id FK
        string stage_id FK
        string moved_by_user_id FK
        enum action "moved_to|rejected_at|hired_at"
        text notes
        datetime created_at
    }

    %% Interviews
    Interview {
        string id PK
        string application_id FK
        string interviewer_id FK
        string scheduled_by_user_id FK
        datetime scheduled_at
        int duration_minutes
        enum type "phone|video|onsite|technical"
        enum status "scheduled|completed|cancelled|no_show"
        text meeting_link
        text location
        json feedback
        decimal score
        datetime created_at
        datetime updated_at
    }

    %% Feedback and Notes
    Feedback {
        string id PK
        string application_id FK
        string user_id FK
        string interview_id FK "nullable"
        enum type "note|interview_feedback|screening_feedback|reference_check"
        text content
        json structured_data
        decimal score
        boolean is_anonymous
        datetime created_at
        datetime updated_at
    }

    %% Scorecards for Structured Evaluation
    Scorecard {
        string id PK
        string job_id FK
        string created_by_user_id FK
        string name
        json criteria
        boolean is_active
        datetime created_at
        datetime updated_at
    }

    %% Scorecard Evaluations
    ScorecardEvaluation {
        string id PK
        string scorecard_id FK
        string application_id FK
        string evaluator_id FK
        json scores
        decimal total_score
        text comments
        datetime completed_at
        datetime created_at
    }

    %% Communication Log
    Communication {
        string id PK
        string application_id FK
        string sender_id FK
        enum type "email|sms|system_notification"
        string subject
        text content
        enum status "sent|delivered|opened|failed"
        datetime sent_at
        datetime created_at
    }

    %% Analytics and Reporting
    JobMetrics {
        string id PK
        string job_id FK
        int total_applications
        int applications_by_stage
        decimal avg_time_to_hire
        json source_breakdown
        json diversity_metrics
        datetime calculated_at
        datetime created_at
    }

    %% Integration Logs
    IntegrationLog {
        string id PK
        string entity_type
        string entity_id
        string integration_name
        enum action "sync|create|update|delete"
        json payload
        enum status "success|failed|pending"
        text error_message
        datetime created_at
    }

    %% Relationships
    Company ||--o{ User : employs
    Company ||--o{ Job : posts
    Company ||--o{ PipelineTemplate : defines

    PipelineTemplate ||--o{ PipelineStage : contains

    User ||--o{ Job : creates
    User ||--o{ Interview : conducts
    User ||--o{ Feedback : provides
    User ||--o{ Scorecard : creates
    User ||--o{ ScorecardEvaluation : completes
    User ||--o{ ApplicationStageHistory : moves
    User ||--o{ Communication : sends

    Job ||--o{ Application : receives
    Job ||--o{ Scorecard : uses
    Job ||--o{ JobMetrics : tracks

    Candidate ||--o{ Application : submits

    Application ||--o{ Interview : schedules
    Application ||--o{ Feedback : receives
    Application ||--o{ ScorecardEvaluation : evaluated_by
    Application ||--o{ ApplicationStageHistory : tracks
    Application ||--o{ Communication : generates

    PipelineStage ||--o{ Application : current_stage
    PipelineStage ||--o{ ApplicationStageHistory : stage_history

    Interview ||--o{ Feedback : generates

    Scorecard ||--o{ ScorecardEvaluation : evaluated_with
```

## 🏗️ High level Design

The high level architecture is define in [system-architecture.md](system-architecture.md)

## 🔍 Skills matching service C4 diagrams

### Context Diagram

![System Context Diagram](C4-diagrams/System%20Context%20Diagram%20for%20Skills%20Matching%20Service%20-%20LTI%20ATS.png)

### Container Diagram

![Container Diagram](C4-diagrams/Container%20Diagram%20for%20Skills%20Matching%20Service%20-%20LTI%20ATS.png)

### Component Diagram

![Component Diagram](C4-diagrams/Component%20Diagram%20for%20Skills%20Matching%20Engine%20-%20LTI%20ATS.png)

### Code Diagram

![Code Diagram](C4-diagrams/Code%20Diagram%20for%20Skills%20Matching%20Service%20-%20LTI%20ATS.png)
