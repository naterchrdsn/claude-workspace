# Claude Workspace

A curated, production-ready collection of **agents**, **commands**, **skills**, and **documentation best practices** for using Claude in any project.

Combines research and expertise from three excellent sources:
- **claude-context-os** — Research-backed prompt design
- **claude-essentials** — Clean command/skill architecture
- **edmunds-claude-code** — Specialized agent patterns

See [SOURCES.md](SOURCES.md) for full attribution.

## What's Inside

### 🚀 Ready to Use

**Commands** — Quick workflows for development tasks
- Test, Debug, Plan, Refactor, Explain, Optimize, Perf Audit, Research, Docs
- Type `/command-name` to invoke
- See [Command Reference](docs/command-reference.md)

**Skills** — Reusable patterns that teach Claude *how* to approach work
- 22 skills covering testing, debugging, architecture, writing, performance, and more
- Load on-demand when you need a proven methodology
- See [Skill Reference](docs/skill-reference.md)

**Agents** — Expert AI personas for complex work
- System Architect, Backend Architect, Frontend Architect
- Tech Stack Researcher, Requirements Analyst, Performance Engineer
- Security Engineer, Technical Writer, Deep Research Agent
- Use for strategic decisions and deep analysis
- See [Agent Reference](docs/agent-reference.md)

**Documentation**
- [Documentation Playbook](docs/documentation-playbook.md) — How to write docs that teams use
- [Processing Protocol](docs/context/processing-protocol.md) — Handle large documents efficiently
- [Example Project Structure](examples/example-project-structure.md) — Start new projects right

### 🎯 Core Concepts

**CLAUDE.md** — Your Claude workspace configuration
- Focuses on what matters (removed unnecessary rules)
- Progressive disclosure (load tools on-demand)
- Session handoff patterns
- Research-backed design

## Quick Start

### 1. Copy to Your Project

```bash
# Copy claude-workspace to your project
cp -r /path/to/claude-workspace .claude-workspace

# Or in your existing project
cp /path/to/CLAUDE.md mynewproject/CLAUDE.md
cp -r /path/to/docs mynewproject/docs
```

### 2. Customize for Your Project

Edit `.claude/CLAUDE.md` with your project context:

```markdown
# CLAUDE.md

## Project

MyProject: [One-line description]

## Tech Stack

- Runtime: Node.js
- Frontend: React + TypeScript
- Database: PostgreSQL  
- Key Services: [List them]

## Where Things Live

- Features: [Where issues go]
- Decisions: [Where architecture decisions go]
- Documentation: docs/

## Current Focus

[What's being built this quarter]
```

### 3. Use Commands

In Claude Code or Claude.ai:

```
/test               # Run tests and analyze failures
/debug "bug issue"  # Debug a specific problem
/plan "feature"     # Create implementation plan
/refactor "code"    # Refactor safely
/explain "concept"  # Explain code or idea
/optimize "slow"    # Fix performance issues
/perf-audit "flow"  # Measure and optimize performance
/research "topic"   # Evidence-backed research
/docs "goal"        # Create or improve documentation
```

### 4. Use Agents

For complex work:

```
@system-architect          # Design scalable architecture
@backend-architect         # Design reliable backend systems
@frontend-architect        # Build accessible, performant UI
@tech-stack-researcher     # Plan technology choices
@requirements-analyst      # Clarify ambiguous specs
@performance-engineer      # Measure and improve performance
@security-engineer         # Assess security
@technical-writer          # Create clear documentation
@deep-research-agent       # Evidence-backed research and synthesis
```

## Documentation

- **[Documentation Playbook](docs/documentation-playbook.md)** — How to write docs that teams actually use
- **[Command Reference](docs/command-reference.md)** — Quick lookup for available commands
- **[Skill Reference](docs/skill-reference.md)** — When to load which skill
- **[Agent Reference](docs/agent-reference.md)** — When to use which agent
- **[Processing Protocol](docs/context/processing-protocol.md)** — Handle large documents efficiently
- **[Example Project Structure](examples/example-project-structure.md)** — Copy-paste directory layout for new projects

## Design Philosophy

### Commands vs. Skills vs. Agents

**Commands** are for **quick, routine tasks**:
- Run tests
- Debug a specific issue  
- Create a plan
- Refactor code
- Time to value: seconds to minutes

**Skills** are **reusable patterns**:
- How to test properly (Testing Trophy model)
- How to debug systematically (four-phase root cause analysis)
- How to optimize safely (measure-first approach)
- How to write clearly (writer + strategy-writer personas)
- How to architect cleanly (module boundaries, dependency management)
- Load on-demand when needed; 22 skills across 8 categories
- See [Skill Reference](docs/skill-reference.md)

**Agents** are **expert personas**:
- Strategic architecture decisions
- Technology research and planning
- Requirements clarification
- Performance optimization and profiling
- Documentation design and clarity
- Security assessment
- Deep research and synthesis
- Time to value: minutes to hours
- Deep, sustained focus

### Key Principles

1. **Progressive Disclosure** — Show what you need, hide details until needed
2. **Research-Backed** — Based on peer-reviewed papers and real usage
3. **Focused** — Fewer rules that actually matter > many rules ignored
4. **Practical** — Every recommendation is actionable

## Project Structure

