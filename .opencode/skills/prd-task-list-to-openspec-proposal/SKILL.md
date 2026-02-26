---
name: prd-task-list-to-openspec-proposal
description: Create OpenSpec change proposals for all tasks in a PRD task list automatically
license: MIT
compatibility: opencode
metadata:
  workflow: openspec-proposal-automation
  audience: opencode-users
---

# PRD Task List to OpenSpec Proposal Converter

Converts tasks from a PRD task list document into complete OpenSpec change proposals with minimal manual effort.

## What I Do

I help you convert PRD task lists into OpenSpec change proposals by:
- Parsing the PRD task list document (`*-task-list.md`)
- Extracting individual task descriptions with their line number ranges
- Creating one OpenSpec change proposal per task using `openspec-propose` skill
- Providing full context from both the PRD and task list to each subagent
- Executing subagents sequentially to prevent tool call conflicts and rate limits
- Tracking completion and providing a summary when all tasks are done

## When to Use Me

Use this skill when you want to:
- "Create openspec change proposals for tasks in xxx-task-list.md"
- "Generate OpenSpec proposals from this task list"
- "Convert all tasks in my task list to OpenSpec changes"

I will automatically:
1. Read and parse the specified task list file
2. Extract all tasks with their descriptions and acceptance criteria
3. Read the corresponding PRD file for additional context
4. Create subagent for each task sequentially
5. Wait for each subagent to complete before starting the next
6. Provide a summary of all created changes

## Workflow Steps

### Step 1: Parse Task List
- Locate the task list file (pattern: `*-task-list.md`)
- Parse task sections using regex to identify:
  - Task number and title (e.g., "## Task 1.1: Create Plugin File Structure")
  - Goal/description
  - Steps (if present)
  - Acceptance criteria (checkbox items)
- Extract line number ranges for each task from the original file

### Step 2: Load PRD Context
- Find the corresponding PRD file (typically `PRD.md` in same directory)
- Read PRD to gather:
  - Overall project context and constraints
  - Architecture decisions
  - Relevant sections that pertain to the task
- Extract relevant sections based on task content

### Step 3: Create Subagent for Each Task
- For each task in the parsed list:
  - Create a Task tool call with:
    - Description: "Create OpenSpec change for [Task Title]"
    - Prompt containing:
      - Task description and steps
      - Acceptance criteria
      - Relevant context from PRD (architecture, decisions, constraints)
      - Instruction to use `openspec-propose` skill
      - Change name pattern: `[task-number]-[task-title-kebab-case]`
      - Note that change directory already exists, just populate artifacts
  - Use `task_id` parameter to resume if needed for interrupted tasks
- Wait for subagent completion before creating the next one

### Step 4: Track Progress
- Monitor subagent results
- Track which tasks succeeded/failed
- Continue with next task only after current task completes
- If a task fails, ask user whether to:
  - Retry the failed task
  - Skip and continue with next task
  - Stop entirely

### Step 5: Provide Summary
- After all tasks complete, show summary:
  - Total tasks processed
  - Successfully created changes
  - Any skipped or failed tasks
  - Location of all change directories

## Task List Parsing

The skill expects task lists in this format (based on standard PRD task lists):

```markdown
## Task X.Y: Task Title

**Goal:** Brief description

**Steps:**
1. First step
2. Second step

**Acceptance Criteria:**
- [ ] Checkbox item 1
- [ ] Checkbox item 2
```

### Extracted Information Per Task

For each task, I extract:
- **Task ID**: X.Y (e.g., "1.1", "2.1")
- **Title**: Task Title
- **Goal**: The brief description of what to accomplish
- **Steps**: Detailed implementation steps (if present)
- **Acceptance Criteria**: List of checkbox items that define completion
- **Line Numbers**: Start and end lines in the task list file

### Change Naming Convention

OpenSpec change names follow this pattern:
- Format: `task-[number]-[title-kebab-case]`
- Example: `task-1-1-create-plugin-file-structure`
- Example: `task-2-3-implement-stage-progression`
- Limit: Lowercase, alphanumeric, single hyphen separators

## Context Provisioning

### From Task List
- Full task description including steps and acceptance criteria
- Task position in the overall sequence
- Dependencies mentioned in task description

