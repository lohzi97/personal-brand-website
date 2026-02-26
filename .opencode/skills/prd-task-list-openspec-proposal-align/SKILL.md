---
name: prd-task-list-openspec-proposal-align
description: Use this skill when user wants to review OpenSpec proposals for alignment with their PRD and task list. The skill reviews each proposal sequentially using subagents to ensure proposals contain sufficient information for implementation.
license: MIT
compatibility: opencode
metadata:
  workflow: openspec-proposal-review
  audience: opencode-users
  type: review-and-align
---

# PRD Task List to OpenSpec Proposal Alignment

## What I Do

I help you systematically review and align OpenSpec change proposals with their corresponding PRD and task list requirements. I process tasks sequentially using subagents to ensure each proposal contains sufficient implementation detail.

## When to Use Me

Use this skill when the user says:

- "Align OpenSpec proposals with the PRD"
- "Review proposals based on prd-task-list.md"
- "Check alignment between proposals and PRD"
- "Ensure proposals are ready for implementation"
- "Review each proposal for completeness"

**Trigger phrases:**
- "Align OpenSpec proposal based on prd-task-list.md to the prd"
- "Review proposals against the PRD"
- "Check if proposals have enough information for implementation"
- "Go through each task and review the proposal"

## Workflow Steps

### 1. Read Context Documents

Read the following files to understand requirements:
- **PRD file**: `official-docs/plugins/opsx-workflow/PRD.md` (or user-specified path)
- **Task list**: `official-docs/plugins/opsx-workflow/prd-task-list.md` (or user-specified path)
- **Proposals directory**: `openspec/changes/` (contains task-specific proposal directories)

### 2. Parse Task List

Parse the task list to extract all tasks:
- Each task starts with `## Task X.Y: [Task Name]`
- Tasks are numbered sequentially (e.g., 1.1, 1.2, 2.1, etc.)
- Each task has:
  - A description of what needs to be done
  - Steps section with detailed implementation steps
  - Acceptance criteria section (usually a checklist)

### 3. Process Tasks Sequentially

For each task in the task list:

#### a. Spin Up a Subagent

Use the `Task` tool with `subagent_type="general"` to create a subagent for reviewing the proposal:
- Provide the task context (task number, description, steps, acceptance criteria)
- Provide relevant PRD sections (if specified in task)
- Provide the path to the corresponding proposal directory

#### b. Subagent Review Process

The subagent should:

1. **Read the proposal files:**
   - Read `openspec/changes/task-X-Y-[slug]/proposal.md`
   - Read other artifacts if present: `design.md`, `tasks.md`, `specs/*/spec.md`

2. **Review against requirements:**
   - Check if proposal captures all steps from task list
   - Verify alignment with relevant PRD sections
   - Ensure acceptance criteria from task list are addressed
   - Check for sufficient implementation detail

3. **Identify gaps or misalignments:**
   - Missing implementation details
   - Incomplete function signatures
   - Missing error handling
   - Unclear specifications
   - Inconsistencies between proposal, PRD, and task list

4. **Update the proposal if needed:**
   - If issues are found, update `proposal.md` with:
     - Added implementation details
     - Clarified specifications
     - Fixed inconsistencies
     - Added missing sections
   - Keep updates minimal and focused

5. **Report back:**
   - Summary of review (issues found or none)
   - Any changes made to the proposal
   - Confirmation that proposal is ready for implementation

#### c. Wait for Completion

Wait for the subagent to complete its review before spinning up the next subagent.

#### d. Track Progress

Maintain a running summary:
- Total tasks to review
- Tasks completed
- Issues found and fixed

### 4. Final Report

After all tasks have been reviewed:

Provide a comprehensive summary:
- **Total proposals reviewed**: Number of tasks processed
- **Proposals updated**: Number that required changes
- **Proposals ready**: Number now ready for implementation
- **Common issues found**: Pattern of problems across proposals (if any)
- **Recommendations**: Suggestions for improving proposal quality

## Important Notes

### Sequential Processing is Critical

**ALWAYS** process tasks sequentially (not in parallel):
- Prevents race conditions when multiple subagents update files
- Avoids conflicts with file writes
- Prevents API rate limiting issues
- Makes it easier to track progress

### Subagent Prompt Template

When spinning up a subagent, use this template:

```
Review the OpenSpec change proposal for Task {task-number}: {task-name}.

The proposal is located in: openspec/changes/{task-slug}/

Context from the PRD:
- {relevant PRD sections or line references}

Context from the task list (prd-task-list.md lines {start_line}-{end_line}):
- {task description, steps, acceptance criteria}

Your task:
1. Read the proposal.md file in the task-{slug} directory
2. Review the proposal against the PRD and task list requirements
3. Check if the proposal contains sufficient information for implementation
4. Look for any gaps, missing details, or inconsistencies

If you find issues:
- Update the proposal.md to include missing details
- Ensure all requirements from PRD and task list are captured
- Make sure the proposal is clear and actionable for implementers

Report back with:
- Summary of your review (issues found or none)
- Any changes you made to the proposal
- Confirmation that the proposal is ready for implementation
```

### File Paths

- **Standard locations:**
  - PRD: `official-docs/plugins/{plugin-name}/PRD.md`
  - Task list: `official-docs/plugins/{plugin-name}/prd-task-list.md`
  - Proposals: `openspec/changes/task-X-Y-[slug]/proposal.md`

- **User can override:** If user specifies different paths, use those instead

### Acceptance Criteria

A proposal is considered "ready for implementation" when:
- ✅ All task list steps are captured
- ✅ All acceptance criteria from task list are addressed
- ✅ Implementation details are specific and actionable
- ✅ Aligns with relevant PRD sections
- ✅ Contains sufficient information for a developer to implement
- ✅ No critical gaps or ambiguities

### Common Issues to Check For

When reviewing proposals, look for:

1. **Missing implementation details:**
   - No function signatures
   - No specific algorithms or logic
   - Vague descriptions instead of concrete steps

2. **Incomplete specifications:**
   - Missing error handling
   - No edge case coverage
   - Unclear input/output formats

3. **Inconsistencies:**
   - Contradictions between proposal and PRD
   - Mismatch with task list requirements
   - Outdated information

4. **Insufficient context:**
   - No reference to PRD sections
   - Missing dependencies on other tasks
   - Unclear integration points

## Example User Requests

- "Align OpenSpec proposals based on prd-task-list.md to the prd"
- "Review each proposal in openspec/changes/ for completeness"
- "Check if all proposals are aligned with the PRD"
- "Go through the task list and review each proposal"
- "Ensure proposals have enough implementation detail"

## Workflow Example

**User says:** "Align OpenSpec proposals based on prd-task-list.md to the prd"

**Agent:**
1. Reads PRD.md and prd-task-list.md
2. Parses 23 tasks from task list
3. Spins up subagent for Task 1.1
4. Waits for subagent to complete review and update
5. Spins up subagent for Task 1.2
6. Continues sequentially through all 23 tasks
7. Provides final summary: "All 23 proposals reviewed. 15 updated with additional details. All proposals now ready for implementation."
