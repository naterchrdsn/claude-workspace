# Documentation Playbook

Best practices for writing documentation that teams actually use.

## The Problem

Most documentation becomes outdated, is too long, or assumes too much context. This playbook helps you write documentation that stays relevant and is actually readable.

## Core Principles

### 1. Progressive Disclosure

Structure documentation so readers get what they need at each level:

**Level 1: Name + One-Line Summary**
- File/topic name
- What it does (1 sentence)
- When to use it

Example: "Performance Optimization - Find bottlenecks and improve code speed while maintaining readability"

**Level 2: When You Need It**
- Specific scenarios where this applies
- What problem does it solve?
- What won't this help with?

**Level 3: The How**
- Step-by-step instructions
- Code examples
- Common patterns

**Level 4: The Deep Dive**
- Why does this work?
- Edge cases
- Alternative approaches
- Trade-offs

### Key: Don't force readers through all 4 levels to get started.

### 2. Targeted Audience

Know who you're writing for:

- **Getting Started**: New team members
- **How-To Guide**: Developers solving a specific problem
- **Reference**: Developers who know what they want but forgot details
- **Explanation**: Engineers wanting to understand the why

Each type has different structure and depth.

### 3. Show, Don't Tell

**Bad:** "Authentication is important and must be implemented correctly."
**Good:** "Here's how to add JWT authentication with these specific trade-offs..."

**Bad:** "Use the testing framework to write tests."
**Good:** "Write a test by creating a file `test.ts` with this structure: [example]"

### 4. One Topic, One File

Don't mix concepts:
- ✗ "Authentication and Authorization" (unless they're inseparable)
- ✓ "JWT Authentication" and "Role-Based Access Control"

This keeps files small and searchable.

### 5. Examples Before Theory

- Start with a concrete example
- Then explain why it works
- Then discuss alternatives

Examples make docs 10x more useful.

## Structure Template: How-To Guide

```markdown
# [Action] [Thing]

One-line summary of what this guide teaches.

## When to Use This

- Scenario 1
- Scenario 2
- Scenario 3 (when NOT to use)

## Before You Start

Prerequisites:
- [ ] Requirement 1
- [ ] Requirement 2

## Step-by-Step

### Step 1: [Specific Action]

Description and context.

```bash
specific command or code
```

### Step 2: [Next Specific Action]

### Step 3: [Final Step]

## Verification

How to know it worked:

```bash
verification command or check
```

## Common Issues

**Problem**: Description
**Solution**: How to fix

## What's Next

Related guides or next steps.
```

## Structure Template: Reference

```markdown
# [Thing]

One-sentence definition.

## Overview

What is this? When would you use it? (2-3 sentences)

## Syntax/Format

```
exact syntax here
```

## Parameters

| Name | Type | Required | Description |
|------|------|----------|-------------|
| param1 | string | Yes | Does what |
| param2 | bool | No | Does what |

## Examples

### Basic Usage
```
example code
```

### Advanced Pattern
```
more complex example
```

## Common Mistakes

- Mistake 1: Why it's wrong, how to fix
- Mistake 2: Why it's wrong, how to fix

## Related

Link to related concepts
```

## Structure Template: Explanation

```markdown
# [Concept]

One-line definition.

## What Is It?

Explain in plain language (no jargon). Real example from your domain.

## Why Does It Matter?

When would you need this? What problems does it solve?

## How Does It Work?

Explain the mechanism:
1. Part A does X
2. Part B does Y because X
3. Result: Z

Include a simple diagram if helpful.

## Example

Real code example showing it in action.

## Common Misconceptions

- "People think X" — Actually it's Y because...
- "People think A" — Actually it's B because...

## Trade-offs

- Benefit: Why this approach
- Cost: What you give up
- Alternative: When you'd choose differently

## Related Concepts

Links to related ideas
```

## Writing Checklist

Before publishing documentation:

- [ ] Audience is clear (who is this for?)
- [ ] Purpose is clear (why would they read this?)
- [ ] Title is specific (not just "Guide to X")
- [ ] Starts with a concrete example or scenario
- [ ] Step-by-step instructions are exact (copy-paste works)
- [ ] Includes a "how to verify it worked" section
- [ ] Has common mistakes or gotchas
- [ ] Links to related documentation
- [ ] Is scannable (headers, lists, code blocks)
- [ ] No "and then you'll understand" — shows don't tell
- [ ] Is current (not outdated)
- [ ] Fits the audience reading it

## File Organization

```
docs/
├── getting-started/          # For new team members
│   ├── setup.md
│   ├── first-feature.md
│   └── debugging.md
├── guides/                   # How-to guides
│   ├── authentication.md
│   ├── testing.md
│   ├── deployment.md
│   └── performance.md
├── reference/                # Look-up documents
│   ├── api.md
│   ├── configuration.md
│   └── cli-commands.md
├── concepts/                 # Understanding documents
│   ├── architecture.md
│   ├── data-flow.md
│   └── state-management.md
└── faq.md                    # Frequently asked questions
```

## Maintenance

Documentation needs upkeep:

1. **Add to Definition of Done**: "Is documentation updated?" checklist item
2. **Link from Code**: Comments link to relevant docs
3. **Version with Code**: Keep docs in sync with code versions
4. **Archive Old Docs**: Move deprecated docs to `/archive/`
5. **Quick Review**: Weekly scan for obviously outdated info

## Real-World Example

**Before (Too Long):**
> "When implementing authentication in your application, it's important to understand that there are many approaches you can take. Historically, applications used session-based authentication, which involves storing session data on the server. However, with the rise of microservices and distributed systems, JWT-based authentication has become more popular because it's stateless and can be verified without accessing a central session store..."

**After (Progressive Disclosure):**
> "Add JWT authentication to your API in 3 commands"
> 
> ```bash
> npm install jsonwebtoken
> npm install dotenv
> ```
> 
> Then add this to your auth endpoint: [exact code example]
> 
> **Why JWT?** Stateless, works with distributed systems.  
> **Alternative**: Session-based auth for simpler apps.

The after version lets developers get started immediately. Those wanting deeper understanding have links to explanations.

## Key Takeaway

Good documentation is:
- **Specific**: Not abstract
- **Complete**: Includes verification steps
- **Progressive**: Readers don't need to understand everything to get started
- **Scannable**: Lots of headers, code blocks, lists
- **Current**: Kept in sync with code
