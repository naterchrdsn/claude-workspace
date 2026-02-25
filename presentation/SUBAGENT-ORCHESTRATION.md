# Subagent Orchestration with Claude Code

**A Technical Leadership Guide**

---

## Executive Summary

Subagent orchestration enables Claude Code to **decompose complex tasks** across specialized AI agents, each with domain expertise and focused capabilities. This approach delivers:

- **10x cost reduction** through intelligent model routing
- **Consistent quality** via validation gates and structured workflows
- **Scalable AI adoption** with reusable, composable components
- **Risk mitigation** through phased execution with checkpoints

---

## The Problem We Solve

### Without Orchestration
```
User Request
    ↓
Single Claude Instance (expensive model)
    ↓
Attempts everything at once
    ↓
Inconsistent quality, high cost, no validation
```

### With Orchestration
```
User Request
    ↓
Lightweight Orchestrator (cheap model)
    ↓
Routes to specialized agents (right model for task)
    ↓
Validation gates between phases
    ↓
Consistent, validated, cost-effective output
```

---

## Core Architecture

### Three-Layer Pattern

```
┌────────────────────────────────────────────────┐
│  COMMANDS (Entry Points)                        │
│  • Lightweight orchestration                    │
│  • User-facing interface                        │
│  • Model: haiku ($0.25/M tokens)               │
└────────────────────────────────────────────────┘
                      │
                      │ Task Tool (delegation)
                      ▼
┌────────────────────────────────────────────────┐
│  AGENTS (Domain Experts)                        │
│  • Specialized capabilities                     │
│  • Domain-specific tools                        │
│  • Model: sonnet/opus ($3-15/M tokens)         │
└────────────────────────────────────────────────┘
                      │
                      │ Preloaded Knowledge
                      ▼
┌────────────────────────────────────────────────┐
│  SKILLS (Domain Knowledge)                      │
│  • Methodologies and patterns                   │
│  • Best practices                               │
│  • Reference materials                          │
└────────────────────────────────────────────────┘
```

### Cost Comparison

| Approach | Model Used | Est. Cost per Task |
|----------|------------|-------------------|
| No orchestration | opus for everything | $15/M tokens |
| Basic orchestration | sonnet for everything | $3/M tokens |
| Smart orchestration | haiku routing + sonnet work | ~$1/M tokens |

**Result:** 10-15x cost reduction with equal or better quality.

---

## What We Built

### Components

| Component | Count | Purpose |
|-----------|-------|---------|
| **Agents** | 10 | Domain experts (architecture, security, performance, etc.) |
| **Commands** | 12 | Entry points (review, plan, implement, research, etc.) |
| **Skills** | 22 | Reusable knowledge patterns |
| **Workflows** | 2 | Orchestrated multi-agent pipelines |

### Key Workflows

#### 1. Code Review Orchestration
```
/orchestrate-review src/api/
    ↓
code-review-agent
    - Preloaded: debugging, refactoring, verification skills
    - Tools: Read, Glob, Grep, Write
    ↓
Structured review report
```

#### 2. RPI Workflow (Research → Plan → Implement)
```
/rpi:research → GO/NO-GO decision
    ↓ (if GO)
/rpi:plan → Multi-perspective planning (PM, UX, Engineering)
    ↓
/rpi:implement → Phased execution with validation gates
```

---

## RPI Workflow Deep Dive

### The Value Proposition

**Before RPI:**
- Features start without validation
- Feasibility discovered mid-implementation
- Wasted effort on non-viable features
- Inconsistent documentation

**After RPI:**
- Research gate prevents waste
- Multi-perspective planning
- Phased implementation with checkpoints
- Full documentation as byproduct

### Flow Diagram

```
┌─────────────────────────────────────────────────┐
│  REQUEST.md                                      │
│  "Add OAuth2 with Google/GitHub"                │
└─────────────────────────────────────────────────┘
                      │
                      ▼
┌─────────────────────────────────────────────────┐
│  PHASE 1: RESEARCH                              │
│  /rpi:research                                  │
│                                                 │
│  Agents:                                        │
│  • requirements-analyst                         │
│  • tech-stack-researcher                        │
│  • system-architect                             │
│                                                 │
│  Output: RESEARCH.md                            │
│  Verdict: GO / NO-GO / CONDITIONAL              │
└─────────────────────────────────────────────────┘
                      │
              ┌───────┴───────┐
              │  GO?          │
              └───────┬───────┘
       NO ◄───────────┴───────────► YES
       │                            │
       ▼                            ▼
  Document                 ┌─────────────────────┐
  & Archive                │  PHASE 2: PLAN      │
                           │  /rpi:plan          │
                           │                     │
                           │  Outputs:           │
                           │  • pm.md (Product)  │
                           │  • ux.md (Design)   │
                           │  • eng.md (Tech)    │
                           │  • PLAN.md          │
                           └─────────────────────┘
                                    │
                                    ▼
                           ┌─────────────────────┐
                           │  PHASE 3: IMPLEMENT │
                           │  /rpi:implement     │
                           │                     │
                           │  • Execute phases   │
                           │  • Validate each    │
                           │  • Document progress│
                           │  • Commit often     │
                           └─────────────────────┘
```

