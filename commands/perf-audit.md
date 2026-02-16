---
description: Perform a measurement-driven performance audit
argument-hint: "<system-or-flow>"
---

Performance audit: `$ARGUMENTS`

## Audit Workflow

1. **Establish Baseline**
   - Define key metrics (latency, throughput, CPU, memory)
   - Record current measurements

2. **Profile and Measure**
   - Identify critical paths
   - Locate bottlenecks with data

3. **Analyze Root Causes**
   - Distinguish symptoms vs causes
   - Note contributing factors

4. **Recommend Optimizations**
   - Prioritize by impact and effort
   - Avoid premature optimization

5. **Validate Improvements**
   - Compare before/after metrics
   - Confirm no regressions

## Output Template

Use: `docs/templates/performance-audit.md`

## Usage

- `/perf-audit "checkout flow"`
- `/perf-audit "search API latency"`
