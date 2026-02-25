---
description: RPI Phase 2 - Create comprehensive implementation plan with multiple expert perspectives
argument-hint: "<feature-slug>"
model: haiku
---

# RPI Planning Phase

Create a comprehensive implementation plan for: `$ARGUMENTS`

## Prerequisites

- Research phase completed with **GO** verdict
- `rpi/[feature-slug]/research/RESEARCH.md` exists

## Workflow

### Step 1: Product Requirements

Use the Task tool to invoke the requirements-analyst agent:
```
Task tool parameters:
- subagent_type: requirements-analyst
- description: Create product requirements
- prompt: Based on research at rpi/[feature-slug]/research/:
  - Create detailed user stories
  - Define acceptance criteria for each
  - Prioritize features (P0/P1/P2)
  - Identify MVP scope
  Write to rpi/[feature-slug]/plan/pm.md
```

### Step 2: UX Design (if applicable)

Use the Task tool to invoke the frontend-architect agent:
```
Task tool parameters:
- subagent_type: frontend-architect
- description: Design UX flows
- prompt: Based on product requirements at rpi/[feature-slug]/plan/pm.md:
  - Design user interaction flows
  - Define key screens/components
  - Specify accessibility requirements
  - Create component hierarchy
  Write to rpi/[feature-slug]/plan/ux.md
```

### Step 3: Technical Specification

Use the Task tool to invoke the backend-architect agent:
```
Task tool parameters:
- subagent_type: backend-architect
- description: Create technical specification
- prompt: Based on requirements and UX at rpi/[feature-slug]/plan/:
  - Design system architecture
  - Define API contracts
  - Specify data models
  - Identify integration points
  - Plan security considerations
  Write to rpi/[feature-slug]/plan/eng.md
```

### Step 4: Generate PLAN.md

Synthesize all perspectives into implementation roadmap:

```markdown
# Implementation Plan: [Feature Name]

## Overview
[Feature summary and scope]

## Phases

### Phase 1: Foundation
- [ ] Task 1.1: [Description]
- [ ] Task 1.2: [Description]
**Exit Criteria:** [What must be true to proceed]

### Phase 2: Core Implementation
- [ ] Task 2.1: [Description]
- [ ] Task 2.2: [Description]
**Exit Criteria:** [What must be true to proceed]

### Phase 3: Integration & Polish
- [ ] Task 3.1: [Description]
- [ ] Task 3.2: [Description]
**Exit Criteria:** [What must be true to proceed]

## Files to Create/Modify
[List all files with create/modify annotation]

## Dependencies
[External dependencies and blockers]

## Testing Strategy
- Unit: [What to test]
- Integration: [What to test]
- E2E: [What to test]

## Rollout Plan
[How to deploy safely]

## Success Metrics
[How to measure success]
```

Write to: `rpi/[feature-slug]/plan/PLAN.md`

## Critical Requirements

1. **Use Task Tool Only**: Invoke agents via Task tool
2. **Multi-Perspective**: Get PM, UX, and Engineering views
3. **Phased Approach**: Break into sequential phases with exit criteria
4. **Testable Tasks**: Each task should be verifiable

## Output

Return to user:
- **Phases**: Count and names of implementation phases
- **Tasks**: Total task count
- **Next Command**: Suggest `/rpi:implement [feature-slug]`

## Usage

```
/rpi:plan user-authentication
/rpi:plan payment-integration
```
