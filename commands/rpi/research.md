---
description: RPI Phase 1 - Research a feature request and provide GO/NO-GO recommendation
argument-hint: "<path-to-request-file>"
model: haiku
---

# RPI Research Phase

Research the feature request at: `$ARGUMENTS`

## Purpose

Analyze the feature request and produce a **GO/NO-GO recommendation** with supporting evidence. This prevents wasted effort on non-viable features.

## Workflow

### Step 1: Parse Requirements

Use the Task tool to invoke the requirements-analyst agent:
```
Task tool parameters:
- subagent_type: requirements-analyst
- description: Parse and clarify requirements
- prompt: Read the request file at [path]. Extract and clarify:
  - Core feature requirements
  - Success criteria
  - Constraints and assumptions
  - Open questions that need answers
  Write findings to rpi/[feature-slug]/research/requirements.md
```

### Step 2: Technical Feasibility

Use the Task tool to invoke the tech-stack-researcher agent:
```
Task tool parameters:
- subagent_type: tech-stack-researcher
- description: Assess technical feasibility
- prompt: Based on requirements at rpi/[feature-slug]/research/requirements.md:
  - Assess technical feasibility
  - Identify technology options
  - Estimate complexity (Low/Medium/High)
  - Flag potential blockers
  Write findings to rpi/[feature-slug]/research/feasibility.md
```

### Step 3: Strategic Alignment

Use the Task tool to invoke the system-architect agent:
```
Task tool parameters:
- subagent_type: system-architect
- description: Check strategic alignment
- prompt: Review the feature against:
  - Existing architecture patterns
  - Current technical direction
  - Resource availability
  Write findings to rpi/[feature-slug]/research/alignment.md
```

### Step 4: Generate RESEARCH.md

Synthesize findings into a GO/NO-GO recommendation:

```markdown
# Research: [Feature Name]

## Verdict: [GO / NO-GO / CONDITIONAL]

## Executive Summary
[2-3 sentences on the recommendation]

## Requirements Analysis
[Key findings from requirements parsing]

## Technical Feasibility
- Complexity: [Low/Medium/High]
- Blockers: [List any blockers]
- Technology Fit: [Good/Acceptable/Poor]

## Strategic Alignment
- Architecture Fit: [Yes/No/Partial]
- Priority Alignment: [High/Medium/Low]

## Recommendation
[GO with conditions / NO-GO with reasons / Proceed with caveats]

## Next Steps
[If GO: proceed to /rpi:plan]
[If NO-GO: alternatives or required changes]
```

Write to: `rpi/[feature-slug]/research/RESEARCH.md`

## Critical Requirements

1. **Use Task Tool Only**: Invoke agents via Task tool, not bash
2. **Sequential Phases**: Complete each analysis before synthesis
3. **Clear Verdict**: Every research must end with GO/NO-GO
4. **Evidence-Based**: Recommendations must cite specific findings

## Output

Return to user:
- **Verdict**: GO / NO-GO / CONDITIONAL
- **Key Factors**: Top 3 reasons for the recommendation
- **Next Command**: If GO, suggest `/rpi:plan [feature-slug]`

## Usage

```
/rpi:research rpi/user-authentication/REQUEST.md
/rpi:research rpi/payment-integration/REQUEST.md
```
