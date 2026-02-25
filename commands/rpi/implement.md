---
description: RPI Phase 3 - Execute implementation plan phase by phase with validation gates
argument-hint: "<feature-slug>"
model: haiku
---

# RPI Implementation Phase

Execute the implementation plan for: `$ARGUMENTS`

## Prerequisites

- Planning phase completed
- `rpi/[feature-slug]/plan/PLAN.md` exists with task checklist

## Workflow

### Step 1: Load Plan

Read `rpi/[feature-slug]/plan/PLAN.md` and identify:
- Current phase (first incomplete phase)
- Tasks in current phase
- Exit criteria for the phase

### Step 2: Execute Phase Tasks

For each task in the current phase, use the Task tool to delegate:

```
Task tool parameters:
- subagent_type: [appropriate agent based on task type]
  - Code implementation → use Explore agent or direct execution
  - Testing → use code-review-agent
  - Documentation → use technical-writer
- description: [task description]
- prompt: [specific instructions with context from plan]
```

### Step 3: Validate Phase Completion

After all tasks in a phase, use the Task tool for validation:
```
Task tool parameters:
- subagent_type: code-review-agent
- description: Validate phase completion
- prompt: Review the implementation for Phase [N]:
  - Verify all tasks are complete
  - Check exit criteria are met
  - Run tests if applicable
  - Document any issues found
  Write validation report to rpi/[feature-slug]/implement/phase-[N]-validation.md
```

### Step 4: Update Progress

Update `rpi/[feature-slug]/implement/IMPLEMENT.md`:

```markdown
# Implementation Progress: [Feature Name]

## Status: [In Progress / Complete]

## Phase 1: Foundation
- [x] Task 1.1: [Completed date]
- [x] Task 1.2: [Completed date]
**Validation:** PASS - [date]

## Phase 2: Core Implementation
- [x] Task 2.1: [Completed date]
- [ ] Task 2.2: [In progress]
**Validation:** PENDING

## Issues Encountered
[Any blockers or changes from plan]

## Decisions Made
[Any deviations from original plan with rationale]
```

### Step 5: Continue or Complete

- If more phases remain: Continue to next phase
- If all phases complete: Generate completion summary

## Phase Validation Gates

Each phase must pass validation before proceeding:

**Foundation Phase:**
- [ ] Infrastructure/setup complete
- [ ] Dependencies installed
- [ ] Base tests passing

**Core Implementation Phase:**
- [ ] Main functionality implemented
- [ ] Unit tests written and passing
- [ ] No critical bugs

**Integration Phase:**
- [ ] Components integrated
- [ ] E2E tests passing
- [ ] Documentation updated

## Critical Requirements

1. **Use Task Tool Only**: Delegate work via Task tool
2. **Phase Gates**: Never skip validation between phases
3. **Document Progress**: Keep IMPLEMENT.md updated
4. **Commit Often**: Commit after each completed task

## Output

Return to user:
- **Phase Status**: Which phase completed/in progress
- **Tasks Completed**: Count of completed tasks
- **Validation Result**: PASS/FAIL for completed phases
- **Next Steps**: What happens next

## Usage

```
/rpi:implement user-authentication
/rpi:implement payment-integration --phase 2  # Resume specific phase
```
