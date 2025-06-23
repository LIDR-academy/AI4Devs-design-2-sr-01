# 📦 Week 05 – Backlog and User Stories (LTI Applicant Tracking System)

## 🧩 1. User Stories

### LTI-01 – Create & Publish Job Vacancy _(Sprint 1 – MVP Core)_
**Story**: As an HR Manager, I want to create and publish a job vacancy on external job boards via LTI, so that the offer appears instantly on both external boards and our internal pipeline.  
**Acceptance Criteria (Gherkin)**:
- Given I am authenticated as an HR Manager, When I complete all required fields and click “Publish”, Then the job appears in the internal LTI pipeline and on the selected job boards.  
**Priority**: Must  
**Effort (t-shirt)**: M  
**Dependencies**: –  
**Notes / Assumptions**: Requires Job Board API integration.  
**Definition of Done**: POST /jobs endpoint, validated React UI, successful job board publication, unit and integration tests.

---

### LTI-02 – Collaborative Candidate Evaluation _(Sprint 1 – MVP Core)_
**Story**: As an HR or Hiring Manager, I want to rate and comment on a candidate from the same card, so that we can quickly decide whether to move forward or reject.  
**Acceptance Criteria (Gherkin)**:
- Given a candidate in the “Screening” phase, When HR and Manager provide feedback and select “Advance” or “Reject”, Then the candidate's status updates and the decision is recorded.  
**Priority**: Must  
**Effort (t-shirt)**: M  
**Dependencies**: LTI-01  
**Notes / Assumptions**: Real-time notifications for the other role.  
**Definition of Done**: React comment component, PATCH /applications/{id}, WebSocket/Push, tests.

---

### LTI-03 – Schedule Interview & Hire Decision _(Sprint 2 – Candidate Flow)_
**Story**: As an HR Manager, I want to schedule an interview and register the final decision, so I can close the position and send the offer automatically.  
**Acceptance Criteria (Gherkin)**:
- Given a candidate in the “Interviewing” phase, When I select “Schedule interview”, pick a slot, and mark “Hire”, Then the system syncs with Google Calendar and sends the offer to the candidate.  
**Priority**: Should  
**Effort (t-shirt)**: M  
**Dependencies**: LTI-01, LTI-02  
**Definition of Done**: Google Calendar API integration, offer email/PDF, vacancy marked “closed”, test coverage.

---

### LTI-04 – AI-Driven Candidate Scoring _(Sprint 3 – Automation)_
**Story**: As a Manager, I want the system to automatically assign a score to each candidate using AI trained on our feedback, so I can prioritize top profiles without reading all CVs.  
**Acceptance Criteria (Gherkin)**:
- Given a new candidate, When their CV is uploaded or imported from LinkedIn, Then the system calculates and displays their score before human review.  
**Priority**: Could  
**Effort (t-shirt)**: L  
**Dependencies**: LTI-02  
**Notes / Assumptions**: Incremental ML model; internal beta.  
**Definition of Done**: Scoring service, endpoint, score badge in UI, A/B feature flag, tests.

---

### LTI-05 – Automated Candidate Notifications _(Sprint 3 – Automation)_
**Story**: As a Candidate, I want to receive automatic emails when my status changes, so I know where I am in the process without needing to ask.  
**Acceptance Criteria (Gherkin)**:
- Given my application moves to a new phase, When the status is updated, Then I receive an email with the new status and next steps.  
**Priority**: Could  
**Effort (t-shirt)**: S  
**Dependencies**: LTI-01  
**Definition of Done**: Trigger on status change, SendGrid integration, email template, unit test for mailer.

---

## 🗂️ 2. Product Backlog (prioritized with MoSCoW)

| ID       | Epic               | Story Summary                                | Sprint                   | Priority | Effort | Dependencies     | Status |
|----------|--------------------|----------------------------------------------|--------------------------|----------|--------|------------------|--------|
| LTI-01   | Recruitment Core   | Create and publish job vacancy               | Sprint 1 – MVP Core      | Must     | M      | –                | To Do  |
| LTI-02   | Recruitment Core   | Collaborative candidate evaluation           | Sprint 1 – MVP Core      | Must     | M      | LTI-01           | To Do  |
| LTI-03   | Recruitment Core   | Schedule interview and hire                  | Sprint 2 – Candidate Flow| Should   | M      | LTI-01, LTI-02   | To Do  |
| LTI-04   | Automation & AI    | AI-based candidate scoring                   | Sprint 3 – Automation    | Could    | L      | LTI-02           | To Do  |
| LTI-05   | Automation & AI    | Automated candidate notifications            | Sprint 3 – Automation    | Could    | S      | LTI-01           | To Do  |

---

## 💬 3. Prompts used and conclusion

### Prompt #1 – General
```
"From the attached PRD, list user stories for an ATS."
```
- Result: Flat list, no structure, MoSCoW or effort estimation.  
- Conclusion: Too generic.

### Prompt #2 – Semi-structured
```
"Draft 5 user stories in Spanish using ‘Como/quiero/para’, include MoSCoW priority and t-shirt effort."
```
- Result: Valid stories but lacked sprint/epic context.  
- Conclusion: Still too vague.

### ✅ Prompt #3 – Final (most effective)
```
Use the document LTI-ASM.md to generate 5 user stories using this full template: [full template]. Assign MoSCoW priority, t-shirt sizing, logical dependencies, and suggest sprint names in the format ‘Sprint N – topic’. Return in a Markdown table with columns: ID, Epic, Story, Sprint, Priority, Effort, Dependencies, Status=To Do.
```
- Result: Complete and well-formatted stories, cleanly structured backlog.  
- Conclusion: Most effective due to combining structure (template + table) and guided content. Reduced ambiguity and ensured consistency.

---

## 🧩 4. Technical tickets + estimation (Story LTI-03)

### Decomposed Story: LTI-03 – Schedule Interview & Hire Decision

| Ticket ID     | Type        | Description                                                                | Effort (t-shirt) | Status |
|---------------|-------------|-----------------------------------------------------------------------------|------------------|--------|
| LTI-03-T1     | Backend     | POST /interviews endpoint: create interview and store availability         | M                | To Do  |
| LTI-03-T2     | Backend     | Integrate Google Calendar API to book time slot and send invite            | M                | To Do  |
| LTI-03-T3     | Frontend    | React widget to pick time slot (DateTime Picker + availability)            | M                | To Do  |
| LTI-03-T4     | Notification| Email “Interview scheduled” via SendGrid + automatic offer                 | S                | To Do  |
| LTI-03-T5     | QA          | Unit + integration tests (endpoint + calendar), validate acceptance criteria| S                | To Do  |