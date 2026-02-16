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

## Common Workflows

### Building a New Feature

1. **Clarify requirements** → Use `@requirements-analyst`
2. **Plan implementation** → Use `/plan` command
3. **Develop iteratively** → Use `/test`, `/debug`, `/refactor`
4. **Validate architecture** → Use `@system-architect`, `@backend-architect`, or `@frontend-architect`

### Debugging a Bug

1. **Understand the problem** → Use `/debug` command
2. **Get reproduction steps** → Systematic investigation
3. **Form hypotheses** → Test one at a time
4. **Fix root cause** — Not the symptom
5. **Verify** → Use `/test` to ensure fix works

### Optimizing Performance

1. **Establish baseline** → Measure current performance
2. **Identify bottleneck** → Use `/optimize` command
3. **Research alternatives** → `@tech-stack-researcher` if major changes
4. **Measure and optimize** → Use `@performance-engineer` for baseline + bottlenecks
5. **Verify** → Use `/test` to ensure nothing broke

### Refactoring Code

1. **Understand behavior** → Read and test existing code
2. **Plan changes** → `/plan` command or manual planning
3. **Make incremental changes** → One small change at a time
4. **Test after each change** → `/test` to verify behavior preserved
5. **Commit frequently** → Small, safe commits

## Documentation

### For Your Team

- **[Documentation Playbook](docs/documentation-playbook.md)** — How to write docs that teams actually use
- **[Command Reference](docs/command-reference.md)** — Quick lookup for available commands
- **[Agent Reference](docs/agent-reference.md)** — When to use which agent
- **[Processing Protocol](docs/context/processing-protocol.md)** — Handle large documents efficiently

### For New Projects

- **[Example Project Structure](examples/example-project-structure.md)** — Copy-paste directory layout and key files
- **CLAUDE.md template** — Provided in root, customize with your project context
- **README template** — See example structure

## Design Philosophy

### Commands vs. Skills vs. Agents

**Commands** are for **quick, routine tasks**:
- Run tests
- Debug a specific issue  
- Create a plan
- Refactor code
- Time to value: seconds to minutes

**Skills** are **reusable patterns**:
- How to test properly
- How to debug systematically
- How to optimize safely
- Load on-demand when needed
- Teaches proven approaches

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
├── agents/                             # Expert personas
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
├── commands/                           # Quick workflows
│   ├── test.md
│   ├── debug.md
│   ├── plan.md
│   ├── refactor.md
│   ├── explain.md
│   └── optimize.md
│
├── docs/
│   ├── documentation-playbook.md       # How to write docs
│   ├── command-reference.md            # Command lookup
│   ├── agent-reference.md              # Agent lookup
│   ├── context/
│   │   └── processing-protocol.md      # Handle large docs
│   ├── templates/                      # Reusable templates
│   └── examples/                       # Example outputs
│
└── examples/
    └── example-project-structure.md    # Start new projects
```

## Integration with Claude Code

### In Claude.ai (claude.ai/code)

Commands and agents work in Claude Code when you have this repo open:

```
/test               # Available as a command
@system-architect   # Available as an agent
@backend-architect  # Available as an agent
@frontend-architect # Available as an agent
@performance-engineer # Available as an agent
@technical-writer   # Available as an agent
@deep-research-agent # Available as an agent
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

## Token Efficiency

Built on research showing:
- **5-10 rules** are effective; 15+ rules fail silently
- **No explanatory prose** — instructions are cleaner
- **Plain language** — "CRITICAL" and "NEVER" cause overcorrection
- **Progressive disclosure** — Load details only when needed
- **Session handoffs** — Pass state via structured templates, not full context

Result: Better outputs with fewer tokens.

## Best Practices

### Use the Processing Protocol

When handling 4+ documents or any >2K word document:
1. List and prioritize
2. Process each document individually
3. Write summaries to disk
4. Read summaries, not originals
5. Cross-reference for contradictions

See: [Processing Protocol](docs/context/processing-protocol.md)

### Write Decisions to Disk

After meaningful work:
- **Create a summary** in `docs/summaries/`
- **Include**: decisions with rationale, exact numbers, file paths, open questions
- **Before session ends**: Write recovery file so you don't lose anything

### Document Architecture

Keep `ARCHITECTURE.md` current:
- **Why** major decisions were made
- **Trade-offs** considered
- **Known bottlenecks**
- **Growth plans**

### Document as You Build

Don't document after the fact:
- **Add to README.md** as you discover gotchas
- **Update ARCHITECTURE.md** when you change structure
- **Write guides** as you figure out patterns
- **Keep docs in git** alongside code

## Getting Help

### Understanding Your Project

1. Read `CLAUDE.md` to understand goals
2. Read `ARCHITECTURE.md` for system design
3. Follow `docs/getting-started/` for specifics

### Solving a Problem

1. Check `docs/faq.md` if one exists
2. Look for similar issues in code
3. Create a test that reproduces the issue
4. Debug systematically with `/debug`

### Learning the Codebase

1. Start with `README.md`
2. Read `ARCHITECTURE.md`
3. Use `/explain` command on specific code
4. Check existing tests for usage examples

## License

MIT License

This workspace combines patterns from:
- [claude-context-os](https://github.com/Arkya-AI/claude-context-os) (MIT)
- [claude-essentials](https://github.com/rileyhilliard/claude-essentials) (MIT)
- [edmunds-claude-code](https://github.com/edmund-io/edmunds-claude-code) (MIT)

See [SOURCES.md](SOURCES.md) for details.

## What's Next?

1. **Copy to your project** — Use the example structure
2. **Customize CLAUDE.md** — Add your project context
3. **Try a command** — Use `/test` or `/debug`
4. **Read documentation** — Start with [Documentation Playbook](docs/documentation-playbook.md)
5. **Use agents for complex work** — Try `@requirements-analyst`, `@backend-architect`, or `@system-architect`

## Questions or Improvements?

This is a curated, opinionated collection. Adapt it to your needs:
- Add project-specific agents in your `.claude/`
- Create custom commands for your workflow
- Extend documentation for your domain

The goal is a workspace you and your team actually use every day.

---

**Built to help you work smarter with Claude.**
