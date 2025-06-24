# 📌 LTI — Refined Core User Stories

All stories follow best practices: clear _who/what/why_, acceptance criteria in
Given/When/Then, business value, dependencies, and assumptions.

---

## ✅ 1. Create a Job Opening

**User Story:**  
_As a recruiter, I want to create a new job opening draft with all relevant
details, so that I can prepare vacancies before they go live._

**Acceptance Criteria:**  
Given I am logged in as a recruiter, When I enter a job title, description,
location, requirements, and save, Then the job opening is saved as a draft And
is not yet visible on the careers page.

**Business Value:**  
Enables recruiters to prepare and edit job openings without immediately
publishing, supporting review and approvals.

**Dependencies:**  
Draft storage, user authentication.

**Assumptions:**  
Multiple drafts per recruiter are supported.

---

## ✅ 2. Publish a Job Opening

**User Story:**  
_As a recruiter, I want to publish a drafted job opening to my company’s careers
page, so that I can make it available to potential candidates._

**Acceptance Criteria:**  
Given I have a saved job draft, When I click "Publish", Then the job opening
becomes visible on the company’s careers page And candidates can apply
immediately.

**Business Value:**  
Controls when job postings go live, ensuring only approved openings are visible
externally.

**Dependencies:**  
Company careers page integration.

**Assumptions:**  
No external job board posting for MVP.

---

## ✅ 3. AI-Powered Resume Parsing & Candidate Matching

**User Story:**  
_As a recruiter, I want the AI to parse incoming resumes, enrich profiles with
public data, and suggest matches for open jobs, so that I can quickly shortlist
the best candidates and approve them._

**Acceptance Criteria:**  
Given candidates have applied for a job, When the AI parses resumes and enriches
profiles, Then I see a ranked list of suggested matches, And I can approve or
reject each, And approved candidates move to the shortlist pipeline.

**Business Value:**  
Automates tedious screening, highlighting LTI’s AI-first advantage.

**Dependencies:**  
Resume parser, data enrichment, matching algorithm, UI for review.

**Assumptions:**  
Recruiters have final say; data use complies with privacy laws.

---

## ✅ 4. Manage Candidate Pipeline Stages

**User Story:**  
_As a recruiter, I want to move candidates through pipeline stages (e.g.,
Applied → Interview → Offer), so that I can track their progress and collaborate
with the hiring team._

**Acceptance Criteria:**  
Given a candidate is in the pipeline, When I drag and drop them to a new stage,
Then their status updates accordingly And this is visible to other team members.

**Business Value:**  
Provides clear visibility and control over the hiring funnel.

**Dependencies:**  
Drag-and-drop UI, real-time updates.

**Assumptions:**  
Team members have shared pipeline access.

---

## ✅ 5. Schedule Interviews

**User Story:**  
_As a recruiter, I want to schedule interviews and sync them with team
calendars, so that I can coordinate availability without manual back-and-forth._

**Acceptance Criteria:**  
Given a candidate is ready for interview, When I select time slots and
participants, And confirm the schedule, Then invites are sent and appear on
calendars.

**Business Value:**  
Saves time and improves the candidate experience.

**Dependencies:**  
Calendar API integration (e.g., Google, Outlook).

**Assumptions:**  
Team uses supported calendar services.

---

## ✅ 6. Team Comments & Notes

**User Story:**  
_As a recruiter or manager, I want to leave comments and notes on candidate
profiles, so that the team can share feedback and make informed hiring
decisions._

**Acceptance Criteria:**  
Given I am viewing a candidate profile, When I add a comment or note, Then it is
visible to authorized team members And persists for future reference.

**Business Value:**  
Facilitates collaboration and informed decision-making.

**Dependencies:**  
Commenting system, permissions.

**Assumptions:**  
Comments remain internal.

---

## ✅ 7. Candidate Consent & Data Privacy Compliance

**User Story:**  
_As a candidate, I want to give explicit consent for my data to be stored and
used for hiring and AI enrichment, so that my privacy rights are protected._

**Acceptance Criteria:**  
Given I submit an application, When I review and accept the privacy consent
form, Then my data is stored securely And only used according to stated
policies.

**Business Value:**  
Ensures compliance with data privacy laws and builds candidate trust.

**Dependencies:**  
Consent mechanism, secure storage.

**Assumptions:**  
Compliant with GDPR, CCPA, or equivalent.

---

## ✅ 8. Recruiter Dashboard

**User Story:**  
_As a recruiter, I want a dashboard showing active jobs, candidate counts, and
pipeline statuses, so that I have a clear overview of my recruitment
activities._

**Acceptance Criteria:**  
Given I log in as a recruiter, When I open my dashboard, Then I see active job
openings, number of candidates per stage, And alerts for pending actions.

**Business Value:**  
Central hub for productivity and status tracking.

**Dependencies:**  
Data aggregation, user-specific views.

**Assumptions:**  
Real-time updates available.