### Agents by Phase

| Phase | Agent | Model | Role |
|-------|-------|-------|------|
| Research | requirements-analyst | sonnet | Parse requirements |
| Research | tech-stack-researcher | sonnet | Assess feasibility |
| Research | system-architect | opus | Strategic alignment |
| Plan | requirements-analyst | sonnet | User stories |
| Plan | frontend-architect | sonnet | UX design |
| Plan | backend-architect | sonnet | Technical spec |
| Implement | code-review-agent | sonnet | Validation |
| Implement | technical-writer | sonnet | Documentation |

---

## Demo Script

### Setup
```bash
# Ensure claude-workspace is in project
ls .claude/  # Should show agents/, commands/, skills/
```

### Demo 1: Simple Orchestration (2 min)
```bash
# Show the command
cat .claude/commands/orchestrate-review.md

# Run it
/orchestrate-review src/api/auth/

# Show agent being invoked via Task tool
# Show structured output in docs/reviews/
```

### Demo 2: RPI Workflow (5 min)
```bash
# Create feature request
mkdir -p rpi/demo-feature
cat > rpi/demo-feature/REQUEST.md << 'EOF'
# Feature: User Notifications
Add in-app notification system with email fallback.
EOF

# Phase 1: Research
/rpi:research rpi/demo-feature/REQUEST.md
# Show GO/NO-GO output

# Phase 2: Plan (if GO)
/rpi:plan demo-feature
# Show generated pm.md, ux.md, eng.md, PLAN.md

# Phase 3: Implement (briefly)
/rpi:implement demo-feature
# Show phased execution and validation
```

### Key Points to Highlight
1. **Cost efficiency**: haiku orchestrates, sonnet works
2. **Validation gates**: Research prevents wasted effort
3. **Multi-perspective**: PM, UX, Engineering views
4. **Documentation**: Generated automatically
5. **Reusability**: Same agents serve multiple workflows

---

## Team Adoption Path

### Week 1: Foundation
- [ ] Copy claude-workspace to team projects
- [ ] Team reviews orchestration-guide.md
- [ ] Each team member tries /orchestrate-review

### Week 2: Simple Orchestration
- [ ] Use /orchestrate-review for all PRs
- [ ] Create team-specific agents if needed
- [ ] Document patterns that emerge

### Week 3: RPI Adoption
- [ ] Start new features with /rpi:research
- [ ] Use full RPI flow for complex features
- [ ] Customize REQUEST.md template for team

### Week 4: Optimization
- [ ] Review cost metrics
- [ ] Identify workflow improvements
- [ ] Create additional commands/agents as needed

---

## Metrics to Track

### Cost Efficiency
- Tokens used per task type
- Model distribution (haiku/sonnet/opus)
- Cost per completed workflow

### Quality
- Validation pass rate
- Issues caught in research phase
- Rework rate after implementation

### Adoption
- Commands used per developer per week
- RPI completion rate
- Agent utilization by type

---

## Key Takeaways

1. **Orchestration = intelligent routing** - Use the right model for each task

2. **Agents = specialized experts** - Domain expertise with focused tools

3. **Skills = injectable knowledge** - Reusable patterns across agents

4. **Validation gates = risk mitigation** - Catch problems early

5. **RPI = systematic development** - Research before planning, plan before implementing

---

## Resources

- `docs/orchestration-guide.md` - Complete technical guide
- `docs/workflows/rpi-workflow.md` - RPI workflow documentation
- `examples/orchestration/README.md` - Code review example
- `examples/rpi-template/` - Ready-to-copy RPI template

---

## Q&A Preparation

**Q: How does this compare to just using Claude directly?**
A: Direct usage works for simple tasks. Orchestration shines for complex, multi-step work where you need validation, multiple perspectives, or cost optimization.

**Q: What's the learning curve?**
A: Commands are immediately usable (/orchestrate-review). Full RPI workflow takes about a week to internalize.

**Q: Can we customize agents?**
A: Yes. Agent definitions are markdown files. Add tools, skills, or modify behavior as needed.

**Q: How do we handle failures?**
A: Validation gates catch failures between phases. Each phase documents progress, so you can resume from the last successful point.

**Q: What about sensitive code?**
A: Agents run locally with configurable tool access. No code leaves your environment unless explicitly configured.
