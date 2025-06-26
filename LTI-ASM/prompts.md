## 🔢 Prompt Iteration Log – Backlog & User Stories (Week 05)

Below is a numbered list of the prompts that were used (or refined) to produce the final deliverable. The process reflects progressive refinement, structured prompting, and analysis.

---

### 1. 🟠 Initial Prompt (Basic Exploration)
```
From the attached PRD, list user stories for an ATS.
```
**Outcome:** Generated a flat list of ~12 user stories, but without any structure, no prioritization, no effort estimation.  
**Conclusion:** Too generic. Did not follow best practices for user stories. Only useful as a first brainstorm.

---

### 2. 🟡 Structured Prompt with Spanish Template
```
Draft 5 user stories in Spanish using ‘Como/quiero/para’, include MoSCoW priority and t-shirt effort.
```
**Outcome:** Valid user stories with roles and actions, but no sprint structure, epics, dependencies or consistent IDs.  
**Conclusion:** Better, but lacked context from the overall PRD and failed to generate a structured backlog format.

---

### 3. ✅ Final Prompt (Highly Structured and Context-Aware)
```
Use the document LTI-ASM.md to generate 5 user stories using this full template:

Title (ID): LTI-###
As a [role], I want to [action], so that [benefit].

Acceptance Criteria:
- Given ...
- When ...
- Then ...

Also include:
- MoSCoW priority
- T-shirt sizing (effort)
- Logical dependencies
- Suggest sprint names using the format “Sprint N – Theme”
- Return everything in a Markdown table with columns: ID, Epic, Story, Sprint, Priority, Effort, Dependencies, Status=To Do.
```
**Outcome:** Produced exactly the structure needed for submission:
- 5 refined user stories
- Prioritized backlog in Markdown table
- Clear effort sizing and logical grouping into sprints
- Consistent formatting and IDs

**Conclusion:** This was the most effective prompt because it:
- Combined **format constraints** (Markdown table, story template)
- Included **content logic** (MoSCoW, dependencies, sprints)
- Anchored all generations on the existing PRD documentation

---

### 4. 🧩 Ticket Breakdown Prompt
```
Take User Story LTI-03 (Schedule Interview & Hire Decision) and break it down into 4–6 technical work tickets, using t-shirt sizing and a Jira-style Markdown format.
```
**Outcome:** Created 5 clearly scoped implementation tickets for backend, frontend, notifications, and QA, each estimated with t-shirt sizes.  
**Conclusion:** Useful for simulating sprint planning sessions, aligned with real-world delivery practices.

---

### 5. 🔄 Prompt to Generate Pull Request Summary
```
Write a professional English summary for a GitHub Pull Request, describing the Week 05 deliverable (user stories, backlog, tickets, prompts, estimation). Use a detailed format similar to enterprise-level documentation.
```
**Outcome:** Generated a polished PR message covering all deliverable sections, ready to paste into GitHub.  
**Conclusion:** Valuable for increasing review quality, alignment with peer submissions, and stakeholder communication.