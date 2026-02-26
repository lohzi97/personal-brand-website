---
name: prd-review
description: Verify PRD feasibility and accuracy by cross-referencing with official documentation and user-provided sources. Ask clarifying questions for gaps/conflicts, then update PRD to be more detailed and accurate.
license: MIT
compatibility: opencode
metadata:
  workflow: prd-validation
  audience: product-managers-technical-writers
---

# PRD Reviewer

## What I Do

- Read through PRD files to understand requirements and design
- Cross-reference PRD claims with official OpenCode documentation
- Verify feasibility of technical approaches and architecture
- Use user-provided sources (docs, guides, files) for validation
- Automatically gather information via webfetch, brave-search, context7, etc. when sources not provided
- Identify issues categorized by severity (CRITICAL, HIGH, MEDIUM, LOW)
- Note positive findings when PRD correctly references official docs
- Ask clarifying questions to resolve uncertainties
- Update PRD with more detailed, accurate specifications based on user's decisions

## When to Use Me

Use this skill when you need to:
- Verify a PRD is technically feasible
- Cross-check PRD against official documentation
- Validate implementation approaches
- Identify missing requirements or architectural issues
- Ensure PRD aligns with available APIs, tools, and frameworks
- Get issues categorized by severity with specific recommendations

Trigger phrases:
- "verify this PRD"
- "check PRD against official docs"
- "is this PRD feasible"
- "validate PRD requirements"
- "review PRD for issues"
- Any mention of reviewing/verifying a PRD file

## Review Process

### 1. Read and Understand PRD
- Parse the PRD file completely
- Extract key requirements, architecture decisions, and assumptions
- Identify technical components, dependencies, and integration points
- Understand problem statement and proposed solution

### 2. Gather Reference Materials
- Check if user provided specific documentation sources (use @ references)
- If not provided, automatically fetch relevant official docs:
  - OpenCode official documentation (via webfetch)
  - Plugin documentation (if applicable)
  - SDK/API documentation
  - Agent configuration guides
  - Command registration documentation
  - Any relevant GitHub repositories or examples
- Use multiple sources to cross-verify claims

### 3. Feasibility Analysis

For each major requirement in PRD, verify:
- **API/Method availability**: Does the referenced method actually exist?
  - Check official docs for SDK methods, hooks, events
  - Verify parameters and return types match PRD
  - Note when methods are available vs assumed
- **Configuration validity**: Are the proposed configurations supported?
  - Check agent configuration options
  - Verify plugin hook definitions
  - Validate file structure requirements
  - Check command registration approaches
- **Technical approach**: Is the proposed implementation approach feasible?
  - Assess architectural patterns
  - Validate workflow logic
  - Check for known limitations or bugs
  - Verify event hook sequences
- **Dependencies**: Are all dependencies available and compatible?
  - Verify npm package versions and availability
  - Check OpenCode/plugin compatibility requirements

### 4. Identify Issues and Gaps

Categorize findings by severity:

**CRITICAL** - Will block implementation:
- Technical impossibilities or non-existent features
- Fundamental architectural flaws
- Missing essential components (hooks, methods, APIs)

**HIGH** - Major issues needing resolution:
- Unclear or missing implementation approaches
- Configuration that won't work
- Missing dependencies or compatibility issues

**MEDIUM** - Important improvements needed:
- Ambiguous specifications
- Incomplete error handling
- State management gaps

**LOW** - Nice-to-have improvements:
- Documentation clarity
- Minor inconsistencies
- Edge cases not covered

Also note:
- **POSITIVE FINDINGS**: Things correctly documented that should be acknowledged
- **Conflicts**: Contradictory requirements or design decisions
- **Missing information**: Critical details needed for implementation
- **Outdated assumptions**: PRD assumptions based on old documentation

### 5. Ask Clarifying Questions
For each issue/gap identified, ask user:
- Group by severity (CRITICAL → HIGH → MEDIUM → LOW)
- Explain the problem clearly with context from PRD (location, issue description)
- Reference specific section or line numbers in PRD
- Provide alternative approaches if available
- For critical/high issues, recommend specific fixes
- For medium/low issues, suggest improvements but note they're less critical
- Ask for user's decision on each item (fix, skip, defer, modify approach)
- Present all findings first, then request user's decisions before making changes

### 6. Update PRD

After gathering user's decisions:
- Organize changes by user's confirmation (e.g., "1. Non-existent session.interrupted - ok. Please use session.status instead of session.interrupted")
- Make targeted updates to PRD file using Edit tool
- Add missing details and specifications
- Correct infeasible or conflicting requirements
- Update code examples to match actual APIs
- Add references to official documentation where appropriate
- Maintain PRD structure and formatting
- Present summary of changes made after updates complete

## Review Checklist

### Technical Feasibility
- [ ] All referenced SDK methods exist in official docs
- [ ] All event hooks are valid (no `session.interrupted` etc.)
- [ ] All configuration options are supported
- [ ] File structures match OpenCode expectations
- [ ] Dependencies are available and version-compatible

### Architectural Soundness
- [ ] Workflow logic is sound and achievable
- [ ] State management approach is clearly defined
- [ ] Error handling is comprehensive with logging
- [ ] Edge cases are addressed (interruption, max iterations)
- [ ] Scalability/limitations are acknowledged

