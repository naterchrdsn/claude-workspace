# File Structure & Navigation Map

## Directory Layout

```
claude-workspace/
│
├── README.md                              ← Start here (main overview)
├── QUICK-START.md                         ← Get running in 5 minutes
├── CLAUDE.md                              ← Configuration & principles
├── SOURCES.md                             ← Attribution & sources
├── LICENSE                                ← MIT License
│
├── agents/                                ← Expert AI personas
│   ├── system-architect.md                ← Design scalable systems
│   ├── tech-stack-researcher.md           ← Technology choices
│   ├── requirements-analyst.md            ← Clarify specifications
│   └── security-engineer.md               ← Security assessment
│
├── commands/                              ← Quick development workflows
│   ├── test.md                            ← Run & analyze tests
│   ├── debug.md                           ← Systematic debugging
│   ├── plan.md                            ← Implementation planning
│   ├── refactor.md                        ← Safe refactoring
│   ├── explain.md                         ← Code/concept explanation
│   └── optimize.md                        ← Performance optimization
│
├── docs/
│   ├── INDEX.md                           ← Documentation navigation
│   ├── command-reference.md               ← Quick command lookup
│   ├── agent-reference.md                 ← Quick agent lookup
│   ├── documentation-playbook.md          ← How to write good docs
│   │
│   ├── context/
│   │   └── processing-protocol.md         ← Handle large documents
│   │
│   ├── templates/                         ← Reusable doc templates
│   │   (for your own projects)
│   │
│   └── examples/
│       (example outputs & patterns)
│
├── examples/
│   └── example-project-structure.md       ← Template for new projects
│
└── skills/                                ← (Reserved for future)
```

## Quick Navigation

### Finding What You Need

| Need | Go To |
|------|-------|
| Getting started | [QUICK-START.md](QUICK-START.md) |
| Project overview | [README.md](README.md) |
| How to use commands | [docs/command-reference.md](docs/command-reference.md) |
| How to use agents | [docs/agent-reference.md](docs/agent-reference.md) |
| Documentation best practices | [docs/documentation-playbook.md](docs/documentation-playbook.md) |
| Handling multiple documents | [docs/context/processing-protocol.md](docs/context/processing-protocol.md) |
| New project template | [examples/example-project-structure.md](examples/example-project-structure.md) |
| Understanding the sources | [SOURCES.md](SOURCES.md) |

### By Audience

**First Time Using?**
1. Read [QUICK-START.md](QUICK-START.md)
2. Read [README.md](README.md)
3. Try a command: `/test` or `/plan "feature"`

**Setting Up a New Project?**
1. Read [examples/example-project-structure.md](examples/example-project-structure.md)
2. Copy the directory structure
3. Customize `.claude/CLAUDE.md` with your project context

**Want to Document Your Project?**
1. Read [docs/documentation-playbook.md](docs/documentation-playbook.md)
2. Follow the templates for your document type
3. Use [docs/INDEX.md](docs/INDEX.md) for organization patterns

**Need to Review Lots of Documents?**
1. Read [docs/context/processing-protocol.md](docs/context/processing-protocol.md)
2. Follow the 5-step process
3. Summarize to disk as you go

**Looking for a Specific Command or Agent?**
1. Check [docs/command-reference.md](docs/command-reference.md) for commands
2. Check [docs/agent-reference.md](docs/agent-reference.md) for agents
3. Read the specific `.md` file in `/commands/` or `/agents/`

### By Task Type

| Task | Commands | Agents | Reference |
|------|----------|--------|-----------|
| Building features | `/plan`, `/debug` | Requirements Analyst | - |
| Technology decisions | - | Tech Stack Researcher | - |
| System design | - | System Architect | ARCHITECTURE.md |
| Testing/QA | `/test`, `/debug` | - | - |
| Refactoring | `/refactor`, `/test` | - | - |
| Performance | `/optimize` | - | - |
| Security | - | Security Engineer | - |
| Documentation | - | - | Playbook |
| Explaining code | `/explain` | - | - |

