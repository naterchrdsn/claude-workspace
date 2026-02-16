# Documentation Index

Quick navigation for claude-workspace documentation.

## Getting Started

**New to this workspace?** Start here:
1. [README.md](../README.md) — Overview and quick start
2. [Command Reference](command-reference.md) — What commands are available
3. [Agent Reference](agent-reference.md) — When to use agents

## Core Documentation

### How to Work (Guides & Recipes)

| Guide | Purpose |
|-------|---------|
| [Documentation Playbook](documentation-playbook.md) | How to write docs your team uses |
| [Processing Protocol](context/processing-protocol.md) | Handle large documents efficiently |
| [Command Reference](command-reference.md) | Quick lookup for all commands |
| [Agent Reference](agent-reference.md) | Understanding agents and when to use them |

### Detailed Guides

**Using This Workspace**
- [CLAUDE.md](../CLAUDE.md) — Workspace configuration and principles
- [SOURCES.md](../SOURCES.md) — Attribution and sources
- [Example Project Structure](../examples/example-project-structure.md) — Template for new projects

## For Your Projects

### Setting Up a New Project

1. Copy [Example Project Structure](../examples/example-project-structure.md)
2. Customize `.claude/CLAUDE.md` with your project context
3. Use templates from [Documentation Playbook](documentation-playbook.md)
4. See [Processing Protocol](context/processing-protocol.md) for handling documents

### Documenting Your Project

Follow the [Documentation Playbook](documentation-playbook.md):
- **How-To Guides** — Step-by-step instructions
- **Reference** — Look-up documentation
- **Explanations** — Understanding concepts
- **Getting Started** — For new team members

### Working with Large Documents

Use [Processing Protocol](context/processing-protocol.md):
1. List and prioritize documents
2. Process each individually
3. Create summaries
4. Work from summaries

## Quick Links

### Commands

See [Command Reference](command-reference.md) for:
- `/test` — Run and analyze tests
- `/debug` — Systematic debugging
- `/plan` — Implementation planning
- `/refactor` — Safe refactoring
- `/explain` — Code/concept explanation
- `/optimize` — Performance optimization

### Agents

See [Agent Reference](agent-reference.md) for:
- **System Architect** — Scale and design
- **Tech Stack Researcher** — Technology choices
- **Requirements Analyst** — Specification
- **Security Engineer** — Security & compliance

## By Use Case

### "I'm new to this project"
1. Read [README.md](../README.md)
2. Check [Example Project Structure](../examples/example-project-structure.md)
3. Find `docs/getting-started/` in your project

### "I need to write documentation"
→ [Documentation Playbook](documentation-playbook.md)

### "I have multiple large documents to review"
→ [Processing Protocol](context/processing-protocol.md)

### "I need to use Claude Code effectively"
→ [Command Reference](command-reference.md) and [Agent Reference](agent-reference.md)

### "I'm starting a new project"
→ [Example Project Structure](../examples/example-project-structure.md)

### "I don't know what command/agent to use"
→ [Command Reference](command-reference.md) or [Agent Reference](agent-reference.md)

## File Organization

```
docs/
├── README.md (this file)        ← You are here
├── command-reference.md          ← Quick command lookup
├── agent-reference.md            ← Quick agent lookup
├── documentation-playbook.md     ← How to write docs
├── context/
│   └── processing-protocol.md   ← Handle large docs
└── examples/
    └── (example outputs)
```

## Navigation Tips

- **Looking for how-to?** → Check [Documentation Playbook](documentation-playbook.md)
- **Need a command?** → Check [Command Reference](command-reference.md)
- **Need an agent?** → Check [Agent Reference](agent-reference.md)
- **Setting up new project?** → Check [Example Project Structure](../examples/example-project-structure.md)
- **Confused by command/agent?** → Check decision tree in [Agent Reference](agent-reference.md)

## Sources

This documentation is custom-created for claude-workspace, combining best practices from:
- [claude-context-os](https://github.com/Arkya-AI/claude-context-os)
- [claude-essentials](https://github.com/rileyhilliard/claude-essentials)
- [edmunds-claude-code](https://github.com/edmund-io/edmunds-claude-code)

See [SOURCES.md](../SOURCES.md) for full attribution.
