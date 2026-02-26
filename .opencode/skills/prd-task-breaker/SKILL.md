---
name: prd-task-breaker
description: Break down PRD documents into actionable task lists with clarifying questions
license: MIT
compatibility: opencode
metadata:
  workflow: task-planning
  audience: maintainers
---

# PRD Task Breaker

Break down large Product Requirements Documents (PRDs) into smaller, implementable tasks.

## What I Do

I read through the PRD document you specify and create a detailed task list broken down into small, manageable tasks. Each task includes:
- Clear goal description
- Step-by-step instructions
- Acceptance criteria checklist

## When to Use Me

Use me when you have a large PRD and want to:
- Split it into sequential implementation tasks
- Identify gaps or ambiguities in the PRD
- Create a trackable task list for development
- Ask clarifying questions before creating tasks

## Workflow

### Step 1: Read and Analyze PRD
- Read the PRD file completely
- Identify the overall scope and architecture
- Note any complex sections that need breakdown
- Check for dependencies between sections

### Step 2: Ask Clarifying Questions (if needed)

If the PRD has:
- Unclear requirements
- Ambiguous technical specifications
- Missing implementation details
- Contradictions between sections

I will ask you targeted questions using the AskUserQuestion tool to clarify:
- Specific functionality expectations
- Technical approach preferences
- Integration points with existing systems
- Edge cases and error handling requirements

### Step 3: Create Task Breakdown

Organize tasks by:
- **Phase** - Logical grouping of related tasks
- **Priority** - HIGH/MEDIUM/LOW based on dependencies
- **Prerequisites** - Tasks that must be completed first
- **Sequence** - Dependencies between tasks

Each task includes:
- **Clear goal** - What the task accomplishes
- **Steps** - Detailed instructions for implementation
- **Acceptance criteria** - Checklist to verify completion
- **Estimated complexity** - LOW/MEDIUM/HIGH for planning

### Step 4: Create Task List File

Generate `xxx-task-list.md` where `xxx` is the PRD filename without extension:
- Same directory as the PRD file
- Markdown format with consistent structure
- Sequential task numbering
- Clear section headers

## Output Format

The task list follows this structure:

```markdown
# [PRD Name] - Task List

Breakdown of [PRD filename] into smaller, implementable tasks. Work through tasks sequentially.

## Task [X.Y]: [Task Name]

**Goal:** [What the task accomplishes]

**Steps:**
1. [First step]
2. [Second step]
...

**Acceptance Criteria:**
- [ ] Criteria 1
- [ ] Criteria 2
...

---

## Notes and Assumptions

[Any important notes or assumptions about specific tasks]
```

## Handling PRD Types

### Technical PRDs
- Focus on implementation tasks in order
- Break down complex features into smaller chunks
- Identify integration points
- Consider testing and documentation

### Process PRDs
- Focus on workflow and automation tasks
- Identify sequential steps
- Consider error handling and edge cases
- Include configuration tasks

### Plugin/Extension PRDs
- Focus on plugin architecture
- Break down hooks, handlers, and integration points
- Include file structure tasks
- Consider state management and persistence

## Questions I May Ask

When analyzing the PRD, I might ask about:

- **Architecture choices**: "Should the plugin use in-memory state or file-based persistence?"
- **Feature scope**: "Is feature X required for MVP, or can it be deferred?"
- **Error handling**: "How should the system handle failure in this step - retry, fallback, or abort?"
- **Integration points**: "Should this integrate with existing system Y, or is it standalone?"
- **Performance**: "Are there specific performance requirements or constraints?"
- **Testing**: "What level of testing is expected - unit, integration, E2E?"

## Examples

### Example 1: Plugin PRD Breakdown

**PRD:** `opsx-workflow/PRD.md`

**Tasks created:**
- Task 1.1: Create plugin file structure
- Task 1.2: Implement file I/O functions
- Task 1.3: Implement proposal finding logic
- Task 2.1: Implement stage management
- Task 2.2: Implement stage progression
...

**Clarifying questions asked (if any):**
- "Should plugin state persist across stages, or use temp file storage?"
- "What happens if an agent name specified in workflow.yml doesn't exist?"

### Example 2: Feature PRD Breakdown

**PRD:** `features/payment-system.md`

**Tasks created:**
- Phase 1: Database schema design
  - Task 1.1: Create payment_transactions table
  - Task 1.2: Create payment_methods table
- Phase 2: API design
  - Task 2.1: Define REST endpoints
  - Task 2.2: Define request/response schemas
...

## Best Practices

- **Read PRD completely** before breaking down to understand context
- **Ask questions early** when something is unclear to avoid wasted work
- **Maintain consistency** in task naming and structure
- **Use clear, actionable language** for task descriptions
- **Include acceptance criteria** to make completion unambiguous
- **Note dependencies** between tasks explicitly
- **Estimate complexity** to help with sprint planning
- **Group related tasks** by phase or feature area
- **Keep tasks granular** - should be completable in 1-2 hours ideally

## Completion

After creating the task list, I will:
1. Confirm the file location: `Created: [directory]/xxx-task-list.md`
2. Provide a summary:
   - Total number of tasks created
   - Number of phases identified
   - Any questions that need answering
3. Wait for your confirmation or next instruction
