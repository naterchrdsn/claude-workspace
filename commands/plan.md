---
description: Create a detailed implementation plan for a feature or task
argument-hint: "<feature-description>"
---

Create a detailed implementation plan for: `$ARGUMENTS`

## Planning Framework

### 1. Understand Requirements
- What needs to be built?
- Who will use it?
- What is the success criteria?
- Are there dependencies or constraints?

### 2. Task Breakdown
- Identify distinct workstreams
- List affected files/components
- Estimate complexity (Small/Medium/Large)
- Identify dependencies and ordering

### 3. Risk Assessment
Identify potential blockers:
- Unknown dependencies
- API limitations
- Data migration needs
- Breaking changes
- Third-party service issues
- Performance risks

### 4. Implementation Steps
Create sequential, logical phases:
- **Phase 1: Setup/Preparation**
  - Infrastructure or tooling changes
  - Configuration updates
- **Phase 2: Core Implementation**
  - Backend/API changes
  - Data model changes
- **Phase 3: Integration**
  - Frontend integration
  - Testing setup
- **Phase 4: Quality & Documentation**
  - Test coverage
  - Documentation
  - Performance verification

### 5. Success Criteria
Define "done":
- Feature works as specified
- Tests pass (existing + new)
- No regressions
- Code reviewed
- Documented

## Output Format

**Task Analysis**
- Type: [Bug Fix / Feature / Refactor / Infrastructure]
- Complexity: [Small / Medium / Large]
- Estimated Time: X hours/days
- Priority: [High / Medium / Low]

**Implementation Plan**
- Phase 1: [Name] (Time estimate)
  - [ ] Step 1
  - [ ] Step 2
- Phase 2: [Name] (Time estimate)
  - [ ] Step 3
  - [ ] Step 4

**Files to Modify/Create**
```
app/page.ts (modify)
lib/utils.ts (modify)
components/NewComponent.ts (create)
```

**Testing Strategy**
- Unit tests for: [parts]
- Integration tests for: [parts]
- Manual testing for: [parts]

## Usage

- `/plan "add user authentication"` — Plan a new feature
- `/plan "refactor database layer"` — Plan refactoring work
