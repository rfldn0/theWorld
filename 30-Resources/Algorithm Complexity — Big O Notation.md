---
title: "Algorithm Complexity — Big O Notation"
date: 2026-06-25
tags: [algorithms, computer-science, big-o, complexity, performance]
status: evergreen
source: "CS 1110 + CS 3310 — Senior_ vault"
related: []
---

## Summary
Big O notation describes how an algorithm's time or space requirements grow relative to input size. It expresses the worst-case upper bound, enabling comparison of algorithms independent of hardware.

## Main Content

### Common Complexities (best to worst)

| Notation | Name | Example |
|----------|------|---------|
| O(1) | Constant | Array index access, hash table lookup |
| O(log n) | Logarithmic | Binary search |
| O(n) | Linear | Linear search, single loop |
| O(n log n) | Log-linear | Merge sort, heap sort |
| O(n²) | Quadratic | Bubble sort, insertion sort, nested loops |
| O(2ⁿ) | Exponential | Recursive Fibonacci, subsets |
| O(n!) | Factorial | Permutations, brute-force TSP |

### Rules
1. **Drop constants** — O(2n) = O(n)
2. **Drop lower-order terms** — O(n² + n) = O(n²)
3. **Worst case** — Big O describes the ceiling, not the average
4. **Sequential steps add** — O(n) + O(n²) = O(n²)
5. **Nested loops multiply** — O(n) inside O(n) = O(n²)

### Sorting Algorithm Reference

| Algorithm | Best | Average | Worst | Space |
|-----------|------|---------|-------|-------|
| Bubble Sort | O(n) | O(n²) | O(n²) | O(1) |
| Insertion Sort | O(n) | O(n²) | O(n²) | O(1) |
| Merge Sort | O(n log n) | O(n log n) | O(n log n) | O(n) |
| Quick Sort | O(n log n) | O(n log n) | O(n²) | O(log n) |
| Heap Sort | O(n log n) | O(n log n) | O(n log n) | O(1) |

### Space Complexity
Same notation, applied to memory usage instead of time. An in-place algorithm uses O(1) extra space.

## Key Insights
- O(log n) algorithms are powerful because doubling input size only adds one operation (binary search on 1M items ≈ 20 steps)
- O(n²) algorithms become impractical around n = 10,000 in most contexts
- The best algorithm depends on input characteristics — insertion sort beats merge sort on nearly-sorted small arrays despite worse Big O
- Space-time tradeoffs are real: hash tables are O(1) lookup but O(n) space

## Questions / Open Threads
- [ ] How does amortized analysis differ from worst-case Big O?
- [ ] Where does [[Dynamic Programming]] fit in complexity reduction?

## Related
- [[Data Structures Overview]] — structures determine which algorithms are available