### From PRD
- Relevant architecture sections for the task
- Key design decisions
- Constraints and assumptions
- File paths and structure requirements
- Interface definitions (if creating types)

### Combined Context

Each subagent receives:
- Complete task specification from task list
- Relevant PRD sections for context
- Instruction to use `openspec-propose` skill
- Note that change directory exists (created in initial pass)

## Sequential Execution

### Why Sequential?

1. **Prevent Tool Call Conflicts**: Running multiple subagents simultaneously can cause:
   - Race conditions in tool execution
   - Conflicting file operations
   - Rate limiting by LLM provider
   - Context fragmentation

2. **Cleaner Progress Tracking**: One subagent at a time means:
   - Clear feedback on each task completion
   - Easier to identify which task failed
   - Better user control over the workflow

3. **Resource Management**: Sequential execution:
   - Prevents exceeding LLM API rate limits
   - Reduces concurrent context consumption
   - Allows proper cleanup between tasks

### Execution Pattern

For each task:
```
[Start Subagent]
  ↓
[Wait for Completion]
  ↓
[Log Success/Failure]
  ↓
[Ask: Continue Next, Retry, or Stop?]
  ↓
[If Continue: Start Next Subagent]
```

## Notes and Edge Cases

### Task List Variations
- **Different formats**: Some task lists may use `### Task X.Y` or `## Task X.Y` - I handle both
- **Missing acceptance criteria**: If no checkbox items, I still create the change
- **Complex tasks**: Tasks with many sub-steps may need larger context windows

### PRD Reference
- **Multiple PRDs**: If task list references multiple PRDs, I read all relevant ones
- **No PRD found**: If task list doesn't reference a PRD, I proceed with task list only
- **PRD location**: I search for `PRD.md` in the same directory as the task list

### Error Handling
- **Failed subagent**: Log the error and ask user whether to continue
- **Missing task file**: Prompt user to provide the correct path
- **Parse errors**: Inform user and ask if they want to continue with available tasks
- **Partial completion**: If workflow interrupted, report completed tasks so far

### Resume Capability

The skill uses `task_id` parameter for:
- Resuming interrupted task sequences
- Debugging failed task conversions
- Not blocking the user from continuing

## Usage Examples

### Example 1: Full Task List Conversion
```
User: "Create openspec change proposals for tasks in prd-task-list.md"

Skill:
  1. Parse prd-task-list.md (23 tasks found)
  2. Read PRD.md for context
  3. Create subagent for Task 1.1...
     [Completes task 1.1 artifacts]
  4. Create subagent for Task 1.2...
     [Completes task 1.2 artifacts]
  ... [continues for all 23 tasks]
Summary: 23/23 changes created successfully
```

### Example 2: Partial Task List
```
User: "Generate OpenSpec proposals from official-docs/plugins/opsx-workflow/prd-task-list.md"

Skill:
  1. Parse task list (23 tasks)
  2. Load PRD from official-docs/plugins/opsx-workflow/PRD.md
  3. Process each task sequentially...
     [Tasks 1.1-1.6: Core structure - all complete]
     [Tasks 2.1-2.6: Workflow orchestration - all complete]
     ... [continues]
Summary: All 23 tasks processed successfully
```

### Example 3: Error Recovery
```
User: "Convert tasks in my-tasks.md"

Skill:
  1. Parse task list (5 tasks found)
  2. Process Task 1... [Complete]
  3. Process Task 2... [FAILED: subagent error]
     → "Task 2.1 failed to create changes. Continue with next task? (y/n)"
     → User: "y"
  4. Process Task 3... [Complete]
  5. Process Task 4... [Complete]
  6. Process Task 5... [Complete]
Summary: 5 tasks processed, 4 complete, 1 failed (Task 2.1)
```

## Important Notes

- This skill creates a LOT of changes - ensure you have sufficient time
- Each subagent runs the `openspec-propose` skill which creates 4 artifacts per task
- The skill itself does NOT create any files directly - it orchestrates subagents
- All actual artifacts (proposal.md, design.md, specs/, tasks.md) are created by subagents
- This is an orchestrator skill - it coordinates other skills/subagents
