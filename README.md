# Claude Workspace

A curated, production-ready collection of **agents**, **commands**, **skills**, and **subagent orchestration patterns** for using Claude in any project.

**New in this version:** Full subagent orchestration support with the **Command → Agent → Skills** architecture pattern and the **RPI workflow** (Research → Plan → Implement).

Combines research and expertise from multiple sources:
- **claude-context-os** — Research-backed prompt design
- **claude-essentials** — Clean command/skill architecture
- **edmunds-claude-code** — Specialized agent patterns
- **shanraisshan/claude-code-best-practice** — Subagent orchestration patterns

See [SOURCES.md](SOURCES.md) for full attribution.

## What's Inside

### Subagent Orchestration (NEW)

The **Command → Agent → Skills** pattern enables cost-effective, high-quality AI workflows:

```
Command (haiku, cheap)
    ↓ Task tool
Agent (sonnet/opus, powerful)
    ↓ Preloaded
Skills (domain knowledge)
```

**Orchestrated Commands:**
- `/orchestrate-review <path>` — Code review with structured output
- `/rpi:research <request.md>` — GO/NO-GO feasibility analysis
- `/rpi:plan <feature-slug>` — Multi-perspective implementation plan
- `/rpi:implement <feature-slug>` — Phased execution with validation

**Documentation:**
- [Orchestration Guide](docs/orchestration-guide.md) — How to build orchestrated workflows
- [RPI Workflow](docs/workflows/rpi-workflow.md) — Research → Plan → Implement
- [Orchestration Example](examples/orchestration/README.md) — Code review example

### Ready to Use

**Commands** — Quick workflows for development tasks (12 commands)
- Test, Debug, Plan, Refactor, Explain, Optimize, Perf Audit, Research, Docs
- Orchestrated: orchestrate-review, rpi:research, rpi:plan, rpi:implement
- Type `/command-name` to invoke
- See [Command Reference](docs/command-reference.md)

**Skills** — Reusable patterns that teach Claude *how* to approach work
- 22 skills covering testing, debugging, architecture, writing, performance, and more
- Preloaded into agents or loaded on-demand
- See [Skill Reference](docs/skill-reference.md)

**Agents** — Expert AI personas with preloaded skills (10 agents)
- System Architect, Backend Architect, Frontend Architect
- Tech Stack Researcher, Requirements Analyst, Performance Engineer
- Security Engineer, Technical Writer, Deep Research Agent
- Code Review Agent (NEW)
- All agents have enhanced frontmatter with tools, skills, and model config
- See [Agent Reference](docs/agent-reference.md)

**Presentation Materials** (NEW)
- [Subagent Orchestration Presentation](presentation/SUBAGENT-ORCHESTRATION.md) — CTO-ready presentation
- [Quick Reference](presentation/QUICK-REFERENCE.md) — Team adoption cheat sheet

### Core Concepts

**CLAUDE.md** — Your Claude workspace configuration
- Focuses on what matters (removed unnecessary rules)
- Progressive disclosure (load tools on-demand)
- Subagent orchestration patterns
- Session handoff patterns
- Research-backed design

## Quick Start

### 1. Copy to Your Project

```bash
# Copy claude-workspace to your project's .claude directory
cp -r /path/to/claude-workspace/.  your-project/.claude/

# Or copy specific components
cp -r /path/to/claude-workspace/agents your-project/.claude/
cp -r /path/to/claude-workspace/commands your-project/.claude/
cp -r /path/to/claude-workspace/skills your-project/.claude/
```

### 2. Try Orchestrated Review

```bash
# Run an orchestrated code review
/orchestrate-review src/api/

# This invokes code-review-agent via Task tool
# Agent uses preloaded debugging, refactoring, and verification skills
# Output goes to docs/reviews/
```

### 3. Try RPI Workflow

```bash
# Create a feature request
mkdir -p rpi/my-feature
# Edit rpi/my-feature/REQUEST.md with your feature description

# Phase 1: Research (GO/NO-GO)
/rpi:research rpi/my-feature/REQUEST.md

# Phase 2: Plan (if GO)
/rpi:plan my-feature

# Phase 3: Implement
/rpi:implement my-feature
```

### 4. Customize for Your Project

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

## Design Philosophy

### The Orchestration Pattern

**Commands** are **entry points** (lightweight):
- Orchestrate workflows using haiku model
- Invoke agents via Task tool
- Present results to user

**Agents** are **domain experts** (powerful):
- Do heavy lifting with sonnet/opus models
- Have preloaded skills for domain knowledge
- Explicit tool access (Read, Write, Grep, etc.)

**Skills** are **injectable knowledge**:
- Methodologies and patterns
- Preloaded into agent context at startup
- Not invoked separately—reference material

### Cost Optimization

| Component | Model | Cost | Purpose |
|-----------|-------|------|---------|
| Command | haiku | $0.25/M tokens | Orchestrate |
| Agent | sonnet | $3/M tokens | Analyze |
| Agent | opus | $15/M tokens | Strategize |

