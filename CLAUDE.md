# CLAUDE.md

Your unified Claude workspace configuration for agents, commands, skills, and best practices.

## Session Start

**Ask yourself:** What is the project, what type of work, what is the target deliverable?

**State before working:**
1. What you understand the project state to be
2. What you plan to do this session
3. Any open questions or uncertainties

**Load handoffs:** If a previous session created a handoff in `docs/summaries/`, read it to understand context and avoid duplicate work.

## Available Resources

- **agents/** — Expert AI personas for complex multi-step work
- **commands/** — Quick workflows for routine development tasks
- **skills/** — Reusable patterns following proven methodologies
- **docs/context/** — Domain knowledge, protocols, and reference materials
- **docs/templates/** — Reusable formats for summaries, plans, decisions, and outputs

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
- Running tests and analyzing failures
- Explaining code or concepts
- Debugging systematically
- Optimizing performance
- Refactoring safely
- Code review workflows
- Creating pull requests
- Planning implementations

### Skills
Reusable patterns following proven methodologies. Load these when you need guidance on HOW to approach work.
- Testing using the Testing Trophy model
- Systematic debugging with root cause focus
- Performance optimization with measurement-first approach
- Safe code migration strategies
- Error handling best practices
- Refactoring with behavior verification

### Agents
Expert AI personas for complex, multi-step work requiring sustained focus.
- Architecture design at scale
- Technology research and evaluation
- Security and performance analysis
- Comprehensive documentation
- Requirements analysis and specification

## Common Workflows

### Code Review
1. Load skill `ce:systematic-debugging` for approach
2. Use command `/ce:review` for structured review
3. Use skill `ce:verification-before-completion` before approving
4. Write findings to disk

### Feature Implementation
1. Load skill `ce:writing-plans` to create implementation plan
2. Use command `/ce:plan` to structure the plan
3. Use skill `ce:condition-based-waiting` if async/flaky tests are involved
4. Load agent for architecture validation if system-level changes
5. Use command `/ce:execute` to drive implementation
6. Use skill `ce:verification-before-completion` before marking done

### Performance Optimization
1. Load skill `ce:optimizing-performance` (measure-first approach)
2. Use command `/ce:optimize` to identify bottlenecks
3. Verify gains justify complexity before accepting changes
4. Document trade-offs in decision record

### Debugging Failed Test
1. Load skill `ce:systematic-debugging` - understand root cause first
2. Load skill `ce:condition-based-waiting` if timing-related
3. Propose fix only after root cause is clear
4. Use skill `ce:verification-before-completion` to verify fix

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

## Error Recovery

If context degrades or you're unexpectedly compacted:
1. Write current work to `docs/summaries/recovery-[date].md`
2. Tell the user what may have been lost
3. Suggest a fresh session with the recovery file as handoff
