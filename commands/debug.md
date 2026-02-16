---
description: Start systematic debugging session for a bug
argument-hint: "<bug-description>"
---

Start systematic debugging for: `$ARGUMENTS`

## Debugging Framework (4 phases)

### Phase 1: Understand & Reproduce
- State the observed behavior clearly
- Understand expected behavior
- Identify reproduction steps
- Gather relevant error messages or logs

### Phase 2: Investigate
- Examine code paths leading to the bug
- Check for recent changes
- Review related tests
- Look for similar issues elsewhere
- Use log analysis for distributed systems

### Phase 3: Form & Test Hypotheses
- What could cause this behavior?
- Which hypothesis is most likely?
- Test the hypothesis with experiments
- Narrow down to root cause

### Phase 4: Fix & Verify
- Implement fix for root cause (not symptoms)
- Run relevant tests
- Verify fix doesn't introduce new issues
- Verify fix matches expected behavior

## Key Principles

- **Understand first, fix second** — Fix the root cause, not the symptom
- **Reproduce systematically** — Unless you can reproduce it, you'll fix the wrong thing
- **Write a test** — Add a test that would have caught this bug
- **Document the finding** — Record what you learned

## Usage

- `/debug "app crashes on login"` — Debug a specific issue
- `/debug "memory leak in X"` — Debug performance issue
- `/debug` with logs attached — Use attached logs for investigation
