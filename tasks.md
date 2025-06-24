# 📌 LTI — Detailed Work Tickets for **Publish a Job Opening**

This breakdown ensures **Create** and **Publish** can be developed **in parallel** by formalizing the shared API contract up front. Mocking allows frontend work to proceed without backend blockers. Includes a dedicated task for writing the Gherkin E2E spec first.

---

## ✅ **Work Tickets**

### 1️⃣ **Formalize API Agreement**

**Description:**  
Define the REST API contract for both *Create Job Opening* and *Publish Job Opening*. Specify request payloads, status codes, validation rules, and example responses. Document this in the API reference.

**Acceptance:**  
- Shared and version-controlled API spec (e.g., OpenAPI or Swagger).
- Approved by backend & frontend developers.

**Story Points:** 3

---

### 2️⃣ **API Endpoint: Publish Job Opening**

**Description:**  
Implement `POST /jobs/:id/publish` backend endpoint. Update job status, validate job completeness, return success/errors.

**Acceptance:**  
- Changes job status to `published` in DB.
- Fails gracefully if draft is incomplete.

**Dependencies:**  
- Uses agreed API spec.

**Story Points:** 5

---

### 3️⃣ **Frontend: Publish Button & Confirmation**

**Description:**  
Add “Publish” button to job draft UI. Call the publish API (mock until real). Show loading, success, or error feedback.

**Acceptance:**  
- Button disabled if job is already published.
- User gets clear feedback.

**Dependencies:**  
- API spec and mocked API.

**Story Points:** 3

---

### 4️⃣ **Server-Side Careers Page Update**

**Description:**  
Ensure server-rendered careers page fetches only `published` jobs. Invalidate cache or SSR output when status changes.

**Acceptance:**  
- Newly published jobs visible immediately.
- No stale cache issues.

**Dependencies:**  
- Publish status in DB.

**Story Points:** 5

---

### 5️⃣ **Audit Logging**

**Description:**  
Log “Job published” events: who published, job ID, and timestamp.

**Acceptance:**  
- Log created only on actual status change.

**Dependencies:**  
- Publish API implementation.

**Story Points:** 2

---

### 6️⃣ **Gherkin E2E Spec**

**Description:**  
Write the Gherkin feature file describing the end-to-end flow:  
*Create draft → Publish draft → Verify on careers page → Verify audit log.*

**Acceptance:**  
- Gherkin file versioned with test code.
- Reviewed by QA and dev team.

**Dependencies:**  
- None — can be done upfront.

**Story Points:** 2

---

### 7️⃣ **Implement E2E Test**

**Description:**  
Develop automated E2E test based on Gherkin: creates a draft (API), publishes it, verifies appearance on careers page, checks audit log.

**Acceptance:**  
- Test runs successfully with real or mocked data.

**Dependencies:**  
- All other tasks complete.

**Story Points:** 3

---

## ✅ **Summary Table**

| Ticket | Description | Story Points |
|--------|---------------------------|--------------|
| 1 | Formalize API Agreement | 3 |
| 2 | API Endpoint: Publish Job Opening | 5 |
| 3 | Frontend: Publish Button | 3 |
| 4 | Server-Side Careers Page Update | 5 |
| 5 | Audit Logging | 2 |
| 6 | Gherkin E2E Spec | 2 |
| 7 | Implement E2E Test | 3 |
| **Total** |  | **23 SP** |

---

## 📌 **Key Planning Notes**

- **Parallelization:** Create & Publish share the same API — API Agreement ensures safe parallel dev.
- **Mocking:** Frontend calls mocked Publish API until real endpoint is ready.
- **Testing:** Gherkin spec task is independent; E2E test task runs last.

---

