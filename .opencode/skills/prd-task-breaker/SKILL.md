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

**🔴 Important: Continuous Testing Pattern**

Every task breakdown **must** include continuous testing acceptance criteria. This means:
- Each task requires running the application and verifying it works
- Developers test after completing each task, not at the end
- Every acceptance criteria includes: run command + specific verification + expected behavior + error checks

See "Continuous Testing Pattern" section below for detailed guidelines.

## What I Do

I read through the PRD document you specify and create a detailed task list broken down into small, manageable tasks. Each task includes:
- Clear goal description
- Step-by-step instructions
- Acceptance criteria checklist with **continuous testing requirements**

**Critical:** Every task must include end-to-end testing acceptance criteria that requires running the application and verifying it works before moving to the next task. This ensures "continuous testing during development" rather than waiting until all code is complete.

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
- **Acceptance criteria** - Checklist to verify completion with **mandatory testing steps**:
  - Run command (e.g., `flutter run -d chrome`, `npm start`, `python app.py`)
  - Specific verifications (e.g., "Hero section displays correctly")
  - Expected behaviors (e.g., "Image loads without errors")
  - Error checks (e.g., "No console errors")
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
- [ ] Basic criteria (files created, code compiles, etc.)
- [ ] **Run `command` - app launches/starts without errors**
- [ ] **Specific feature works (e.g., "Hero section displays correctly")**
- [ ] **Expected behaviors verified (e.g., "Button is clickable and responds")**
- [ ] **No console errors or warnings**

---

## Notes and Assumptions

[Any important notes or assumptions about specific tasks]
```

**Continuous Testing Pattern:**
Every task's acceptance criteria must include:
1. A **run command** that executes the current state of the application
2. **Specific verifications** that the new feature/component displays correctly
3. **Expected behaviors** that demonstrate the feature works as intended
4. **Error checks** that ensure no console errors or warnings

This pattern ensures developers verify each task before proceeding to the next.

## Handling PRD Types

### Technical PRDs
- Focus on implementation tasks in order
- Break down complex features into smaller chunks
- Identify integration points
- Include continuous testing for every implementation task
- Consider testing and documentation

### Process PRDs
- Focus on workflow and automation tasks
- Identify sequential steps
- Consider error handling and edge cases
- Include configuration tasks
- Add testing where possible (e.g., verify workflow runs, check logs)

### Plugin/Extension PRDs
- Focus on plugin architecture
- Break down hooks, handlers, and integration points
- Include file structure tasks
- Consider state management and persistence

## Continuous Testing Pattern

**What is Continuous Testing?**

Continuous testing means verifying that each task works correctly before moving to the next task, rather than waiting until all code is complete. This catches issues early and ensures a working state at every step.

**Why It Matters:**

- **Catches errors early** - Don't wait until the end to find broken code
- **Ensures incremental progress** - Each task produces a verifiable result
- **Reduces debugging time** - Problems are easier to fix when recent
- **Builds confidence** - Developers know their work is working

**How to Apply:**

Every task's acceptance criteria MUST include:

1. **Run Command:** The exact command to execute the application
   - Examples: `flutter run -d chrome`, `npm start`, `python app.py`, `go run main.go`

2. **Specific Verifications:** What to check visually or functionally
   - Examples: "Hero section displays correctly", "Button responds to clicks", "Table contains expected data"

3. **Expected Behaviors:** How the feature should behave
   - Examples: "Image loads without errors", "Link navigates to correct URL", "Form submits successfully"

4. **Error Checks:** Verification that nothing is broken
   - Examples: "No console errors", "No warnings in terminal", "API returns 200 status"

**Example Task with Continuous Testing:**

```markdown
## Task 2.1: Create Hero Section

**Goal:** Display header with profile, title, and bio.

**Steps:**
1. Create `lib/pages/hero_section.dart`
2. Add Image.asset for profile photo
3. Add title text
4. Add bio text

**Acceptance Criteria:**
- [ ] Hero section widget created
- [ ] Profile image displays
- [ ] Title and bio shown
- [ ] **Run `flutter run -d chrome` - Hero section displays correctly**
- [ ] **Profile image loads without errors**
- [ ] **Text is readable and properly styled**
- [ ] **No console errors**
```

**When NOT to Use Continuous Testing:**

- Pure configuration changes (e.g., updating README)
- Documentation-only tasks (unless they're code documentation)
- Infrastructure setup that can't be tested locally (e.g., Docker deployment to remote server) - in these cases, mark as "(For Later)" or note that testing will be done during deployment

## Questions I May Ask

When analyzing the PRD, I might ask about:

- **Architecture choices**: "Should the plugin use in-memory state or file-based persistence?"
- **Feature scope**: "Is feature X required for MVP, or can it be deferred?"
- **Error handling**: "How should the system handle failure in this step - retry, fallback, or abort?"
- **Integration points**: "Should this integrate with existing system Y, or is it standalone?"
- **Performance**: "Are there specific performance requirements or constraints?"
- **Testing**: "What run command should be used for testing? (e.g., `flutter run -d chrome`, `npm start`)"
- **Testing approach**: "Should tasks use continuous testing pattern (test after each task) or deferred testing?"

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

**Example acceptance criteria with continuous testing:**
```markdown
**Acceptance Criteria:**
- [ ] payment_transactions table created with all required columns
- [ ] **Run `npm run migrate` - migration executes successfully**
- [ ] **Run `psql -d payments_db -c "\d payment_transactions"` - table schema is correct**
- [ ] **No migration errors**
```

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
- **Always include continuous testing** - every task must have run-and-verify acceptance criteria
- **Test after each task** - never defer testing until the end
- **Be specific with testing commands** - provide exact commands (e.g., `flutter run -d chrome`)
- **Include error checks** - every task should verify no console errors or warnings

## Completion

After creating the task list, I will:
1. Confirm the file location: `Created: [directory]/xxx-task-list.md`
2. Provide a summary:
   - Total number of tasks created
   - Number of phases identified
   - Any questions that need answering
3. Wait for your confirmation or next instruction
