# Prompts

## Prompt 1. Cursor (claude-4-opus)

````markdown
## Role

You are an experienced Product Manager and Business Analyst.

## Goal

@LTI-JAGM.md is a prd for an ATS. I would like you to help me generate the user stories for the backlog.

## Output

Each user story should follow this template:

```markdown
# User Story Title

As a **[user role]**, I want **[action the user wants to perform]**, so that **[benefit the user expects to obtain]**.

## Acceptance Criteria:

- [Specific functionality detail]
- [Specific functionality detail]
- [Specific functionality detail]

## Additional Notes:

[Any additional considerations]

## Related User Stories:

[Relationships with other user stories]
```

## Details

- Generate a markdown document with the user stories.
- Add an index at the begining of it
````

## Prompt 2. Cursor(claude-4-opus)

```markdown
## Role

You are an experienced Product Manager and Business Analyst.

## Goal

@LTI-JAGM.md is a prd for an ATS. From this prd I have generated the user stories @UserStories-JAGM.md .
I would like you to help me priorotize this user stories. To do so consider the following criteria:

1. User impact and business value
2. Urgency, based on market trends
3. Complexity and estimated effort
4. Risks and dependencies between tasks.

Assign to each user story values from 1 to 3, being 1 the minimum and 3 the maximum, for each the criteria. After that consider the order of the criteria to stablish wich user stories should be prioritize.

## Details

- Add a new section `Backlog` in @UserStories-JAGM.md with the sorted user stories.
- Include the formula for calculating the final score
- For each user story add a link to its description
- For each user story add the weight you gave in each criteria and the final score.
```

**In my opinion the prompt worked well in the first attempt. It made a mistake sorting the user stories based on the final score that I have to fix manually. I also forget to explicitly mention to add the backlog in the table of contents, so I had to do that manually too.**

## Same chat

### Prompt 3. Cursor(claude-4-opus)

```markdown
## Role

You are an experienced Product Manager and Business Analyst.

## Goal

@LTI-JAGM.md is a prd for an ATS. In this file @UserStories-JAGM.md we have listed the user stories and a backlog.
I would like to generate the user tasks for the first user story in the backlog.

## Output

Each user task must have:

### 1. Clear and Concise Title

A brief summary that reflects the essence of the task. It should be descriptive enough for any team member to quickly understand what the ticket is about.

### 2. Detailed Description

**Purpose:** Explanation of why the task is necessary and what problem it solves.

**Specific Details:** Additional information about specific requirements, constraints, or conditions necessary for task completion.

### 3. Acceptance Criteria

**Clear Expectations:** Detailed list of conditions that must be met for the work on the ticket to be considered complete.

**Validation Tests:** Specific steps or tests that must be performed to verify that the task has been completed correctly.

### 4. Priority

**Urgency Level:** A classification of the importance and urgency of the task, which helps determine the order in which tasks should be addressed within the backlog.

### 5. Assignment

**Responsible Party:** Who or which team will be responsible for completing the task. This ensures that all stakeholders understand who is in charge of each part of the project.

### 6. Labels or Tags

**Categorization:** Tags that help classify the ticket by type (bug, enhancement, task, etc.), by product features (UI, backend, etc.), or by sprint/version.

### 7. Comments and Notes

**Collaboration:** Space for team members to add relevant information, ask questions, or provide updates on task progress.

### 8. Links or References

**Related Documentation:** Links to documents, designs, specifications, or related tickets that provide additional context or information necessary for task execution.

### 9. Change History

**Modification Tracking:** A record of all changes made to the ticket, including status updates, reassignments, and modifications to details or priorities.

## Details

- Add a new section `User tasks for {user-story}` in @UserStories-JAGM.md with the user tasks.
- Include the new section in the table of contents
```

**The prompt added a section with notes at the end. These notes made references to some of the user tasks, so I move each of them to the user task mention under the section `Notes`**

### Prompt 4. Cursor(claude-4-opus)

```markdown
## Goal

Estimate the effort of the user tasks you just added to @UserStories-JAGM.md . Use the Fibonacci methodology and story points.

## Details

- Add a new section `Story Points` at the end of each user task
```
