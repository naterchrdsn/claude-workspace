# Example Project Structure

Start new projects or migrate existing ones using this structure.

## Directory Layout

```
my-project/
├── .claude/                   # Claude workspace configuration
│   └── CLAUDE.md             # Project-specific Claude config
│
├── docs/
│   ├── getting-started/      # New team member onboarding
│   │   ├── setup.md
│   │   ├── first-feature.md
│   │   └── debugging.md
│   ├── guides/               # How-to documents
│   │   ├── authentication.md
│   │   ├── testing.md
│   │   ├── deployment.md
│   │   └── performance.md
│   ├── reference/            # Technical reference
│   │   ├── api.md
│   │   ├── configuration.md
│   │   └── cli-commands.md
│   ├── concepts/             # Understanding documents
│   │   ├── architecture.md
│   │   ├── data-flow.md
│   │   └── state-management.md
│   ├── summaries/            # Claude session state (git-ignored)
│   │   ├── handoff-2024-01-15-auth-feature.md
│   │   ├── source-design-spec.md
│   │   └── recovery-2024-01-16.md
│   └── faq.md
│
├── .claude-context-os/       # (Optional) If using context-os templates
│   └── templates/
│       └── claude-templates.md
│
├── src/                      # Application code
│   ├── api/
│   ├── components/
│   ├── lib/
│   └── services/
│
├── tests/                    # Test files
│   ├── unit/
│   ├── integration/
│   └── e2e/
│
├── README.md                 # Project overview
├── ARCHITECTURE.md           # System design document
├── CONTRIBUTING.md           # How to contribute
└── .gitignore               # Include: docs/summaries/
```

## Core Files to Create

### 1. .claude/CLAUDE.md

Project-specific Claude configuration:

```markdown
# CLAUDE.md

## Project

[Project Name]: [One-line description of what this project does]

Example: "Analytics Dashboard: Real-time metrics visualization for SaaS platforms"

## Key Context

- **Tech Stack**: React, TypeScript, Node.js, PostgreSQL
- **Team**: [Size and expertise]
- **Current Focus**: [What's being built this quarter]
- **Key Constraints**: [Performance targets, compliance, etc.]

## Architecture

Brief overview and link to detailed architecture document.

See: `docs/concepts/architecture.md`

## Where Things Live

- **New Feature Requests**: GitHub Issues with "feature" label
- **Bug Reports**: GitHub Issues with "bug" label
- **Decisions**: `docs/summaries/` (see handoff files)
- **Documentation**: `docs/` (organized by audience)
- **API Reference**: `docs/reference/api.md`

## Common Workflows

### Adding a New Feature

1. Use Requirements Analyst to clarify ambiguous specs
2. Use `/plan` command to create implementation plan
3. Work iteratively with `/test`, `/debug`, `/refactor`
4. Use System Architect if major architectural implications

### Investigating a Bug

1. Use `/debug` command to systematically investigate
2. Start with reproduction steps
3. Check logs using processing protocol
4. Implement fix and verify with `/test`

### Performance Work

1. Establish baseline with profiling
2. Use `/optimize` to identify bottleneck
3. Implement and measure improvement
4. Verify fix with `/test`

## Current Handoff

If switching sessions, read the latest: `docs/summaries/`

Most recent: [filename] - [brief description]
```

### 2. README.md

Project overview:

```markdown
# [Project Name]

[One-line description]

## Quick Start

1. [Clone/setup]
2. [Install dependencies]
3. [Run locally]
4. [Verify it works]

## Key Documentation

- **New Team Members**: Start with [docs/getting-started/setup.md](docs/getting-started/setup.md)
- **Creating Features**: Read [docs/guides/](docs/guides/) for how-tos
- **Architecture Questions**: See [docs/concepts/architecture.md](docs/concepts/architecture.md)
- **API Reference**: See [docs/reference/api.md](docs/reference/api.md)

## Common Tasks

### Running Tests
```bash
npm test
```

### Debugging
Use the `/debug` command in Claude Code and see `docs/guides/debugging.md`

### Performance Optimization
See `docs/guides/performance.md` or use `/optimize` command

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md)

## Architecture

High-level overview: [docs/concepts/architecture.md](docs/concepts/architecture.md)

System components, data flow, and design decisions.

## Status

`[Alpha | Beta | Stable | Maintenance]`

## License

[Your License]
```

### 3. ARCHITECTURE.md

System design document:

```markdown
# Architecture

High-level overview of system design, key components, and major decisions.

## System Overview

[Brief description of what the system does]

## Major Components

1. **[Component Name]**
   - **Purpose**: [What it does]
   - **Technology**: [Tech used]
   - **Key Files**: [Important files]

2. **[Component Name]**
   - **Purpose**: [What it does]
   - **Technology**: [Tech used]
   - **Key Files**: [Important files]

## Data Flow

[High-level data flow diagram or text description]

## Key Design Decisions

| Decision | Choice | Rationale | Trade-off |
|----------|--------|-----------|-----------|
| Authentication | JWT | Stateless, scales | Less granular revocation |
| Database | PostgreSQL | Relational data, reliability | More ops overhead |
| Cache | Redis | Performance, simple | Consistency complexity |

## Scalability Approach

How does the system scale?

- [Horizontal approach]
- [Vertical approach]
- [Known bottlenecks]

## Deployment Architecture

Development → Staging → Production

[Critical deployment details]

## Open Questions

- OPEN: [Question 1 not yet resolved]
- ASSUMED: [Assumption we're making]

## See Also

- API Reference: `docs/reference/api.md`
- Performance Guide: `docs/guides/performance.md`
- Deployment Guide: `docs/guides/deployment.md`
```

### 4. CONTRIBUTING.md

How to contribute:

```markdown
# Contributing

How to contribute to this project.

## Getting Started

1. Read `docs/getting-started/setup.md` to set up environment
2. Check [GitHub Issues](https://github.com/...) for tasks
3. Review `ARCHITECTURE.md` to understand the system

## Development Workflow

1. **Create a branch** from `main`: `git checkout -b feature/your-feature`
2. **Create implementation plan**: Use `/plan` command in Claude Code
3. **Implement the feature**: Use `/test`, `/debug`, `/refactor` commands
4. **Write/update documentation**: Use documentation playbook
5. **Request review**: Create pull request with checklist below
6. **Iterate**: Address feedback and re-test

## Before Submitting PR

- [ ] Code compiles/lints without errors
- [ ] All tests pass: `npm test`
- [ ] Added tests for new functionality
- [ ] Updated relevant documentation
- [ ] Described changes clearly in PR description
- [ ] No unnecessary dependencies added

## Code Review

- Expect feedback on architecture and approach
- Use Security Engineer agent if security implications
- All conversations should be respectful and constructive

## Reporting Issues

1. Check if issue already exists
2. Provide clear reproduction steps
3. Include environment details
4. Attach relevant logs or screenshots

## Questions?

- Check `docs/faq.md`
- Review existing issues and discussions
- Ask in pull request comments

Thank you for contributing!
```

## Customization Checklist

When starting a new project:

- [ ] Update `.claude/CLAUDE.md` with project-specific context
- [ ] Update `README.md` with project name and links
- [ ] Create `ARCHITECTURE.md` with system design
- [ ] Update `CONTRIBUTING.md` with project standards
- [ ] Create `docs/getting-started/setup.md` with setup steps
- [ ] Create `docs/guides/` with project-specific how-tos
- [ ] Create `docs/concepts/` with conceptual guides
- [ ] Add `.gitignore` entry: `docs/summaries/`

## Documentation Folders Explained

### getting-started/
For **new team members**:
- `setup.md` — How to get environment running
- `first-feature.md` — Making your first contribution
- `debugging.md` — How to debug using tools

### guides/
For **developers solving specific problems**:
- `authentication.md` — How to add auth
- `testing.md` — Testing patterns in this project
- `deployment.md` — How to deploy
- `performance.md` — Performance optimization

### reference/
For **knowing exactly how something works**:
- `api.md` — All API endpoints
- `configuration.md` — All configuration settings
- `cli-commands.md` — All CLI commands available

### concepts/
For **understanding the why**:
- `architecture.md` — System design and decisions
- `data-flow.md` — How data moves through system
- `state-management.md` — State management approach

## File Naming Conventions

- Use kebab-case for files: `my-feature.md`
- Keep files focused on one topic
- Link between related files
- Archive old versions instead of deleting

## Progressive Disclosure in Project Docs

1. **Project Overview** (README.md) — What is this? How do I get started?
2. **Setup Guide** (docs/getting-started/setup.md) — Exact steps to run
3. **Architecture** (ARCHITECTURE.md) — How does it work?
4. **Deep Dives** (docs/guides/\*, docs/concepts/\*) — Detailed information
5. **Reference** (docs/reference/\*) — Look-up details

Readers should be able to get started without reading everything.
