# Agent Reference

Specialized AI personas for complex work.

## When to Use Agents

Agents are for **complex, multi-step work** that requires sustained focus and expertise.

Commands are for quick **routine tasks** (test, refactor, debug).

Agents are for **strategic decisions** (architecture, requirements, security).

## Available Agents

### System Architect

**Purpose:** Design scalable, maintainable system architectures

**Use When:**
- Designing system architecture from scratch
- Evaluating architectural patterns
- Planning for 10x growth
- Managing dependencies and component boundaries
- Making long-term technical strategy decisions

**Delivers:**
- Architecture diagrams
- Design documentation with trade-offs
- Scalability plans
- Migration strategies

**Example:** "Design the architecture for a real-time notification system that needs to support 1M concurrent users"

---

### Tech Stack Researcher

**Purpose:** Research technology choices and architecture recommendations

**Use When:**
- Planning new features and need technology guidance
- Comparing technology options (WebSockets vs SSE)
- Beginning feature development and need "best way?"
- Evaluating ecosystem fit
- Designing feature architecture

**Delivers:**
- Feature analysis
- Recommended approach with specific technologies
- Alternative options with pros/cons
- Implementation considerations
- Concrete next steps

**Example:** "I'm adding real-time chat to our app. What's the best approach?"

---

### Requirements Analyst

**Purpose:** Transform ambiguous ideas into concrete specifications

**Use When:**
- Have a vague idea that needs clarification
- Creating PRDs from conceptual ideas
- Developing user stories and acceptance criteria
- Defining project scope
- Facilitating stakeholder alignment

**Delivers:**
- Product Requirements Documents
- User stories with acceptance criteria
- Project specifications and scope
- Success metrics and frameworks
- Requirements validation reports

**Example:** "We need better user onboarding but I'm not sure what that means. Help me figure it out."

---

### Security Engineer

**Purpose:** Identify vulnerabilities and ensure compliance

**Use When:**
- Security vulnerability assessment
- Code audit and compliance verification
- Threat modeling and attack vector analysis
- Implementing authentication/authorization
- Reviewing data protection approaches

**Delivers:**
- Security audit reports
- Threat models
- Compliance reports
- Vulnerability assessments
- Secure coding guidelines

**Example:** "Review our API security and identify vulnerabilities"

---

## Agent vs. Command Decision Tree

```
Does it involve:
├─ Designing system architecture? → System Architect
├─ Planning new technology approach? → Tech Stack Researcher
├─ Clarifying vague requirements? → Requirements Analyst
├─ Security assessment? → Security Engineer
└─ Quick routine task?
   ├─ Run tests → /test command
   ├─ Debug a bug → /debug command
   ├─ Plan implementation → /plan command
   ├─ Refactor code → /refactor command
   ├─ Learn a concept → /explain command
   └─ Improve performance → /optimize command
```

## Usage Pattern: Complete Feature Workflow

1. **Planning Phase**
   - Use Requirements Analyst for unclear specs
   - Use Tech Stack Researcher to decide architecture

2. **Implementation Phase**
   - Use `/plan` command for detailed implementation plan
   - Use `/test` and `/debug` for routine work

3. **Review Phase**
   - Use System Architect if major architectural concerns
   - Use Security Engineer if security implications

4. **Optimization Phase**
   - Use `/optimize` command for performance
   - Use `/refactor` command for code quality

## How to Invoke Agents

**In Claude Code:**
- Reference by name: `@system-architect`, `@requirements-analyst`, etc.
- Or describe the work and ask for recommendation

**Key Context:**
- Provide project background
- Share relevant code or documents
- Be specific about the challenge
- Mention constraints (timeline, budget, team expertise)

## Agent Details

See:
- [system-architect.md](../agents/system-architect.md)
- [tech-stack-researcher.md](../agents/tech-stack-researcher.md)
- [requirements-analyst.md](../agents/requirements-analyst.md)
- [security-engineer.md](../agents/security-engineer.md)
