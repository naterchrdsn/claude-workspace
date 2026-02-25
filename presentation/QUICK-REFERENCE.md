# Subagent Orchestration Quick Reference

## Commands

| Command | Purpose | Model |
|---------|---------|-------|
| `/orchestrate-review <path>` | Code review with structured output | haiku→sonnet |
| `/rpi:research <request.md>` | GO/NO-GO feasibility analysis | haiku→sonnet |
| `/rpi:plan <feature-slug>` | Multi-perspective implementation plan | haiku→sonnet |
| `/rpi:implement <feature-slug>` | Phased execution with validation | haiku→sonnet |

## Agents

| Agent | Use For | Model | Skills |
|-------|---------|-------|--------|
| system-architect | Architecture design | opus | architecting-systems, writing-plans, mermaid |
| backend-architect | APIs, databases | sonnet | architecting-systems, managing-databases, errors |
| frontend-architect | UI, accessibility | sonnet | design, optimizing-performance, refactoring |
| tech-stack-researcher | Technology evaluation | sonnet | writing-plans, architecting-systems |
| requirements-analyst | Requirements clarity | sonnet | writing-plans, documenting-systems |
| performance-engineer | Performance optimization | sonnet | optimizing-performance, debugging, logs |
| security-engineer | Security audits | sonnet | debugging, handling-errors, verification |
| technical-writer | Documentation | sonnet | documenting-systems, writer |
| deep-research-agent | Research synthesis | opus | writing-plans, documenting-systems |
| code-review-agent | Code quality review | sonnet | debugging, refactoring, verification |

## RPI Workflow

```
REQUEST.md → /rpi:research → GO/NO-GO
                ↓ (if GO)
            /rpi:plan → pm.md + ux.md + eng.md + PLAN.md
                ↓
            /rpi:implement → Phase-by-phase with validation
```

## Creating New Orchestrated Workflows

### 1. Define Command (`commands/my-command.md`)
```yaml
---
description: What it does
model: haiku
---
# Command Name
Use Task tool to invoke agent:
- subagent_type: my-agent
- description: brief
- prompt: detailed instructions
```

### 2. Define Agent (`agents/my-agent.md`)
```yaml
---
name: my-agent
description: Use PROACTIVELY when...
tools: Read, Glob, Grep, Write
model: sonnet
skills:
  - skill-1
  - skill-2
---
# Agent instructions
```

### 3. Wire with Task Tool
```
Task(
  subagent_type="my-agent",
  description="Brief description",
  prompt="Detailed instructions..."
)
```

## Key Principles

| Do | Don't |
|----|-------|
| Use haiku for orchestration | Use opus for everything |
| Preload 3-5 relevant skills | Load all 22 skills |
| Validate between phases | Skip validation gates |
| Use Task tool for agents | Use bash to invoke agents |
| Write structured output | Return free-form prose |

## Cost Optimization

```
haiku  = $0.25/M tokens  → Orchestration, routing
sonnet = $3/M tokens     → Analysis, implementation
opus   = $15/M tokens    → Architecture, strategy
```

Smart routing: **haiku orchestrates → sonnet works → opus advises**

## File Locations

```
.claude/
├── commands/           # Entry points
│   ├── orchestrate-review.md
│   └── rpi/
│       ├── research.md
│       ├── plan.md
│       └── implement.md
├── agents/             # Domain experts
│   ├── code-review-agent.md
│   ├── system-architect.md
│   └── [10 total agents]
└── skills/             # Domain knowledge
    └── [22 skill directories]
```
