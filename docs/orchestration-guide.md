# Subagent Orchestration Guide

A comprehensive guide to building orchestrated workflows using the **Command → Agent → Skills** architecture pattern.

## Core Concept

Subagent orchestration separates concerns into three layers:

```
┌─────────────────────────────────────────────────────────────┐
│  COMMAND                                                     │
│  • Entry point for user                                      │
│  • Lightweight (haiku model)                                 │
│  • Orchestrates workflow                                     │
│  • Uses Task tool to invoke agents                          │
└─────────────────────────────────────────────────────────────┘
                              │
                              │ Task tool
                              ▼
┌─────────────────────────────────────────────────────────────┐
│  AGENT                                                       │
│  • Domain expert                                             │
│  • Heavy lifting (sonnet/opus model)                         │
│  • Has preloaded skills                                      │
│  • Specific tool access                                      │
└─────────────────────────────────────────────────────────────┘
                              │
                              │ Preloaded at startup
                              ▼
┌─────────────────────────────────────────────────────────────┐
│  SKILLS                                                      │
│  • Domain knowledge                                          │
│  • Methodologies and patterns                                │
│  • Reference material                                        │
│  • NOT invoked separately                                    │
└─────────────────────────────────────────────────────────────┘
```

## Why Orchestration?

### Cost Efficiency
| Component | Model | Cost | Purpose |
|-----------|-------|------|---------|
| Command | haiku | $0.25/M tokens | Route and orchestrate |
| Agent | sonnet | $3/M tokens | Complex analysis |
| Agent | opus | $15/M tokens | Strategic decisions |

Using haiku for orchestration and sonnet/opus only when needed can reduce costs by 10x+.

### Separation of Concerns
- **Commands**: User interaction, workflow coordination
- **Agents**: Domain expertise, complex reasoning
- **Skills**: Reusable knowledge, patterns

### Reusability
- One agent serves multiple commands
- Skills shared across agents
- Composable architecture

### Clarity
- Explicit tool allowlists prevent hallucination
- Preloaded skills ensure consistent methodology
- Structured output contracts

## Building Blocks

### 1. Command Definition

Commands are entry points that orchestrate workflows.

**Location:** `commands/[name].md`

**Structure:**
```yaml
---
description: What this command does
argument-hint: "<what-to-pass>"
model: haiku                    # Use haiku for orchestration
---

# Command Name

[Instructions for the command]

## Workflow

1. Step 1: Gather context
2. Step 2: Invoke agent via Task tool
3. Step 3: Present results

## Agent Invocation

Use the Task tool to invoke [agent-name]:
```
Task tool parameters:
- subagent_type: [agent-name]
- description: [brief description]
- prompt: [specific instructions]
- model: [model override if needed]
```

## Critical Requirements

1. **Use Task Tool Only**: Never bash commands to invoke agents
2. [Other requirements]
```

### 2. Agent Definition

Agents are domain experts that do the heavy lifting.

**Location:** `agents/[name].md`

**Structure:**
```yaml
---
name: agent-name
description: Use PROACTIVELY when [trigger conditions]
tools: Read, Glob, Grep, Write    # Explicit tool allowlist
model: sonnet                      # or opus for complex work
color: cyan                        # CLI color for visibility
memory: project                    # user/project/local
skills:                            # Preloaded at startup
  - skill-1
  - skill-2
  - skill-3
---

# Agent Name

[Agent persona and instructions]

## Your Task

Execute workflow using preloaded skills:
1. Step 1 using skill-1
2. Step 2 using skill-2
3. Step 3 using skill-3

## Workflow

[Detailed workflow steps]

## Boundaries

**Will:**
- [What this agent does]

**Will Not:**
- [What this agent doesn't do]
```

### 3. Skill Definition

Skills provide domain knowledge injected into agent context.

**Location:** `skills/[name]/SKILL.md`

**Structure:**
```yaml
---
name: skill-name
description: When to use this skill
---

# Skill Name

## Purpose

[What this skill teaches]

## When to Use

[Trigger conditions]

## Methodology

[Step-by-step approach]

## Anti-Patterns

[What NOT to do]

## References

[Links to additional materials in references/ subdirectory]
```

## The Task Tool

The Task tool is how commands invoke agents. **Critical**: Never use bash commands to invoke agents.

