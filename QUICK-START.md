# Quick Start Guide

Get up and running with claude-workspace in 5 minutes.

## What You Have

A production-ready collection of **agents**, **commands**, and **documentation** for working with Claude.

- ✅ 9 Specialized agents (System Architect, Backend Architect, Frontend Architect, Tech Stack Researcher, Requirements Analyst, Performance Engineer, Security Engineer, Technical Writer, Deep Research Agent)
- ✅ 9 Core commands (Test, Debug, Plan, Refactor, Explain, Optimize, Perf Audit, Research, Docs)
- ✅ 22 Skills covering testing, debugging, architecture, writing, performance, and more
- ✅ Documentation playbook and example project structure
- ✅ Processing protocol for handling large documents efficiently
- ✅ Everything is research-backed and practical

**Total:** Ready to copy into any project

## Step 1: Copy to Your Project (2 min)

**Option A: Start a new project**

```bash
# Create new project directory
mkdir my-project
cp -r claude-workspace my-project/.claude-workspace

# Or copy individual pieces
cp -r agents/ my-project/
cp -r commands/ my-project/
cp -r docs/ my-project/
cp CLAUDE.md my-project/.claude/CLAUDE.md
```

**Option B: Add to existing project**

```bash
# Copy to your existing project
cp CLAUDE.md my-existing-project/
cp -r agents/ my-existing-project/.claude/agents/
cp -r commands/ my-existing-project/.claude/commands/
cp -r docs/ my-existing-project/
```

## Step 2: Customize CLAUDE.md (2 min)

Edit your project's CLAUDE.md or `.claude/CLAUDE.md`:

```markdown
# CLAUDE.md

## Project

MyProject: Brief description of what it does

## Tech Stack

- Language: Python/TypeScript/etc
- Runtime: Node/Python/Go/etc
- Database: PostgreSQL/MongoDB/etc
- Key Libraries: [Your key dependencies]

## Where Things Live

- Source code: src/
- Tests: tests/
- Documentation: docs/
- Main configuration: config.json

## Current Focus

What you're building this quarter
```

## Step 3: Use Commands (1 min)

In Claude Code or Claude.ai, use commands directly:

```
/test               # Run tests
/debug "bug desc"   # Debug systematically
/plan "feature"     # Create implementation plan
/refactor "code"    # Refactor safely
/explain "concept"  # Explain code or ideas
/optimize "slow"    # Fix performance
/perf-audit "flow"  # Performance baseline
/research "topic"   # Evidence-backed research
/docs "goal"        # Documentation task
```

## Step 4: Load Skills (Optional)

For proven methodologies:

```
writing-tests              # Testing Trophy model, behavior-focused
systematic-debugging       # Four-phase root cause analysis
refactoring-code           # Behavior-preserving refactoring
verification-before-completion  # Confirm work is done
writing-plans              # Implementation plan structure
optimizing-performance     # Measure-first optimization
writer                     # Human-sounding docs and READMEs
strategy-writer            # Executive-quality strategic docs
visualizing-with-mermaid   # Architecture and flow diagrams
post-mortem                # Session review for improvements
```

See [Skill Reference](docs/skill-reference.md) for all 22 skills and when to load each.

## Step 5: Use Agents (Optional)

For complex, multi-step decisions:

```
@system-architect        # Design architecture
@backend-architect       # Design backend systems
@frontend-architect      # Design UI architecture
@tech-stack-researcher   # Plan technology
@requirements-analyst    # Clarify specs
@performance-engineer    # Optimize performance
@security-engineer       # Assessment
@technical-writer        # Documentation
@deep-research-agent     # Research synthesis
```

## Step 6: Read Key Documentation

When you need guidance:

- **[Documentation Playbook](docs/documentation-playbook.md)** — How to write docs
- **[Command Reference](docs/command-reference.md)** — All commands explained
- **[Skill Reference](docs/skill-reference.md)** — All 22 skills and when to load each
- **[Agent Reference](docs/agent-reference.md)** — When to use agents
- **[Example Project Structure](examples/example-project-structure.md)** — Directory layout template

## Pro Tips

✅ **Write decisions to disk** — After meaningful work, create a summary in docs/summaries/

✅ **Use processing protocol** — For 4+ large documents, follow docs/context/processing-protocol.md

✅ **Customize agents** — Add project-specific agents in your `.claude/agents/`

✅ **Build as you document** — Update docs alongside code changes

✅ **Use your CLAUDE.md** — The config makes all subsequent work more effective

## Folder Structure

```
my-project/
├── .claude/
│   ├── CLAUDE.md          ← Customize this
│   ├── agents/            ← Your agents
│   └── commands/          ← Your commands
├── docs/
│   ├── guides/            ← How-to docs
│   ├── concepts/          ← Explanations
│   ├── reference/         ← Tech reference
│   └── summaries/         ← Session state
├── src/                   ← Your code
├── tests/                 ← Your tests
├── README.md              ← Project overview
└── ARCHITECTURE.md        ← System design
```

## Reference

| Need | Doc |
|------|-----|
| Command lookup | [Command Reference](docs/command-reference.md) |
| Skill lookup | [Skill Reference](docs/skill-reference.md) |
| Agent lookup | [Agent Reference](docs/agent-reference.md) |
| Writing docs | [Documentation Playbook](docs/documentation-playbook.md) |
| Large documents | [Processing Protocol](docs/context/processing-protocol.md) |
| New project layout | [Example Project Structure](examples/example-project-structure.md) |
