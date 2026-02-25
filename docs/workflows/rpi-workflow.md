# RPI Workflow: Research → Plan → Implement

A systematic development workflow with **validation gates** at each phase. Prevents wasted effort on non-viable features and ensures comprehensive documentation.

## Overview

```
┌─────────────────────────────────────────────────────────────────┐
│                    Feature Request                               │
│              "Add OAuth2 authentication"                         │
└─────────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────────┐
│  PHASE 1: RESEARCH                                              │
│  /rpi:research rpi/oauth2/REQUEST.md                            │
│                                                                 │
│  Agents: requirements-analyst, tech-stack-researcher,           │
│          system-architect                                       │
│                                                                 │
│  Output: RESEARCH.md with GO/NO-GO verdict                      │
└─────────────────────────────────────────────────────────────────┘
                              │
                      ┌───────┴───────┐
                      │   GO?         │
                      └───────┬───────┘
               NO ◄───────────┴───────────► YES
               │                            │
               ▼                            ▼
        ┌──────────┐          ┌─────────────────────────────────────┐
        │ STOP     │          │  PHASE 2: PLAN                      │
        │ Document │          │  /rpi:plan oauth2                   │
        │ reasons  │          │                                     │
        └──────────┘          │  Agents: requirements-analyst,      │
                              │          frontend-architect,        │
                              │          backend-architect          │
                              │                                     │
                              │  Output: pm.md, ux.md, eng.md,      │
                              │          PLAN.md                    │
                              └─────────────────────────────────────┘
                                            │
                                            ▼
                              ┌─────────────────────────────────────┐
                              │  PHASE 3: IMPLEMENT                 │
                              │  /rpi:implement oauth2              │
                              │                                     │
                              │  Agents: Various based on task      │
                              │                                     │
                              │  Process:                           │
                              │  - Execute Phase 1 tasks            │
                              │  - Validate → PASS?                 │
                              │  - Execute Phase 2 tasks            │
                              │  - Validate → PASS?                 │
                              │  - Execute Phase 3 tasks            │
                              │  - Final validation                 │
                              │                                     │
                              │  Output: Working feature + docs     │
                              └─────────────────────────────────────┘
```

## Why RPI?

### The Problem
- Features start without clear requirements
- Technical feasibility discovered too late
- No validation between phases
- Wasted effort on non-viable features
- Inconsistent documentation

### The Solution
- **Research Gate**: Validate viability before planning
- **Multi-Perspective Planning**: PM, UX, Engineering views
- **Phased Implementation**: Exit criteria between phases
- **Agent Orchestration**: Right expert for each task

## Quick Start

### 1. Create Feature Request

```bash
mkdir -p rpi/user-auth
```

Create `rpi/user-auth/REQUEST.md`:
```markdown
# Feature Request: User Authentication

## Problem
Users cannot securely access the application.

## Proposed Solution
Implement OAuth2 authentication with Google and GitHub providers.

## Success Criteria
- Users can sign in with Google
- Users can sign in with GitHub
- Session persists across browser restarts
- Logout clears all session data

## Constraints
- Must work with existing user database
- No paid authentication services
```

### 2. Research Phase

```
/rpi:research rpi/user-auth/REQUEST.md
```

Agents involved:
- **requirements-analyst**: Clarifies requirements
- **tech-stack-researcher**: Assesses feasibility
- **system-architect**: Checks alignment

Output: `rpi/user-auth/research/RESEARCH.md` with **GO/NO-GO**

### 3. Plan Phase (if GO)

```
/rpi:plan user-auth
```

Agents involved:
- **requirements-analyst**: User stories + acceptance criteria
- **frontend-architect**: UX flows + components
- **backend-architect**: API design + data models

Output:
- `rpi/user-auth/plan/pm.md` - Product requirements
- `rpi/user-auth/plan/ux.md` - UX design
- `rpi/user-auth/plan/eng.md` - Technical spec
- `rpi/user-auth/plan/PLAN.md` - Implementation roadmap

### 4. Implement Phase

```
/rpi:implement user-auth
```

Process:
- Execute tasks phase by phase
- Validate each phase before proceeding
- Document progress in `IMPLEMENT.md`
- Commit after each task

Output: Working feature with full documentation

## Folder Structure

```
rpi/
└── [feature-slug]/
    ├── REQUEST.md                 # Initial feature request
    ├── research/
    │   ├── requirements.md        # Parsed requirements
    │   ├── feasibility.md         # Technical assessment
    │   ├── alignment.md           # Strategic fit
    │   └── RESEARCH.md            # GO/NO-GO decision
    ├── plan/
    │   ├── pm.md                  # Product requirements
    │   ├── ux.md                  # UX design
    │   ├── eng.md                 # Technical spec
    │   └── PLAN.md                # Implementation roadmap
    └── implement/
        ├── phase-1-validation.md  # Phase 1 review
        ├── phase-2-validation.md  # Phase 2 review
        └── IMPLEMENT.md           # Progress tracking
```

## Agents Used

| Phase | Agent | Purpose |
|-------|-------|---------|
| Research | requirements-analyst | Parse and clarify requirements |
| Research | tech-stack-researcher | Assess technical feasibility |
| Research | system-architect | Check strategic alignment |
| Plan | requirements-analyst | User stories + acceptance criteria |
| Plan | frontend-architect | UX design + components |
| Plan | backend-architect | Technical specification |
| Implement | code-review-agent | Phase validation |
| Implement | technical-writer | Documentation |
| Implement | [various] | Task execution |

## Validation Gates

### Research → Plan Gate
- [ ] RESEARCH.md exists with verdict
- [ ] Verdict is GO or CONDITIONAL
- [ ] All open questions resolved

### Plan → Implement Gate
- [ ] PLAN.md exists with phases
- [ ] All phases have exit criteria
- [ ] Dependencies identified

### Phase → Phase Gates
- [ ] All tasks in phase complete
- [ ] Exit criteria met
- [ ] Validation report generated
- [ ] No blocking issues

## Best Practices

### Do
- Start every feature with `/rpi:research`
- Document NO-GO decisions for future reference
- Keep phases small (3-5 tasks each)
- Commit after each task completion
- Update IMPLEMENT.md in real-time

### Don't
- Skip research phase for "obvious" features
- Proceed past validation failures
- Combine unrelated work in one RPI
- Ignore open questions from research

## Customization

The RPI workflow is designed to be customized:

1. **Add domain-specific agents**: Security review, compliance check
2. **Modify validation criteria**: Add org-specific gates
3. **Extend phases**: Split into more granular phases
4. **Add templates**: Org-specific REQUEST.md format

See `examples/rpi-template/` for a ready-to-copy structure.