```
claude-workspace/
├── CLAUDE.md                           # Your Claude configuration
├── SOURCES.md                          # Attribution & sources
├── README.md                           # This file
│
├── agents/                             # Expert personas (9)
│   ├── system-architect.md
│   ├── backend-architect.md
│   ├── frontend-architect.md
│   ├── tech-stack-researcher.md
│   ├── requirements-analyst.md
│   ├── performance-engineer.md
│   ├── security-engineer.md
│   ├── technical-writer.md
│   └── deep-research-agent.md
│
├── commands/                           # Quick workflows (9)
│   ├── test.md
│   ├── debug.md
│   ├── plan.md
│   ├── refactor.md
│   ├── explain.md
│   ├── optimize.md
│   ├── perf-audit.md
│   ├── research.md
│   └── docs.md
│
├── skills/                             # Reusable patterns (22)
│   ├── writing-tests/
│   ├── fixing-flaky-tests/
│   ├── condition-based-waiting/
│   ├── systematic-debugging/
│   ├── reading-logs/
│   ├── refactoring-code/
│   ├── handling-errors/
│   ├── verification-before-completion/
│   ├── preflight-checks/
│   ├── writing-plans/
│   ├── executing-plans/
│   ├── architecting-systems/
│   ├── migrating-code/
│   ├── managing-databases/
│   ├── documenting-systems/
│   ├── documenting-code-comments/
│   ├── writer/
│   ├── strategy-writer/
│   ├── optimizing-performance/
│   ├── post-mortem/
│   ├── design/
│   └── visualizing-with-mermaid/
│
├── docs/
│   ├── documentation-playbook.md       # How to write docs
│   ├── command-reference.md            # Command lookup
│   ├── skill-reference.md              # Skill lookup
│   ├── agent-reference.md              # Agent lookup
│   ├── context/
│   │   └── processing-protocol.md      # Handle large docs
│   └── templates/                      # Reusable templates
│
└── examples/
    └── example-project-structure.md    # Start new projects
```

## Integration with Claude Code

### In Claude Code (CLI)

Copy this workspace's `agents/`, `commands/`, and `skills/` into your project's `.claude/` directory. Claude Code picks them up automatically:

```
/test                    # Run tests and analyze failures
/debug                   # Systematic debugging
/plan                    # Implementation planning
/refactor                # Safe refactoring
/explain                 # Code/concept explanation
/optimize                # Performance optimization
/perf-audit              # Baseline and bottleneck analysis
/research                # Evidence-backed research
/docs                    # Documentation workflow
```

```
@system-architect        # Design scalable architecture
@backend-architect       # Design reliable backend systems
@frontend-architect      # Build accessible, performant UI
@tech-stack-researcher   # Plan technology choices
@requirements-analyst    # Clarify ambiguous specs
@performance-engineer    # Measure and improve performance
@security-engineer       # Assess security
@technical-writer        # Create clear documentation
@deep-research-agent     # Evidence-backed research synthesis
```

### In Your Project

Create `.claude/CLAUDE.md` with project context:

```markdown
# CLAUDE.md

You work with [Name], building [Project].

## Where Things Live

- Code: src/
- Tests: tests/
- Docs: docs/
- Architecture: ARCHITECTURE.md

## Current Focus

[What you're working on]
```

## Quick Reference

### When to Use Commands

| Command | Use When |
|---------|----------|
| `/test` | After making changes |
| `/debug` | Investigating a bug |
| `/plan` | Starting feature work |
| `/refactor` | Cleaning up code |
| `/explain` | Learning the codebase |
| `/optimize` | Performance is slow |
| `/perf-audit` | Baseline and bottleneck analysis |
| `/research` | Evidence-backed research needed |
| `/docs` | Writing or improving documentation |

### When to Use Skills

| Skill | Load When |
|-------|-----------|
| `writing-tests` | Writing tests; choosing test strategy |
| `systematic-debugging` | Investigating bugs or unexpected behavior |
| `refactoring-code` | Cleaning up or restructuring code |
| `verification-before-completion` | Before claiming any task is done |
| `writing-plans` | Planning a feature or migration |
| `optimizing-performance` | Addressing slow code |
| `writer` | Writing docs, READMEs, commit messages |
| `strategy-writer` | Executive-facing strategic documents |
| `visualizing-with-mermaid` | Creating architecture diagrams |
| `post-mortem` | Reviewing a session for improvements |

See [Skill Reference](docs/skill-reference.md) for all 22 skills.

### When to Use Agents

| Agent | Use When |
|-------|----------|
| System Architect | Designing system architecture |
| Backend Architect | Designing APIs and data systems |
| Frontend Architect | UX, accessibility, and UI architecture |
| Tech Stack Researcher | Planning new tech choices |
| Requirements Analyst | Specs are vague/unclear |
| Performance Engineer | Measuring and improving performance |
| Security Engineer | Security assessment needed |
| Technical Writer | Writing or improving documentation |
| Deep Research Agent | Research synthesis with citations |

## License

MIT License

This workspace combines patterns from:
- [claude-context-os](https://github.com/Arkya-AI/claude-context-os) (MIT)
- [claude-essentials](https://github.com/rileyhilliard/claude-essentials) (MIT)
- [edmunds-claude-code](https://github.com/edmund-io/edmunds-claude-code) (MIT)

See [SOURCES.md](SOURCES.md) for details.

---

**Built to help you work smarter with Claude.**
