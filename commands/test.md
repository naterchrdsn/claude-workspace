---
description: Run tests and analyze failures
argument-hint: "[test-command]"
---

Run tests and analyze results.

## Steps

1. **Detect Test Command** (if no custom command provided)
   - Check for package.json (npm test / yarn test)
   - Check for pytest.ini or setup.py (pytest)
   - Check for Cargo.toml (cargo test)
   - Check for Makefile with test target
   - Check for go.mod (go test ./...)
   - Check for Jest configuration (jest)

2. **Run Tests**
   Execute the detected or provided test command

3. **Analyze Failures** (if any occur)
   - Parse failure messages
   - Identify root causes
   - Reference specific file:line locations
   - Suggest fixes based on error patterns

4. **Report Results**
   Summary including:
   - Total tests run
   - Passed/failed/skipped counts
   - For failures: clear, actionable feedback
   - Suggestions for next steps

## Usage

- `/test` — Auto-detect and run tests
- `/test npm test` — Run specific test command
- `/test pytest -v` — Run with verbose output