### Documentation Quality
- [ ] Requirements are clear and unambiguous
- [ ] Examples match actual API signatures
- [ ] Diagrams match actual implementation
- [ ] References to official docs are correct and up-to-date
- [ ] Missing information is called out as assumptions to verify

### Completeness
- [ ] All necessary sections are present
- [ ] Edge cases are considered in testing strategy
- [ ] Error scenarios are covered (interruption, failures, recovery)
- [ ] Testing strategy includes positive and negative cases
- [ ] Deployment steps are feasible and complete

## Best Practices

- Always verify against latest official documentation
- Provide specific line numbers or section references when raising issues
- Suggest concrete alternatives, not just flagging problems
- Distinguish between "blocking" and "nice-to-have" issues
- Preserve PRD structure and voice when making updates
- Add comments explaining why changes were made
- Keep user in the loop on major decisions
- Prioritize clarity over cleverness
- Test assumptions by asking questions before proposing solutions

## Common Issues to Look For

### Plugin-Related PRDs
- **CRITICAL**: Using non-existent event hooks (e.g., `session.interrupted`)
- **HIGH**: Assuming SDK methods or parameters that don't exist or are incorrect
- **MEDIUM**: Incorrect hook parameter structures or missing required fields
- **LOW**: Missing required frontmatter in agent files
- **HIGH**: Invalid or missing command registration approaches

### Workflow-Related PRDs
- **CRITICAL**: Infinite loops without max iteration limits
- **HIGH**: Missing state persistence strategy
- **CRITICAL**: No interruption handling (wrong hook usage)
- **MEDIUM**: Incorrect resume logic or state management
- **HIGH**: Missing error recovery paths

### Agent-Related PRDs
- **HIGH**: Undefined agent references that will cause runtime errors
- **MEDIUM**: Invalid permission settings
- **LOW**: Missing required agent configuration fields
- **MEDIUM**: Incorrect tool access configurations
- **HIGH**: Agent mode conflicts (primary vs subagent)

## Output Format

When reviewing a PRD, structure your findings as:

### CRITICAL ISSUES

**N. Issue Title**
- **Location**: Line numbers or section references
- **Issue**: Clear description of the problem
- **Correct Approach**: What should be done instead based on official docs
- **Fix**: Specific fix recommendation or action needed

### HIGH ISSUES

**N. Issue Title**
- **Location**: Line numbers or section references
- **Issue**: Clear description of the problem
- **Gap**: What information is missing or unclear
- **Fix**: Specific fix recommendation or question for user

### MEDIUM ISSUES

**N. Issue Title**
- **Location**: Line numbers or section references
- **Issue**: Clear description of the problem
- **Recommendation**: Suggested improvement or clarification
- **Fix**: Specific fix recommendation

### LOW ISSUES

**N. Issue Title**
- **Location**: Line numbers or section references
- **Issue**: Clear description of the problem
- **Recommendation**: Suggested improvement

### POSITIVE FINDINGS

✅ Correctly documented feature or approach
✅ Another correct finding

After presenting findings, summarize with user's confirmation:

```markdown
## Changes Based on User Feedback

1. [Issue Title] - [User's instruction]
2. [Issue Title] - [User's instruction]
3. [Issue Title] - [User's instruction]

[Proceed with updates to PRD...]
```

Then make the actual edits to the PRD file.

## Example Workflow

User says: "Verify official-docs/plugins/opsx-workflow/PRD.md"

1. Read PRD to understand workflow plugin requirements
2. Cross-check with:
    - official-docs/plugins.md (for plugin hooks and structure)
    - official-docs/sdk.md (for SDK methods)
    - official-docs/agents.md (for agent configuration)
    - official-docs/commands.md (for custom command registration)

3. Identify issues:

### CRITICAL ISSUES

**1. Non-existent Event Hook `session.interrupted`**
- **Location**: Lines 50, 1093
- **Issue**: Architecture diagram and workflow flow diagrams reference `session.interrupted` hook, which does not exist in OpenCode
- **Correct Hook**: `session.status` (which the implementation correctly uses to detect 'aborted'/'failed' states)
- **Fix**: Update all diagrams to remove `session.interrupted` reference

### HIGH ISSUES

**2. Missing Command Registration Documentation**
- **Location**: Lines 1612-1634
- **Issue**: PRD assumes `/opsx-flow-start` and `/opsx-flow-stop` work automatically but never explains how they're registered
- **Gap**: If unregistered, these commands won't reach the `command.executed` hook
- **Fix**: Add command registration instructions in deployment section (create markdown files in `.opencode/commands/`)

### POSITIVE FINDINGS

✅ SDK API calls are correct (`client.session.create`, `client.session.abort`, `client.session.messages`, `client.app.log`)
✅ Hook structure follows proper pattern (`command.executed`, `session.idle`, `session.status`)
✅ Agent configuration approach is valid (can be configured in opencode.json or markdown files)

4. Ask user for confirmation on each issue, gather their decisions

5. After user confirmation, update PRD with:
   - Replace `session.interrupted` with `session.status` in all diagrams and references
   - Add step to create `.opencode/commands/opsx-flow-start.md` and `opsx-flow-stop.md` in installation section
   - Update all related workflow flows and code examples

6. Present summary of changes made to PRD

## Notes

- This skill requires internet access for webfetching official docs
- When user provides specific documentation files, prioritize those over web sources
- Always validate against the latest version of official docs available
- If official docs are contradictory, note this and ask user which to follow
- Be thorough but efficient—focus on issues that would actually block implementation
