---
description: Orchestrate a comprehensive code review using subagent with preloaded skills
argument-hint: "<file-or-directory>"
model: haiku
---

# Code Review Orchestrator

Orchestrate a comprehensive code review for: `$ARGUMENTS`

## Workflow

1. **Gather Context**: Identify what needs to be reviewed (files, PR, or directory)
2. **Invoke Review Agent**: Use the Task tool to delegate to the code-review-agent
3. **Present Results**: Summarize findings for the user

## Agent Invocation

Use the Task tool to invoke the code-review-agent:

```
Task tool parameters:
- subagent_type: code-review-agent
- description: Comprehensive code review
- prompt: Review the code at [target]. Apply your preloaded skills (systematic-debugging, verification-before-completion, refactoring-code) to analyze code quality, identify issues, and suggest improvements. Write findings to docs/reviews/[timestamp]-review.md
- model: sonnet
```

## Critical Requirements

1. **Use Task Tool Only**: DO NOT use bash commands to invoke agents. You MUST use the Task tool.
2. **Single Agent**: The code-review-agent handles all review aspects using its preloaded skills.
3. **Structured Output**: Ensure the agent writes findings to a review file.

## Output Summary

After the agent completes, provide:
- Files reviewed
- Critical issues found (if any)
- Improvement suggestions count
- Link to full review document

## Usage

```
/orchestrate-review src/api/
/orchestrate-review pull-request-123
/orchestrate-review src/components/Button.tsx
```

## Why Orchestration?

This command demonstrates the **Command → Agent → Skills** pattern:
- **Command** (this file): Lightweight entry point, uses haiku model
- **Agent** (code-review-agent): Does the heavy lifting with sonnet model
- **Skills**: Domain knowledge preloaded into agent context

This pattern enables:
- Cost efficiency (haiku for orchestration, sonnet for analysis)
- Reusable agents across multiple commands
- Skills as injectable domain knowledge
