---
name: prd-task-list-align
description: Align PRD task lists with their PRDs - reviews task lists for completeness, logical ordering, and PRD alignment before updating them. Use when user says "align xxx-prd.md with xxx-prd-task-list.md" or similar phrases about reviewing and aligning task lists with PRDs.
license: MIT
compatibility: opencode
metadata:
  workflow: prd-review-and-alignment
  audience: product-managers-developers
---

# PRD Task List Alignment

## What I Do

I review task lists against their corresponding PRDs to ensure:
- **Completeness**: All PRD requirements have corresponding tasks
- **Alignment**: Task descriptions match PRD specifications
- **Logical Ordering**: Tasks are ordered feasibly and correctly
- **Dependencies**: Task dependencies are properly sequenced

## When to Use Me

Use this skill when user:
- Says "align xxx-prd.md with xxx-prd-task-list.md"
- Mentions "review task list" or "check task list alignment"
- Provides both a PRD file and a task list file
- Asks to verify if task list covers all PRD requirements

Trigger phrases:
- "Align [PRD-file] with [task-list-file]"
- "Review task list alignment with PRD"
- "Check if task list matches PRD"
- "Validate task list against PRD"

## Workflow Steps

When user provides a PRD file and a task list file for alignment:

### 1. Read PRD File
- Use the `read` tool to read the PRD file (e.g., `xxx-prd.md`)
- Extract key sections:
  - Problem statement and solution
  - Architecture and system components
  - File structures and schemas
  - Workflow logic and flows
  - Implementation phases
  - Goals and requirements

### 2. Read Task List File
- Use the `read` tool to read the task list file (e.g., `xxx-prd-task-list.md`)
- Extract all tasks:
  - Task IDs and descriptions
  - Steps and acceptance criteria
  - Dependencies between tasks
  - Current ordering

### 3. Perform Alignment Review

#### Check for Completeness
- Compare PRD requirements with task list items
- Identify missing requirements:
  - Features mentioned in PRD but not in task list
  - Components defined in PRD but no tasks to implement
  - Workflows described but no corresponding tasks
  - Files/templates specified but no tasks to create

#### Check for Alignment Issues
- Compare task descriptions with PRD specifications:
  - Task steps match PRD's implementation approach
  - Acceptance criteria reflect PRD's requirements
  - File paths match PRD's file structure
  - Agent/component names match PRD's architecture

#### Check for Logical Ordering Issues
- Analyze task dependencies:
  - Tasks creating files before tasks using them
  - Core structure tasks before feature tasks
  - Configuration tasks before implementation tasks
  - Testing tasks after implementation tasks
- Identify ordering problems:
  - Tasks referencing undefined variables/functions
  - Tasks requiring outputs from later tasks
  - Circular dependencies

#### Check for Feasibility Issues
- Verify each task is actionable:
  - Clear steps and acceptance criteria
  - All required information available
  - No ambiguous or vague requirements
  - Realistic scope for a single task

### 4. Generate Review Summary

Organize findings into clear categories:

**Critical Issues** (must fix):
- Tasks that contradict PRD
- Missing critical features
- Impossible ordering/dependencies

**Alignment Issues** (should fix):
- Tasks that partially match PRD but need updates
- Inconsistent terminology or file paths
- Missing implementation details

**Ordering Issues** (should fix):
- Tasks in wrong sequence
- Missing prerequisite tasks
- Tasks that could be reordered for better flow

**Minor Issues** (nice to fix):
- Typos or formatting issues
- Inconsistent numbering
- Missing version info

### 5. Present Review to User

Format the review summary:

```markdown
# PRD Task List Alignment Review

**PRD**: [filename]
**Task List**: [filename]
**Review Date**: [timestamp]

## Critical Issues

[List issues that must be fixed]

## Alignment Issues

[List issues that should be fixed]

## Ordering Issues

[List ordering problems]

## Minor Issues

[List minor issues]

## Recommendations

[High-level suggestions for improvement]
```

### 6. Discuss with User

- Present the review summary clearly
- Ask for user feedback on each issue
- Allow user to:
  - Accept all recommendations
  - Reject specific recommendations
  - Modify recommendations
  - Add additional concerns

### 7. Update Task List (After Approval)

Only proceed if user explicitly approves the changes:

#### For Each Approved Change:
1. **Reorder Tasks**:
   - Edit task list file using `edit` tool
   - Adjust task numbering (1.1, 1.2, etc.) to maintain sequence
   - Update references between tasks

2. **Add Missing Tasks**:
   - Create new task entries following existing format
   - Include task ID, description, steps, acceptance criteria
   - Insert at appropriate position in sequence
   - Renumber subsequent tasks

3. **Modify Existing Tasks**:
   - Use `edit` tool with `oldString` and `newString`
   - Update task descriptions to match PRD
   - Correct file paths, component names, etc.
   - Update acceptance criteria

4. **Delete Redundant/Incorrect Tasks**:
   - Remove tasks that don't align with PRD
   - Renumber remaining tasks to maintain sequence

#### Update Version Information:
- Add or update version section at end of task list:
  ```markdown
  ---
  **Task List Version:** [new-version]
  **Created:** [original-date]
  **Updated:** [current-date]
  **Based on:** [PRD version]

  **Changes in v[new-version]:**
  - Added Task X.Y: [description]
  - Fixed Task A.B: [change description]
  - Reordered: [changes]
  - Updated to v[new-version]: [other changes]
  ```

## Important Notes

- **Read-only by default**: Initially only read files and provide review
- **Explicit approval required**: Never edit task list without user confirmation
- **Maintain formatting**: Preserve markdown structure, numbering, and code blocks
- **Document changes**: Always update version history in task list
- **Check for conflicts**: If user has uncommitted changes to task list, mention this

## Common Review Patterns

### Missing Task Scenarios
Look for:
- PRD describes components but no tasks to create them
- PRD specifies hooks/events but no tasks to implement them
- PRD defines workflows but no tasks for execution
- PRD lists configuration files but no tasks to set them up

### Ordering Scenarios
Common ordering issues:
- Tests before implementation
- Configuration after usage
- Plugin/agent tasks after implementation tasks that need them
- Documentation tasks scattered throughout (group them)

### Alignment Scenarios
Check for:
- File paths not matching PRD specifications
- Component names inconsistent with PRD terminology
- Hook/event names not matching PRD architecture
- Agent/tool names not matching PRD requirements

## Example Workflow

**User**: "Align official-docs/plugins/opsx-workflow/PRD.md with official-docs/plugins/opsx-workflow/prd-task-list.md"

**My Process**:
1. Read PRD.md to understand plugin architecture and requirements
2. Read prd-task-list.md to see current tasks
3. Review and identify:
   - Missing tasks: Command file creation (PRD line 87-102, no corresponding task)
   - Wrong hook name: Task 4.1 uses `session.interrupted` but PRD says `session.status` (line 585)
   - Missing state persistence: PRD defines `savePluginState()` but no task to implement it
4. Present review summary with categorized issues
5. Discuss with user, get approval
6. Update task list with approved changes
7. Confirm updates and provide summary of what changed

## User Confirmation Prompts

Before making any changes, ask:

- "I found [X] issues. Shall I proceed to update the task list?"
- "These changes will: [summary]. Proceed?"
- "Any issues you'd like me to skip or modify?"

Only use `edit` tool after receiving explicit user approval.
