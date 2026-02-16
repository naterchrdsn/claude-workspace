---
description: Refactor code while preserving behavior
argument-hint: "<refactoring-goal>"
---

Refactor code for: `$ARGUMENTS`

## Refactoring Principles

1. **Start with Tests**
   - Ensure existing tests pass
   - Add tests for untested code paths
   - Tests act as behavior specification

2. **One Change at a Time**
   - Make a small change
   - Verify tests still pass
   - Commit
   - Repeat

3. **Preserve Behavior**
   - Never refactor and change behavior simultaneously
   - If behavior needs to change, address in separate PR
   - Use tests to verify no behavior changed

4. **Common Refactorings**
   - Extract method/function
   - Inline variables
   - Move code to more logical locations
   - Rename for clarity
   - Reduce duplication
   - Simplify conditional logic

## Steps

1. **Understand Current Behavior**
   - Read and understand the code
   - Understand any tests
   - Understand dependencies

2. **Set Up Testing**
   - Ensure tests cover the code
   - Add delta testing if needed
   - Verify all tests pass

3. **Plan Refactoring Steps**
   - Identify changes (smallest possible)
   - Determine safe ordering
   - Plan rollback if needed

4. **Execute Incrementally**
   - Make one small change
   - Run tests
   - If pass, continue
   - If fail, revert and adjust

5. **Verify Completeness**
   - All tests pass
   - Code is cleaner
   - No behavior changed
   - Documentation updated

## Common Patterns

**Extract method** — Move logic into a named function
- Improves readability
- Enables reuse
- Simplifies testing

**Remove duplication** — DRY principle
- Single source of truth
- Easier to maintain
- Reduces side effects

**Simplify conditionals** — Make logic clearer
- Guard clauses over deeply nested ifs
- Boolean extraction for complex conditions
- Polymorphism over switch/if chains

## Usage

- `/refactor "extract database access patterns"` — Extract reusable patterns
- `/refactor "remove duplication in validation"` — Remove duplicate code
- `/refactor "simplify authentication flow"` — Simplify logic