Smart routing can reduce costs by **10x** while maintaining quality.

### Key Principles

1. **Progressive Disclosure** — Show what you need, hide details until needed
2. **Research-Backed** — Based on peer-reviewed papers and real usage
3. **Focused** — Fewer rules that actually matter > many rules ignored
4. **Practical** — Every recommendation is actionable
5. **Cost-Effective** — Use the right model for each task

## Project Structure

```
claude-workspace/
├── CLAUDE.md                           # Your Claude configuration
├── SOURCES.md                          # Attribution & sources
├── README.md                           # This file
│
├── agents/                             # Expert personas (10)
│   ├── system-architect.md             # Architecture design (opus)
│   ├── backend-architect.md            # APIs, databases (sonnet)
│   ├── frontend-architect.md           # UI, accessibility (sonnet)
│   ├── tech-stack-researcher.md        # Technology evaluation (sonnet)
│   ├── requirements-analyst.md         # Requirements clarity (sonnet)
│   ├── performance-engineer.md         # Performance optimization (sonnet)
│   ├── security-engineer.md            # Security audits (sonnet)
│   ├── technical-writer.md             # Documentation (sonnet)
│   ├── deep-research-agent.md          # Research synthesis (opus)
│   └── code-review-agent.md            # Code quality review (sonnet) [NEW]
│
├── commands/                           # Quick workflows (12)
│   ├── test.md
│   ├── debug.md
│   ├── plan.md
│   ├── refactor.md
│   ├── explain.md
│   ├── optimize.md
│   ├── perf-audit.md
│   ├── research.md
│   ├── docs.md
│   ├── orchestrate-review.md           # [NEW] Orchestrated code review
│   └── rpi/                            # [NEW] RPI workflow
│       ├── research.md                 # GO/NO-GO analysis
│       ├── plan.md                     # Multi-perspective planning
│       └── implement.md                # Phased execution
│
├── skills/                             # Reusable patterns (22)
│   └── [22 skill directories]
│
├── docs/
│   ├── orchestration-guide.md          # [NEW] How to orchestrate
│   ├── workflows/
│   │   └── rpi-workflow.md             # [NEW] RPI documentation
│   ├── documentation-playbook.md
│   ├── command-reference.md
│   ├── skill-reference.md
│   ├── agent-reference.md
│   ├── context/
│   │   └── processing-protocol.md
│   ├── templates/
│   └── reviews/                        # [NEW] Review output location
│
├── examples/
│   ├── orchestration/                  # [NEW] Orchestration example
│   │   └── README.md
│   ├── rpi-template/                   # [NEW] RPI feature template
│   │   ├── REQUEST.md
│   │   ├── research/
│   │   ├── plan/
│   │   └── implement/
│   └── example-project-structure.md
│
└── presentation/                       # [NEW] CTO presentation materials
    ├── SUBAGENT-ORCHESTRATION.md       # Full presentation
    └── QUICK-REFERENCE.md              # Team cheat sheet
```

## Quick Reference

### Orchestrated Commands

| Command | Purpose | Agents Used |
|---------|---------|-------------|
| `/orchestrate-review <path>` | Code review | code-review-agent |
| `/rpi:research <request>` | GO/NO-GO | requirements-analyst, tech-stack-researcher, system-architect |
| `/rpi:plan <slug>` | Planning | requirements-analyst, frontend-architect, backend-architect |
| `/rpi:implement <slug>` | Execution | code-review-agent, technical-writer, others |

### Standard Commands

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

| Agent | Model | Use When |
|-------|-------|----------|
| system-architect | opus | System architecture, scalability |
| backend-architect | sonnet | APIs, databases, security |
| frontend-architect | sonnet | UI, accessibility, performance |
| tech-stack-researcher | sonnet | Technology evaluation |
| requirements-analyst | sonnet | Vague specs, discovery |
| performance-engineer | sonnet | Profiling, optimization |
| security-engineer | sonnet | Security assessment |
| technical-writer | sonnet | Documentation |
| deep-research-agent | opus | Research synthesis |
| code-review-agent | sonnet | Code quality review |

## For CTOs and Team Leads

See [presentation/SUBAGENT-ORCHESTRATION.md](presentation/SUBAGENT-ORCHESTRATION.md) for:
- Executive summary of subagent orchestration
- Cost/benefit analysis
- Demo script
- Team adoption path
- Metrics to track

## License

MIT License

This workspace combines patterns from:
- [claude-context-os](https://github.com/Arkya-AI/claude-context-os) (MIT)
- [claude-essentials](https://github.com/rileyhilliard/claude-essentials) (MIT)
- [edmunds-claude-code](https://github.com/edmund-io/edmunds-claude-code) (MIT)
- [shanraisshan/claude-code-best-practice](https://github.com/shanraisshan/claude-code-best-practice) (reference)

See [SOURCES.md](SOURCES.md) for details.

---

**Built to help you work smarter with Claude through intelligent orchestration.**
