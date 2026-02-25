# Orchestration Example: Code Review

This example demonstrates the **Command → Agent → Skills** architecture pattern for subagent orchestration.

## Architecture Overview

```
┌─────────────────────────────────────────────────────────────────┐
│                        User Request                              │
│                   "Review src/api/ for issues"                   │
└─────────────────────────────────────────────────────────────────┘
                              │
                              ▼
                    ┌──────────────────────┐
                    │  /orchestrate-review │
                    │  Command             │
                    │  Model: haiku        │
                    │  (Entry point)       │
                    └──────────────────────┘
                              │
                              │ Task tool invocation
                              │ (delegates to agent)
                              ▼
                    ┌──────────────────────┐
                    │  code-review-agent   │
                    │  Agent               │
                    │  Model: sonnet       │
                    │  (Heavy lifting)     │
                    │                      │
                    │  Preloaded Skills:   │
                    │  - systematic-debug  │
                    │  - refactoring-code  │
                    │  - handling-errors   │
                    │  - verification      │
                    └──────────────────────┘
                              │
              ┌───────────────┼───────────────┐
              │               │               │
              ▼               ▼               ▼
     ┌─────────────┐  ┌─────────────┐  ┌─────────────┐
     │ Glob/Read   │  │ Analysis    │  │ Write       │
     │ files       │  │ using skills│  │ report      │
     └─────────────┘  └─────────────┘  └─────────────┘
                              │
                              ▼
                    ┌──────────────────────┐
                    │ docs/reviews/        │
                    │ [date]-review.md     │
                    │ (Structured output)  │
                    └──────────────────────┘
                              │
                              ▼
                    ┌──────────────────────┐
                    │ Summary returned     │
                    │ to user via command  │
                    └──────────────────────┘
```

## Component Breakdown

### 1. Command: `/orchestrate-review`

**Location:** `commands/orchestrate-review.md`

**Purpose:** Lightweight entry point that:
- Accepts user input
- Invokes the agent via Task tool
- Presents results

**Model:** `haiku` (fast, cheap for orchestration)

```yaml
---
description: Orchestrate a comprehensive code review
argument-hint: "<file-or-directory>"
model: haiku
---
```

### 2. Agent: `code-review-agent`

**Location:** `agents/code-review-agent.md`

**Purpose:** Does the actual work:
- Reads and analyzes code
- Applies domain knowledge from skills
- Writes structured output

**Model:** `sonnet` (balanced intelligence for analysis)

```yaml
---
name: code-review-agent
tools: Read, Glob, Grep, Write
model: sonnet
color: cyan
memory: project
skills:
  - systematic-debugging
  - verification-before-completion
  - refactoring-code
  - handling-errors
---
```

### 3. Skills: Domain Knowledge

Skills are **preloaded into the agent's context** at startup. They provide:
- Proven methodologies
- Checklists and frameworks
- Language-specific patterns

The agent follows skill instructions as reference material, not as separate invocations.

## Key Pattern: Task Tool Invocation

The command invokes the agent using the Task tool:

```
Task tool parameters:
- subagent_type: code-review-agent
- description: Comprehensive code review
- prompt: [specific instructions with context]
- model: sonnet (or inherit from agent)
```

**Critical:** Never use bash commands to invoke agents. Always use the Task tool.

## Why This Pattern Works

### Cost Efficiency
- Haiku ($0.25/M tokens) for orchestration
- Sonnet ($3/M tokens) only for complex analysis
- 10x+ cost savings on simple routing

### Separation of Concerns
- Commands handle user interaction
- Agents handle domain logic
- Skills provide reusable knowledge

### Reusability
- Same agent can be invoked by multiple commands
- Skills shared across agents
- Composable architecture

### Clarity
- Explicit tool allowlist prevents hallucination
- Preloaded skills ensure consistent methodology
- Structured output contracts

## Execution Example

```
User: /orchestrate-review src/api/auth/

Command (haiku):
  → Parses input: "src/api/auth/"
  → Invokes: Task(subagent_type="code-review-agent", ...)

Agent (sonnet):
  → Globs: src/api/auth/**/*
  → Reads: 12 files
  → Analyzes using preloaded skills
  → Writes: docs/reviews/2024-01-15-review.md

Command (haiku):
  → Receives agent result
  → Presents: "Reviewed 12 files. Found 3 issues. See docs/reviews/..."

User sees: Clean summary with link to detailed report
```

## Files in This Example

```
commands/
  └── orchestrate-review.md     # Entry point command

agents/
  └── code-review-agent.md      # Worker agent with skills

skills/
  ├── systematic-debugging/     # Analysis methodology
  ├── refactoring-code/         # Quality patterns
  ├── handling-errors/          # Error handling checks
  └── verification-before-completion/  # Completion checklist

docs/reviews/
  └── [generated review files]  # Output location
```

## Adapting This Pattern

To create your own orchestrated workflow:

1. **Define the command** - What does the user invoke?
2. **Create the agent** - What skills does it need? What tools?
3. **Wire with Task tool** - Command invokes agent
4. **Specify output contract** - Where does output go?

See `docs/orchestration-guide.md` for detailed guidance.
