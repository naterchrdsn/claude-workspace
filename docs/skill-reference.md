# Skill Reference

Reusable patterns that teach Claude *how* to approach a category of work. Load a skill when you need a proven methodology, not just a quick action.

## Skills vs. Commands vs. Agents

**Skills** are for *how* — patterns and approaches you apply to work.
**Commands** are for *what* — quick workflows with a specific goal.
**Agents** are for *who* — expert personas for complex, sustained work.

A skill doesn't do the work for you. It gives Claude a proven framework to follow while doing it.

## Available Skills

### Testing

| Skill | Purpose | When to Load |
|-------|---------|--------------|
| `writing-tests` | Testing Trophy model — behavior-focused tests with real dependencies | Writing tests, choosing test types, avoiding mock anti-patterns |
| `fixing-flaky-tests` | Diagnose and fix tests that fail when run concurrently | Tests pass in isolation but fail together; shared state issues |
| `condition-based-waiting` | Replace arbitrary `sleep()` delays with condition polling | Tests fail intermittently; async operations need proper waits |

### Debugging

| Skill | Purpose | When to Load |
|-------|---------|--------------|
| `systematic-debugging` | Four-phase framework that finds root causes before proposing fixes | Investigating bugs, errors, unexpected behavior, failed tests |
| `reading-logs` | Targeted log analysis through search and iterative refinement | Investigating errors, debugging incidents, analyzing log patterns |

### Code Quality

| Skill | Purpose | When to Load |
|-------|---------|--------------|
| `refactoring-code` | Improve structure while preserving behavior through test verification | Cleaning up code, reducing duplication, reorganizing modules |
| `handling-errors` | Prevent silent failures and context loss in error handling | Writing try-catch blocks, designing error propagation |
| `verification-before-completion` | Run verification commands before claiming work is done | Before asserting any task is done, bug is fixed, or tests pass |
| `preflight-checks` | Auto-detect and run linters, formatters, and type checkers | Before committing; after any code changes |

### Planning & Execution

| Skill | Purpose | When to Load |
|-------|---------|--------------|
| `writing-plans` | Create implementation plans with tasks grouped by subsystem | Starting implementation work; planning a feature or migration |
| `executing-plans` | Execute plans with smart task grouping and parallelism | Working through an existing implementation plan |

### Architecture

| Skill | Purpose | When to Load |
|-------|---------|--------------|
| `architecting-systems` | Clean, scalable architecture during the build phase | Designing modules, defining boundaries, managing dependencies |
| `migrating-code` | Safe migrations with backward compatibility and reversibility | Upgrading dependencies, changing schemas, API versioning |
| `managing-databases` | Architecture decisions for PostgreSQL, DuckDB, Parquet, PGVector | Schema design, query optimization, storage strategy selection |

### Documentation & Writing

| Skill | Purpose | When to Load |
|-------|---------|--------------|
| `documenting-systems` | Task-oriented technical docs with progressive disclosure | Writing READMEs, API docs, architecture docs |
| `documenting-code-comments` | Standards for self-documenting code and minimal comments | Auditing inline docs; deciding when comments add value |
| `writer` | Writing style guide for human-sounding content (7 personas) | Any user-facing writing: docs, READMEs, commit messages, UI copy |
| `strategy-writer` | Executive-quality strategic docs in Economist/HBR style (4 personas) | Strategy memos, market analysis, business cases, research reports |

### Performance

| Skill | Purpose | When to Load |
|-------|---------|--------------|
| `optimizing-performance` | Measure-first optimization that balances gains against complexity | Addressing slow code, profiling issues, evaluating trade-offs |

### Process & Review

| Skill | Purpose | When to Load |
|-------|---------|--------------|
| `post-mortem` | Review a completed session to extract actionable improvements | After a debugging session, incident, or complex implementation |
| `preflight-checks` | Detect and run project linters, formatters, and type checkers | Before committing or claiming completion |

### Design & Visualization

| Skill | Purpose | When to Load |
|-------|---------|--------------|
| `design` | Precise, minimal design for dashboards and admin interfaces | Building SaaS UIs, data-heavy interfaces |
| `visualizing-with-mermaid` | Professional Mermaid diagrams with semantic styling | Flowcharts, sequence diagrams, architecture visualizations |

## Skill Details

Each skill lives in `skills/<skill-name>/SKILL.md` with optional `references/` for language-specific patterns:

```
skills/
├── writing-tests/
│   ├── SKILL.md
│   └── references/
│       ├── typescript-react.md
│       ├── python.md
│       └── go.md
├── systematic-debugging/
│   ├── SKILL.md
│   └── references/
│       └── debugging-techniques.md
└── ...
```

## Common Workflows Using Skills

### Before committing code
1. Load `preflight-checks` — run linters and type checkers
2. Load `verification-before-completion` — confirm tests pass

### Debugging a hard bug
1. Load `systematic-debugging` — four-phase root cause analysis
2. Load `reading-logs` if log-heavy investigation needed
3. Load `condition-based-waiting` if timing is involved

### Writing a new feature
1. Load `writing-plans` — structure the implementation
2. Load `writing-tests` — write behavior-focused tests first
3. Load `executing-plans` — work through the plan systematically

### Refactoring
1. Load `refactoring-code` — test-verified, behavior-preserving approach
2. Load `verification-before-completion` — confirm nothing broke

### Writing documentation or strategy content
1. Load `writer` — choose persona based on content type
2. Load `documenting-systems` for technical docs
3. Load `strategy-writer` for executive-facing documents

## Skills with Multiple Personas

Two skills use a persona system — load the sub-persona for your specific context:

**`writer`** (7 personas):
- The Engineer — technical docs, READMEs, API references
- The Architect — ADRs, design docs, tradeoff analyses
- The PM — strategy docs, product specs, roadmaps
- The Marketer — landing pages, blog posts, pitch content
- The Educator — tutorials, onboarding, walkthroughs
- The Contributor — commit messages, PRs, changelogs
- The UX Writer — error messages, UI copy, notifications

**`strategy-writer`** (4 personas):
- The Strategist — executive summaries, recommendations
- The Analyst — market research, competitive analysis
- The Advocate — investment cases, ROI justifications
- The Researcher — user research synthesis, customer insights

## Skill Lookup by Task

| Task | Skill to Load |
|------|--------------|
| "Write tests for this" | `writing-tests` |
| "Tests are flaky" | `fixing-flaky-tests` + `condition-based-waiting` |
| "Debug this bug" | `systematic-debugging` |
| "Read through logs" | `reading-logs` |
| "Refactor this code" | `refactoring-code` |
| "Make sure this is done" | `verification-before-completion` |
| "Plan this feature" | `writing-plans` |
| "Design the architecture" | `architecting-systems` |
| "Migrate to new library" | `migrating-code` |
| "Write this README" | `writer` (The Engineer) |
| "Write a strategy memo" | `strategy-writer` (The Strategist) |
| "Build a diagram" | `visualizing-with-mermaid` |
| "Optimize performance" | `optimizing-performance` |
| "Post-session review" | `post-mortem` |

## See Also

- [Command Reference](command-reference.md) — quick workflow commands (`/test`, `/debug`, `/plan`, etc.)
- [Agent Reference](agent-reference.md) — expert personas for complex, multi-step work
- [CLAUDE.md](../CLAUDE.md) — workspace configuration and which skill to use in which workflow
