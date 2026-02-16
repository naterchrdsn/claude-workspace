# Sources & Attribution

This workspace is a curated collection of best practices, agents, commands, and documentation patterns from three excellent source repositories.

## Source Repositories

### 1. claude-context-os
**GitHub:** [Arkya-AI/claude-context-os](https://github.com/Arkya-AI/claude-context-os)  
**License:** MIT

**What We Curated:**
- Research-backed system prompt design principles
- Context management and document processing protocols
- Token efficiency strategies
- Session handoff patterns

**Key Contributions:**
- CLAUDE.md structure and session management approach
- Document Processing Protocol (docs/context/processing-protocol.md)
- Emphasis on research-backed prompt design
- v4 improvements (reduced complexity, removed noise)

**Key Insights from claude-context-os:**
- LLMs track 5-10 rules effectively; beyond that performance degrades
- Explanatory prose interferes with instruction compliance
- Emphatic language ("CRITICAL", "NEVER") causes overcorrection
- Progressive disclosure prevents context loss
- Structured templates prevent summarization failures

---

### 2. claude-essentials  
**GitHub:** [rileyhilliard/claude-essentials](https://github.com/rileyhilliard/claude-essentials)  
**License:** MIT

**What We Curated:**
- Command and skill architecture
- Clean separation of concerns (commands vs. skills vs. agents)
- Practical workflow commands
- Plugin structure and naming conventions

**Key Contributions:**
- Command framework (test, debug, plan, refactor, explain, optimize)
- Skill concept and progressive disclosure approach
- Clear namespace conventions (ce:)
- Plugin metadata and configuration patterns
- Session hooks and automation

**Key Insights from claude-essentials:**
- Commands are routine tasks; skills are patterns; agents are experts
- Namespace conventions keep things organized
- Progressive disclosure (metadata → body → references)
- Hooks enable automation on session start
- Clear boundaries and integration patterns

---

### 3. edmunds-claude-code
**GitHub:** [edmund-io/edmunds-claude-code](https://github.com/edmund-io/edmunds-claude-code)  
**License:** MIT

**What We Curated:**
- Specialized agent definitions
- Domain-specific expertise patterns
- Agent triggers and behavioral mindsets
- Complete agent implementations

**Key Contributions:**
- System Architect agent
- Tech Stack Researcher agent
- Requirements Analyst agent
- Security Engineer agent
- Pattern for high-quality agent design

**Key Insights from edmunds-claude-code:**
- Agents need clear triggers and use cases
- Behavioral mindset shapes outputs
- Boundaries clarify what agents will/won't do
- Context-aware agents outperform generic ones
- Research methodology should be explicit

---

## What We Built

This `claude-workspace` combines the strengths:

| Component | Source | Why This One |
|-----------|--------|-------------|
| **CLAUDE.md** | context-os + essentials | Research-backed, clean structure |
| **Agents** | edmunds-claude-code | Complete implementations, clear triggers |
| **Commands** | claude-essentials | Practical workflows |
| **Documentation Playbook** | context-os | Best practices + structures |
| **Processing Protocol** | context-os | Proven method for large documents |
| **Example Project Layout** | essentials (adapted) | Ready-to-use structure |

## License

This workspace is MIT-licensed.

**Source code and patterns** are used under the original MIT licenses.

**Documentation** created for this workspace is MIT-licensed.

## How to Use These Resources

### If You Want Research-Backed Prompt Design
→ Study `CLAUDE.md` and `docs/context/processing-protocol.md`

### If You Want Production-Ready Commands
→ Use the commands in `/commands/` with the patterns from `docs/command-reference.md`

### If You Want Expert Agents
→ Reference agents in `/agents/` and patterns in `docs/agent-reference.md`

### If You Want to Document Well
→ Read `docs/documentation-playbook.md` and use `examples/example-project-structure.md`

## Contributing Back

If you improve this workspace:
1. Keep attribution to original sources
2. Document what you changed and why
3. Consider contributing back to upstream repos

## Further Reading

- **claude-context-os**: Deep dive into research-backed system prompts
- **claude-essentials**: Complete plugin architecture and patterns
- **edmunds-claude-code**: Domain-specific agent design

## Acknowledgments

Credit to:
- **Arkya-AI** for research-backed prompt design and context management
- **Riley Hilliard** for clean plugin architecture and practical commands
- **Edmund Edmunds** for specialized agent design patterns

This resource stands on their excellent work.
