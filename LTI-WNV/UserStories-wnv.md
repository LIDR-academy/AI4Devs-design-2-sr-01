# 📘 LTI ATS – MVP User Stories

---

## ✅ User Story 1: Resume Upload & Auto-Fill (Candidate)

**User Story**  
_As a candidate, I want to upload my resume and auto-fill my profile so that I can quickly apply without manually entering all my information._

**Description**  
Candidates should be able to upload a résumé (PDF/DOC), which the system then parses using the AI Resume Parser and pre-fills the candidate profile. This improves candidate experience and accelerates the apply process.

### ✅ Acceptance Criteria

- **Given** I’m on the job application page,  
  **When** I upload a valid résumé file,  
  **Then** the system extracts and displays pre-filled profile fields.

- **Given** the extracted data looks incorrect,  
  **When** I click “Edit,”  
  **Then** I can update the auto-filled fields manually.

- **Given** I complete and submit the form,  
  **When** the system processes the submission,  
  **Then** I see a confirmation message and my application is saved.

### 🔧 Tasks

- Integrate File Upload UI (PDF/DOC support)
- Connect to Resume Parser API
- Map extracted fields to Candidate DB schema
- Enable editing of parsed fields before submission
- Store structured candidate profile and resume URL

### 📝 Notes

- Resume parsing handled by a containerized ML system (NLP → ML Model → Formatter).
- Ensure data validation on fields like email, phone.
- Store parsed resumes in S3 with signed URLs.
- Error handling for unsupported/resume parsing failure.

---

## ✅ User Story 2: Ranked Applicants View (Recruiter)

**User Story**  
_As a recruiter, I want to view a ranked list of applicants for a job so that I can prioritize the most relevant candidates quickly._

**Description**  
Recruiters need a ranked view of candidates based on job fit. The AI Matching Engine ranks applicants using job descriptions + parsed resume data and displays the list sorted by relevance.

### ✅ Acceptance Criteria

- **Given** I’m viewing applicants for a job,  
  **When** I load the candidate list,  
  **Then** candidates are shown in ranked order (best-fit at top).

- **Given** I click on a candidate profile,  
  **When** it loads,  
  **Then** I see their parsed résumé, score, and key fit highlights.

- **Given** multiple applicants are tied,  
  **Then** the system shows them grouped with the same score.

### 🔧 Tasks

- Implement API call to fetch applicants per job
- Interface with AI Matching Engine to return ranked results
- Display sortable list UI (default sort: score descending)
- Fetch and display parsed résumé + job fit data on profile view

### 📝 Notes

- Ranking is based on AI model scoring.
- Recruiter role must be authenticated to access this view.
- Pulls in job description + candidate profiles from DB before sending to AI service.
- MVP may use basic TF-IDF/NLP match before advanced ML rollout.


## ✅ User Story 3: Interview Scheduling (Recruiter)

**User Story**  
_As a recruiter, I want to schedule interviews with candidates and invite interviewers so that the process is fast, coordinated, and visible to all parties._

**Description**  
Recruiters should be able to select available time slots, choose interviewers, and send calendar invites directly from the platform. This reduces back-and-forth and improves transparency across the team.

### ✅ Acceptance Criteria

- **Given** I’m on a candidate’s profile,  
  **When** I click “Schedule Interview,”  
  **Then** I can choose time slots and assign one or more interviewers.

- **Given** I confirm the schedule,  
  **When** I submit,  
  **Then** the system sends invites to the candidate and interviewers with calendar links.

- **Given** an interviewer declines,  
  **Then** I receive a notification to reschedule or reassign.

### 🔧 Tasks

- Integrate calendar picker UI with availability inputs
- Link with interviewer user accounts and roles
- Generate and send calendar invites via integrated email/calendar API
- Save interview event metadata to DB
- Handle rescheduling logic (declines, time conflicts)

### 📝 Notes

- Requires calendar API integration (e.g., Google or Outlook)
- Interview rounds/types should be taggable (e.g., “Tech Screen”)
- Must account for time zone handling

---

## ✅ User Story 4: Application Status Tracking (Candidate)

**User Story**  
_As a candidate, I want to view the current status of my application so that I know where I stand in the process._

**Description**  
After submitting a job application, candidates should be able to log in and view a clear status like “Submitted,” “Under Review,” “Interview Scheduled,” or “Rejected.” This reduces uncertainty and improves transparency.

### ✅ Acceptance Criteria

- **Given** I log into my dashboard,  
  **When** I view my job applications,  
  **Then** I see the status for each one.

- **Given** the recruiter updates the status,  
  **Then** the change is reflected in the candidate’s view within 1 minute.

- **Given** my application is rejected,  
  **Then** I see a clear message and can no longer submit updates for that job.

### 🔧 Tasks

- Create candidate dashboard UI
- Connect application statuses from backend DB
- Define and implement allowed status states
- Trigger UI update logic on status change events
- Handle state transitions securely (permissions & logging)

### 📝 Notes

- Backend should use a controlled status enum (e.g., SUBMITTED, SCREENING, INTERVIEW, OFFER, REJECTED)
- Frontend may show simplified/translated labels (e.g., “In Review”)
- Candidates must only see their own application statuses

