# Quick Start Guide

Get up and running with claude-workspace in 5 minutes.

## What You Have

A production-ready collection of **agents**, **commands**, and **documentation** for working with Claude.

- ✅ 9 Specialized agents (System Architect, Backend Architect, Frontend Architect, Tech Stack Researcher, Requirements Analyst, Performance Engineer, Security Engineer, Technical Writer, Deep Research Agent)
- ✅ 9 Core commands (Test, Debug, Plan, Refactor, Explain, Optimize, Perf Audit, Research, Docs)
- ✅ Documentation playbook and example project structure
- ✅ Processing protocol for handling large documents efficiently
- ✅ Everything is research-backed and practical

**Total:** ~500KB, ready to copy into any project

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

## Step 4: Use Agents (Optional, 1 min)

For complex decisions:

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

## Step 5: Read Key Documentation

When you need guidance:

- **[Documentation Playbook](docs/documentation-playbook.md)** — How to write docs
- **[Command Reference](docs/command-reference.md)** — All commands explained
- **[Agent Reference](docs/agent-reference.md)** — When to use agents
- **[Example Project Structure](examples/example-project-structure.md)** — Directory layout template

## Done! 🎉

You now have a Claude workspace configured for your project.

## Common Next Steps

### "I want to start a new feature"
1. Use `@requirements-analyst` if specs are unclear
2. Use `/plan "feature name"`
3. Work iteratively with `/test`, `/debug`, `/refactor`

### "I need to fix a bug"
1. Use `/debug "describe the bug"`
2. Systematically investigate
3. Use `/test` to verify the fix

### "I need to optimize performance"
1. Establish baseline (measure current performance)
2. Use `/optimize "slow part"`
3. Implement improvements
4. Verify with `/test`

### "I need to write documentation"
1. Read [Documentation Playbook](docs/documentation-playbook.md)
2. Follow the structure for your document type
3. Use progressive disclosure
4. Link between related docs

## Key Principles

**Commands** = Quick routines (seconds/minutes)
- `/test`, `/debug`, `/plan`, `/refactor`

**Agents** = Expert work (minutes/hours)
- Architecture, backend/frontend design, performance, documentation, research

**Documentation** = Written to be read
- Progressive disclosure, scannable, specific examples

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

## Getting Help

**Don't know which command to use?**
→ See [Command Reference](docs/command-reference.md)

**Don't know which agent to use?**
→ See [Agent Reference](docs/agent-reference.md)

**Want to write good documentation?**
→ See [Documentation Playbook](docs/documentation-playbook.md)

**Have lots of documents to review?**
→ See [Processing Protocol](docs/context/processing-protocol.md)

**Setting up a new project?**
→ See [Example Project Structure](examples/example-project-structure.md)

## That's It!

You're ready to use claude-workspace with your team.

The commands and agents are self-explanatory—just try them out.

Questions? Check the documentation or customize the agents/commands for your specific needs.

---

**Happy building! 🚀**
