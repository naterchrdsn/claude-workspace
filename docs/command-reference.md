# Command Reference

Quick lookup for available commands.

## Development Commands

| Command | Purpose | When to Use |
|---------|---------|-----------|
| `/test` | Run tests and analyze failures | After making changes, before commit |
| `/debug` | Start systematic debugging | When investigating a bug or error |
| `/plan` | Create implementation plan | At start of feature or refactoring work |
| `/refactor` | Refactor code safely | When cleaning up or reducing duplication |
| `/explain` | Break down code or concepts | When learning codebase or understanding patterns |
| `/optimize` | Find and fix performance issues | When addressing slow features or bottlenecks |
| `/perf-audit` | Run a measurement-driven performance audit | When you need baseline and bottleneck analysis |
| `/research` | Conduct deep research with synthesis | When you need evidence-backed recommendations |
| `/docs` | Create or improve documentation | When writing or refining technical docs |

## Usage Patterns

### Quick Workflow

```
/plan "add user authentication"
  ↓
/debug "authentication endpoint fails"
  ↓
/test
  ↓
/refactor "cleanup auth code"
  ↓
/test (verify refactoring didn't break anything)
```

### Debugging Workflow

```
/debug "app crashes on login"
  → Understand and reproduce
  → Investigate codebase
  → Form and test hypotheses
  → Implement fix
  → /test (verify fix)
```

### Performance Optimization

```
/optimize "dashboard loads slowly"
  → Identify bottleneck
  → Profile code/queries
  → Suggest improvements
  → Implement with verification
  → /test (ensure nothing broke)

### Research Workflow

```
/research "compare Redis vs Kafka for event streaming"
  → Clarify scope and constraints
  → Gather sources
  → Synthesize findings with citations
  → Deliver research report
```

### Documentation Workflow

```
/docs "write API usage guide for payments"
  → Define audience and goal
  → Draft with examples first
  → Add verification steps
  → Review for clarity
```
```

## Advanced Patterns

### Planning Complex Features

1. Use `/plan` to create detailed implementation strategy
2. Break into phases
3. For each phase: `/test`, `/debug`, `/refactor` as needed
4. Verify with `/test` at completion

### Code Review & Refactoring

1. `/explain` to understand existing code
2. `/refactor` to improve structure
3. `/test` to verify behavior preserved
4. Use agents for complex architectural decisions

### Performance Work

1. Establish baseline with profiling
2. Identify bottleneck with `/optimize`
3. Implement improvements
4. Verify gains justify complexity
5. Deploy and monitor

## Command Details

See:
- [test.md](../commands/test.md) — Testing framework
- [debug.md](../commands/debug.md) — Debugging methodology
- [plan.md](../commands/plan.md) — Planning framework
- [refactor.md](../commands/refactor.md) — Refactoring safely
- [explain.md](../commands/explain.md) — Understanding code
- [optimize.md](../commands/optimize.md) — Performance optimization
- [perf-audit.md](../commands/perf-audit.md) — Measurement-driven performance audit
- [research.md](../commands/research.md) — Evidence-backed research
- [docs.md](../commands/docs.md) — Documentation workflow
