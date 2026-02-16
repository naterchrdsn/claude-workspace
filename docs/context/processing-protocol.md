# Processing Protocol

How to efficiently handle multiple documents and large files without losing critical information.

## The Problem

Reading multiple large documents can:
- Lose critical details in summaries
- Mix up information across sources
- Forget open questions and important caveats
- Waste token budget on unnecessary re-reads

This protocol prevents these issues.

## For 1-3 Short Documents (< 2K words each)

**Just read them sequentially** and work with them directly. No special handling needed.

## For 4+ Documents OR Any Document > 2K Words

Use this 5-step protocol:

### Step 1: List and Prioritize

List all documents with file sizes:

```
1. design-spec.md (1,200 words) - Core requirements
2. api-reference.md (5,400 words) - API details
3. testing-guide.md (3,200 words) - Testing patterns
4. architecture.md (2,800 words) - System design
```

Ask: "Which documents should I focus on first?"

This gives you priority order before diving in.

### Step 2: Process Each Document

For each document in priority order:

1. **Read** the full document
2. **Extract** key information using the **Source Summary Template**:
   - Document name and purpose
   - Key concepts (3-5 main ideas)
   - Specific data (numbers, dates, names)
   - Decision rationale (why these choices)
   - Open questions (OPEN or ASSUMED items)
   - Action items (what needs to happen next)

3. **Write** to `./docs/summaries/source-[filename].md`
4. **Release** the document from active consideration

Template example:

```markdown
# Source Summary: API Reference

**Original:** api-reference.md (5,400 words)
**Purpose:** Define all API endpoints and contracts

## Key Concepts
- RESTful design with JSON payloads
- 10 main endpoint categories
- Authentication via JWT bearer tokens
- Rate limiting: 1,000 req/hour per user

## Critical Numbers
- Response timeout: 30 seconds
- Max batch size: 100 items
- Retention: 90 days
- Max request size: 5MB

## Decision Rationale
- JWT chosen for stateless authentication
- JSON because most clients use it
- 30-second timeout balances latency vs. processing needs

## Open Questions
- OPEN: Should batch endpoints support partial failures?
- ASSUMED: All clients support gzip compression

## Action Items
- [ ] Add rate limiting headers to responses
- [ ] Document webhook retry strategy
- [ ] Add OpenAPI schema
```

### Step 3: Read Summaries, Not Originals

After processing all documents:

- Read **only the summaries** to form your working context
- Summaries are 10-20% of original size
- You have critical info without redundancy

### Step 4: Cross-Reference

Scan summaries for:
- Contradictions between sources
- Dependencies or ordering
- Gaps in information
- Overlapping coverage

Note these explicitly:

```markdown
## Cross-Reference Notes
- API Reference contradicts Design Spec on timeout (30s vs 60s)
  → Use 30s (API Reference is more recent)
- Testing Guide assumes feature X exists, but Architecture 
  shows it's not implemented yet
  → Feature X is OPEN
```

### Step 5: Proceed with Work

Now use the summary layer for all decisions and discussions.

**Reference originals only if:**
- You need exact quote/section
- A summary is unclear
- You're verification checking

## Template: Source Document Summary

Use this format for all multipart work:

```markdown
# Source Summary: [Document Title]

**Original File:** [filename] ([size], Processed [date])
**Purpose:** One-line description

## Overview
Context and key takeaways (3-4 sentences).

## Key Concepts

1. **Concept Name**: Definition and why it matters
2. **Concept Name**: Definition and why it matters
3. **Concept Name**: Definition and why it matters

## Critical Data Points

| Item | Value | Context |
|------|-------|---------|
| Limit | 1,000/hour | Per user, includes retries |
| Timeout | 30 seconds | Hard deadline, no extensions |
| Version | 2.1.0 | Latest stable release |

## Decisions & Rationale

- **Decision**: JWT over session tokens
  **Rationale**: Stateless, works across microservices
  **Trade-off**: Less granular revocation

## Open Questions

- OPEN: Should we support webhook signatures?
- ASSUMED: All clients cache responses locally

## Dependencies

- Requires API v2.0 (feature X uses v3.0 endpoints)
- Blocks implementation of feature Y (waiting for this spec)

## Action Items

- [ ] Specific action 1
- [ ] Specific action 2
```

## For Large Codebases

If processing code files:

1. **Understand structure** — Map directory layout and main modules
2. **Identify key files** — Find critical implementations
3. **Read carefully** — Often smaller and worth reading fully
4. **Summarize patterns** — Look for repeated approaches
5. **Note dependencies** — How modules interact

## For Specification Documents

1. **Extract requirements** — Functional + non-functional
2. **Identify constraints** — Technical, temporal, resource
3. **Note acceptance criteria** — What "done" looks like
4. **Flag assumptions** — What they're assuming about you
5. **List unknowns** — What's explicitly open

## For Research/Analysis Documents

1. **Identify main findings** — Core conclusions
2. **Note supporting evidence** — Data backing claims
3. **Flag contradictions** — Where sources disagree
4. **Extract citations** — References for deeper learning
5. **Note limitations** — Caveats and boundaries

## When to Break This Protocol

You can skip this if:
- Documents are < 1K words total
- You're extracting one specific piece
- Documents are highly related duplicates
- You've worked with this material recently

Otherwise, **use the protocol**. It saves time and prevents information loss.

## Key Principles

1. **One document at a time** — Process sequentially to avoid mixing information
2. **Summary as working memory** — Use summaries, not originals, for decisions
3. **Explicit open questions** — Never assume clarity; mark unknowns
4. **Track exact data** — Numbers, dates, names without rounding
5. **Document rationale** — Why decisions were made, not just what was decided