## File Purposes Explained

### Root Level

**README.md** — Everything you need to know about the workspace

**QUICK-START.md** — Get running in 5 minutes (copy, customize, go)

**CLAUDE.md** — The workspace configuration and operating principles

**SOURCES.md** — Attribution and sources (where ideas came from)

**LICENSE** — MIT License (you can use and modify freely)

### agents/ Directory

Each file is a specialized AI persona with:
- **name**: What it's called
- **description**: What it does
- **When to use**: Specific triggers and scenarios
- **Behavioral mindset**: How it approaches work
- **Key actions**: What it actually does
- **Outputs**: What you get back
- **Boundaries**: What it will/won't do

**4 Agents Included:**
1. **system-architect.md** — Large-scale system design
2. **tech-stack-researcher.md** — Technology planning
3. **requirements-analyst.md** — Requirements gathering
4. **security-engineer.md** — Security audits

### commands/ Directory

Each file is a quick workflow with:
- **Description**: What it does
- **When to use**: When you'd invoke it
- **Framework/Steps**: How it works
- **Examples**: Real usage examples
- **Usage patterns**: Integration with other commands

**6 Commands Included:**
1. **test.md** — Run tests, analyze failures
2. **debug.md** — Systematic debugging process
3. **plan.md** — Create implementation plans
4. **refactor.md** — Safe code refactoring
5. **explain.md** — Explain code or concepts
6. **optimize.md** — Performance optimization

### docs/ Directory

**INDEX.md** — Navigation for all documentation

**command-reference.md** — Quick lookup table for all commands

**agent-reference.md** — Quick lookup table for all agents + decision tree

**documentation-playbook.md** — How to write documentation:
- Progressive disclosure structure
- Template for each document type
- Writing checklist
- File organization examples

**context/processing-protocol.md** — Handle large documents:
- When to use it
- 5-step process
- Source summary template
- Error prevention

**examples/** — Example outputs and patterns for your own work

**templates/** — (For your project) Store your own templates here

## How Files Relate

```
                    README.md
                        ↓
            ___________/|\___________
           /          / | \          \
          ↓          ↓  ↓  ↓          ↓
      Commands    Agents Docs    CLAUDE.md
         /\         /\    /\          |
        /  \       /  \  /  \         |
       ↓    ↓     ↓    ↓↓    ↓        ↓
     test debug plan... architect... reference... (Project Context)
                                ↓
                            Example Structure
```

## Tips for Navigation

1. **Bookmarks** — Bookmark [docs/INDEX.md](docs/INDEX.md) for easy navigation

2. **Quick Links** — Command reference and agent reference are your goto

3. **Follow Links** — Each document links to related content

4. **Search** — Use your editor's search (Ctrl+Shift+F) to find topics

5. **Ask Claude** — Claude can help interpret any file or concept

## Integration Points

### In Your Project

Place files like this:

```
my-project/
├── .claude/
│   └── CLAUDE.md          ← Your project config
├── docs/
│   ├── getting-started/   ← For new team members
│   ├── guides/            ← How-to docs
│   ├── concepts/          ← Understanding docs
│   ├── reference/         ← Lookup docs
│   └── summaries/         ← Claude session state
└── [... rest of project]
```

### In Claude.ai/Code

Commands and agents become available when:
1. Files are in your workspace
2. CLAUDE.md is configured properly
3. You invoke them with `/command` or `@agent`

## Project Statistics

- **Total files**: 20+
- **Agents**: 4
- **Commands**: 6
- **Documentation files**: 8
- **Example templates**: 1
- **Total size**: ~500KB (all readable text)
- **Average file size**: 2-3KB (scannable)

## Success Criteria

You've successfully integrated if:
✅ You can run `/test` or `/debug` commands
✅ You understand the difference between commands and agents
✅ You can find documentation easily
✅ You've customized CLAUDE.md for your project
✅ Your team knows where to look for answers

---

**This workspace is designed to be easy to navigate and understand.** Start with QUICK-START.md and let the links guide you!