### Basic Invocation
```
Task tool parameters:
- subagent_type: code-review-agent
- description: Review authentication code
- prompt: Review src/auth/ for security issues...
```

### Full Parameters
```
Task tool parameters:
- subagent_type: [agent name from agents/*.md]
- description: [3-5 word summary]
- prompt: [detailed instructions]
- model: [haiku/sonnet/opus - optional, inherits from agent]
- run_in_background: [true/false - for long-running tasks]
```

### Chaining Agents

Commands can invoke multiple agents sequentially:

```
## Workflow

### Step 1: Research
Task(subagent_type="tech-stack-researcher", ...)
Wait for result

### Step 2: Implement
Task(subagent_type="backend-architect", ...)
Use result from Step 1

### Step 3: Review
Task(subagent_type="code-review-agent", ...)
Validate Step 2 output
```

## Patterns

### Pattern 1: Single Agent Orchestration

Simple command → single agent → skills

```
/orchestrate-review
    ↓
code-review-agent (skills: debugging, refactoring, verification)
    ↓
Review report
```

**Use when:** Single domain, straightforward workflow

### Pattern 2: Multi-Agent Pipeline

Command → agent 1 → agent 2 → agent 3

```
/rpi:plan
    ↓
requirements-analyst → pm.md
    ↓
frontend-architect → ux.md
    ↓
backend-architect → eng.md
    ↓
Combined PLAN.md
```

**Use when:** Multiple perspectives needed, complex deliverable

### Pattern 3: Validation Gates

Phase execution with validation between phases

```
/rpi:implement
    ↓
Execute Phase 1 tasks
    ↓
code-review-agent validates → PASS?
    ↓ YES
Execute Phase 2 tasks
    ↓
code-review-agent validates → PASS?
    ↓ YES
Complete
```

**Use when:** Critical work requiring checkpoints

### Pattern 4: Parallel Execution

Multiple independent agents in parallel

```
/comprehensive-analysis
    ↓
┌─────────────────┬─────────────────┬─────────────────┐
│ security-agent  │ performance-eng │ code-review     │
│ Security audit  │ Perf analysis   │ Quality review  │
└─────────────────┴─────────────────┴─────────────────┘
    ↓                    ↓                   ↓
Combined analysis report
```

**Use when:** Independent analyses can run concurrently

## Best Practices

### Do

1. **Use haiku for commands** - Orchestration is lightweight
2. **Use sonnet for most agents** - Good balance of cost/capability
3. **Use opus for strategic work** - Architecture, research synthesis
4. **Preload relevant skills** - Don't load everything
5. **Explicit tool allowlists** - Prevent hallucinated tool use
6. **Structured output contracts** - Define where output goes
7. **Validation gates** - Don't skip quality checks

### Don't

1. **Don't use bash to invoke agents** - Always use Task tool
2. **Don't skip validation phases** - Gates exist for a reason
3. **Don't overload agents with skills** - 3-5 skills max
4. **Don't use opus for everything** - Cost adds up
5. **Don't assume agent output** - Verify before proceeding

## Creating New Orchestrated Workflows

### Step 1: Define the Goal

What does the user want to accomplish? What's the deliverable?

### Step 2: Identify Agents Needed

Which domain experts are required? New or existing?

### Step 3: Map Skill Requirements

What knowledge does each agent need? Create skills if missing.

### Step 4: Design the Flow

Sequential? Parallel? Validation gates needed?

### Step 5: Create the Command

Write the orchestrating command with Task tool invocations.

### Step 6: Test the Flow

Run end-to-end and verify outputs at each step.

## Debugging Orchestration

### Agent Not Found
- Check `subagent_type` matches `name` in agent frontmatter
- Verify agent file is in `agents/` directory

### Skills Not Loading
- Check skill names in agent `skills` list match directories in `skills/`
- Verify `SKILL.md` exists in skill directory

### Wrong Model Used
- Check `model` in agent frontmatter
- Override with `model` parameter in Task call if needed

### Output Not Written
- Verify agent has `Write` in `tools` list
- Check output path is valid

## Examples

See these examples in the repository:

- `examples/orchestration/README.md` - Code review orchestration
- `docs/workflows/rpi-workflow.md` - RPI multi-phase workflow
- `commands/orchestrate-review.md` - Simple orchestration command
- `agents/code-review-agent.md` - Agent with preloaded skills
