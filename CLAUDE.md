# CLAUDE.md

Your unified Claude workspace configuration for agents, commands, skills, and **subagent orchestration**.

## Session Start

**Ask yourself:** What is the project, what type of work, what is the target deliverable?

**State before working:**
1. What you understand the project state to be
2. What you plan to do this session
3. Any open questions or uncertainties

**Load handoffs:** If a previous session created a handoff in `docs/summaries/`, read it to understand context and avoid duplicate work.

## Available Resources

- **agents/** — Expert AI personas with preloaded skills (10 agents)
- **commands/** — Quick workflows and orchestration entry points (12 commands)
- **skills/** — Reusable patterns following proven methodologies (22 skills)
- **docs/workflows/** — Multi-agent orchestration patterns (RPI workflow)
- **docs/orchestration-guide.md** — How to build orchestrated workflows
- **presentation/** — CTO presentation materials on subagent orchestration

## Subagent Orchestration

This workspace supports the **Command → Agent → Skills** pattern for complex tasks.

### The Pattern

```
Command (haiku) → Task tool → Agent (sonnet/opus) → Preloaded Skills
```

- **Commands** orchestrate using cheap models
- **Agents** do heavy lifting with appropriate models
- **Skills** inject domain knowledge into agents

### Orchestrated Commands

| Command | Purpose |
|---------|---------|
| `/orchestrate-review <path>` | Code review with structured output |
| `/rpi:research <request.md>` | GO/NO-GO feasibility analysis |
| `/rpi:plan <feature-slug>` | Multi-perspective implementation plan |
| `/rpi:implement <feature-slug>` | Phased execution with validation |

### When to Use Orchestration

Use orchestrated workflows when:
- Task requires multiple domain perspectives
- Validation gates would prevent wasted effort
- Cost optimization matters (haiku routes, sonnet works)
- Structured, documented output is important

## Key Principles (From Research)

1. **Stay focused:** Do not mix unrelated project contexts in one session.

2. **Write decisions to disk:** After completing meaningful work, write a summary to `docs/summaries/` including:
   - Decisions with rationale
   - Exact numbers (not rounded)
   - File paths and references
   - Open questions marked as OPEN or ASSUMED

3. **Process documents efficiently:** For 4+ documents or any document > 2K words:
   - Read one document at a time
   - Extract key points to a summary file
   - Release from active memory before reading the next
   - Use the Document Processing Protocol (docs/context/processing-protocol.md)

4. **Do not silently resolve questions:** If something is unclear, mark it explicitly as OPEN.

5. **Sub-agents must be structured:** Use output contracts from templates to ensure sub-agent returns are structured, not free-form prose.

6. **Prefer patterns over rules:** Skills teach proven patterns you can apply; commands are quick shortcuts for routine tasks.

## When to Use What

### Commands
Quick workflows for everyday tasks. These are shortcuts.
- `/test` — Run tests and analyze failures
- `/debug` — Systematic debugging
- `/plan` — Implementation planning
- `/refactor` — Safe refactoring
- `/orchestrate-review` — Orchestrated code review

### Orchestrated Workflows (RPI)
For complex features requiring validation and multiple perspectives:
- `/rpi:research` — Research phase with GO/NO-GO
- `/rpi:plan` — Multi-agent planning (PM, UX, Engineering)
- `/rpi:implement` — Phased execution with validation

### Skills
Reusable patterns following proven methodologies. Load these when you need guidance on HOW to approach work.
- Testing using the Testing Trophy model
- Systematic debugging with root cause focus
- Performance optimization with measurement-first approach
- Safe code migration strategies
- Error handling best practices
- Refactoring with behavior verification

### Agents
Expert AI personas invoked via Task tool. Each agent has preloaded skills.
- **system-architect** — Architecture design (opus, skills: architecting-systems, writing-plans, mermaid)
- **backend-architect** — APIs, databases (sonnet, skills: architecting-systems, managing-databases)
- **frontend-architect** — UI, accessibility (sonnet, skills: design, optimizing-performance)
- **tech-stack-researcher** — Technology evaluation (sonnet, skills: writing-plans, architecting-systems)
- **requirements-analyst** — Requirements clarity (sonnet, skills: writing-plans, documenting-systems)
- **performance-engineer** — Performance optimization (sonnet, skills: optimizing-performance, debugging)
- **security-engineer** — Security audits (sonnet, skills: debugging, handling-errors)
- **technical-writer** — Documentation (sonnet, skills: documenting-systems, writer)
- **deep-research-agent** — Research synthesis (opus, skills: writing-plans, documenting-systems)
- **code-review-agent** — Code quality review (sonnet, skills: debugging, refactoring, verification)

## Common Workflows

### Orchestrated Code Review
```
/orchestrate-review src/api/
```
Invokes code-review-agent via Task tool with preloaded debugging and verification skills.

### RPI Feature Development
```
# 1. Create request
rpi/my-feature/REQUEST.md

# 2. Research (GO/NO-GO)
/rpi:research rpi/my-feature/REQUEST.md

# 3. Plan (if GO)
/rpi:plan my-feature

# 4. Implement
/rpi:implement my-feature
```

### Quick Code Review (Non-orchestrated)
1. Load skill `systematic-debugging` for approach
2. Use command `/debug` for issue analysis
3. Use skill `verification-before-completion` before approving
4. Write findings to disk

### Feature Implementation (Quick)
1. Use command `/plan` to structure the plan
2. Load skill `writing-plans` for methodology
3. Use skill `verification-before-completion` before marking done

### Performance Optimization
1. Load skill `optimizing-performance` (measure-first approach)
2. Use command `/optimize` to identify bottlenecks
3. Verify gains justify complexity before accepting changes
4. Document trade-offs in decision record

## Before Delivering Output

Verify:
- ✓ Exact numbers preserved (not rounded)
- ✓ Open questions marked OPEN or ASSUMED
- ✓ Output matches what was requested (not assumed)
- ✓ Claims backed by specific data
- ✓ Output consistent with stored decisions
- ✓ Summary written to disk for this session's work

## Token Efficiency

- Load skills and agents on demand only (progressive disclosure)
- Keep session state in `docs/summaries/` — handoff references, not full content
- Use document processing protocol for large files
- Read summaries, not original documents
- Release documents from context once summarized
- Use haiku for orchestration, sonnet for work, opus for strategy

## Error Recovery

If context degrades or you're unexpectedly compacted:
1. Write current work to `docs/summaries/recovery-[date].md`
2. Tell the user what may have been lost
3. Suggest a fresh session with the recovery file as handoff

## Learn More

- **docs/orchestration-guide.md** — Complete orchestration guide
- **docs/workflows/rpi-workflow.md** — RPI workflow documentation
- **examples/orchestration/** — Code review orchestration example
- **presentation/** — CTO presentation materials
