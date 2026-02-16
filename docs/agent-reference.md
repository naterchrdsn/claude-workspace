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

### Backend Architect

**Purpose:** Design reliable backend systems with focus on data integrity, security, and fault tolerance

**Use When:**
- Designing server-side APIs or data services
- Evaluating database schema and query patterns
- Planning reliability, security, and observability
- Handling backend scalability constraints

**Delivers:**
- API specifications with security considerations
- Database schemas with indexing and constraints
- Reliability patterns and observability guidance
- Performance and scaling recommendations

**Example:** "Design a fault-tolerant API and database schema for our billing system"

---

### Frontend Architect

**Purpose:** Create accessible, performant user interfaces with strong UX foundations

**Use When:**
- Building or redesigning UI component systems
- Ensuring WCAG compliance and accessibility
- Improving Core Web Vitals and frontend performance
- Establishing responsive design patterns

**Delivers:**
- Accessible component patterns
- Performance improvement plans
- Responsive layout guidance
- UX and interaction design notes

**Example:** "Design an accessible dashboard UI with strong performance metrics"

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

### Performance Engineer

**Purpose:** Optimize system performance through measurement-driven analysis and bottleneck elimination

**Use When:**
- Investigating slow endpoints or UI responsiveness
- Establishing baselines and performance budgets
- Prioritizing high-impact optimization work
- Validating before/after performance changes

**Delivers:**
- Performance audits with bottlenecks
- Before/after benchmarks
- Optimization recommendations
- Performance regression guidance

**Example:** "Profile checkout flow and propose optimizations with measurable gains"

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

### Technical Writer

**Purpose:** Create clear, comprehensive technical documentation tailored to specific audiences

**Use When:**
- Writing API documentation or technical specs
- Creating user guides and tutorials
- Improving documentation structure and clarity
- Ensuring documentation accessibility and usability

**Delivers:**
- API references and how-to guides
- Structured documentation outlines
- Troubleshooting and installation docs
- Accessibility-focused documentation

**Example:** "Create a developer-friendly API guide with examples"

---

### Deep Research Agent

**Purpose:** Conduct comprehensive research with adaptive strategies and evidence-based synthesis

**Use When:**
- Investigating complex topics with multiple sources
- Producing research-backed recommendations
- Synthesizing findings across domains
- Needing citations and confidence levels

**Delivers:**
- Research plans and methodology
- Evidence-backed findings
- Source lists and citations
- Synthesis with confidence statements

**Example:** "Research the best approaches to realtime data sync and summarize trade-offs"

---

## Agent vs. Command Decision Tree

```
Does it involve:
├─ System-level architecture? → System Architect
├─ Backend design or data integrity? → Backend Architect
├─ Frontend UX or accessibility? → Frontend Architect
├─ Planning new technology approach? → Tech Stack Researcher
├─ Clarifying vague requirements? → Requirements Analyst
├─ Performance bottlenecks? → Performance Engineer
├─ Security assessment? → Security Engineer
├─ Documentation quality? → Technical Writer
├─ Deep research or synthesis? → Deep Research Agent
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
   - Use System Architect for architectural concerns
   - Use Backend Architect for server-side risk review
   - Use Frontend Architect for UX and accessibility review
   - Use Security Engineer for security implications
   - Use Technical Writer for doc quality and clarity

4. **Optimization Phase**
   - Use Performance Engineer for measurement-driven optimization
   - Use `/optimize` command for focused performance work
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
- [backend-architect.md](../agents/backend-architect.md)
- [frontend-architect.md](../agents/frontend-architect.md)
- [tech-stack-researcher.md](../agents/tech-stack-researcher.md)
- [requirements-analyst.md](../agents/requirements-analyst.md)
- [performance-engineer.md](../agents/performance-engineer.md)
- [security-engineer.md](../agents/security-engineer.md)
- [technical-writer.md](../agents/technical-writer.md)
- [deep-research-agent.md](../agents/deep-research-agent.md)
