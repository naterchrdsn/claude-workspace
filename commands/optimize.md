---
description: Analyze code and suggest performance improvements
argument-hint: "<code-section>"
---

Optimize: `$ARGUMENTS`

## Performance Optimization Framework

### Measure First
1. **Identify the Problem**
   - What is slow?
   - How slow is it?
   - What is "acceptable" performance?

2. **Profile the Code**
   - Use profiling tools
   - Identify bottlenecks
   - Measure memory usage
   - Check database query performance

3. **Establish Baseline**
   - Document current performance
   - Create reproducible test case
   - Measure before optimization

### Find Root Causes
- Algorithmic inefficiency (O(n²) vs O(n))
- Resource utilization (memory, CPU, I/O)
- Unnecessary work (duplicate queries, calculations)
- Blocking operations (network, disk)

### Evaluate Trade-offs
- **Complexity vs. Gain**
  - Is 2x performance worth 3x complexity?
  - New tech debt or technical risk?
  
- **Readability vs. Performance**
  - Does optimization reduce clarity?
  - Can we document it well?

- **Maintenance vs. Performance**
  - Harder to maintain?
  - More brittle?

### Common Optimizations

**Algorithm & Logic**
- Use better algorithm (e.g., binary search vs. linear)
- Avoid duplicate work (memoization, caching)
- Simplify logic (fewer operations)

**Database**
- Use indices (selectively)
- Optimize queries (avoid N+1)
- Use connection pooling

**Caching**
- Cache computed results
- Cache HTTP responses
- Use appropriate cache invalidation

**Parallelization**
- Process data in parallel
- Use async/await properly
- Avoid synchronous blocking

## Verification

1. **Benchmark Again**
   - Measure after optimization
   - Calculate actual improvement
   - Verify assumptions

2. **Verify Correctness**
   - All tests still pass
   - Behavior unchanged
   - Edge cases handled

3. **Deploy & Monitor**
   - Monitor in production
   - Track actual improvements
   - Revert if issues arise

## Usage

- `/optimize "user loading on dashboard"` — Optimize slow experience
- `/optimize "database queries"` — Improve query performance
- `/optimize "bundle size"` — Reduce assets
