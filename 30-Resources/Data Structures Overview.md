---
title: "Data Structures Overview"
date: 2026-06-25
tags: [data-structures, computer-science, algorithms]
status: evergreen
source: "CIS 2610 + CS 1110 — Senior_ vault"
related: []
---

## Summary
Data structures define how data is organized and accessed in memory. Choosing the right structure is the primary lever for algorithm performance — the same problem can be O(1) or O(n) depending on the structure used.

## Main Content

### Arrays
- Fixed-size, contiguous memory, zero-indexed
- **Access:** O(1) | **Search:** O(n) | **Insert/Delete:** O(n) (shifting)
- Best for: random access by index, known size, cache-friendly iteration
- Multidimensional arrays: matrix operations, grids

### LinkedList
- Nodes containing value + pointer to next node
- **Access:** O(n) | **Search:** O(n) | **Insert/Delete at head:** O(1)
- Best for: frequent insertions/deletions, unknown size
- Singly vs doubly linked (doubly allows backward traversal)

### Arrays vs LinkedList

| | Array | LinkedList |
|-|-------|-----------|
| Memory | Contiguous | Scattered |
| Access by index | O(1) | O(n) |
| Insert at start | O(n) | O(1) |
| Cache performance | Better | Worse |
| Size | Fixed (static) | Dynamic |

### Stack
- LIFO (Last In, First Out)
- Operations: `push`, `pop`, `peek` — all O(1)
- Use cases: function call stack, undo/redo, expression parsing

### Queue
- FIFO (First In, First Out)
- Operations: `enqueue`, `dequeue` — O(1) with LinkedList backing
- Use cases: BFS, task scheduling, print queues

### HashMap / Dictionary
- Key-value pairs, hash function maps key → index
- **Access/Insert/Delete:** O(1) average, O(n) worst (collisions)
- Best for: fast lookups by key, counting frequencies
- Java: `HashMap`, `TreeMap` (sorted, O(log n))

### TreeMap
- Sorted key-value pairs backed by a balanced BST (Red-Black Tree)
- **All operations:** O(log n)
- Use when: sorted iteration over keys is needed

### Binary Trees / BST
- Each node has left and right children
- BST property: left < root < right
- **Search/Insert/Delete:** O(log n) average, O(n) worst (unbalanced)
- Traversals: in-order (sorted), pre-order, post-order

## Key Insights
- No single best structure — choose based on which operations are most frequent
- HashMap is the default "fast lookup" structure; use TreeMap only when sorted order matters
- LinkedList's O(1) insert is only at known positions — finding the position is still O(n)
- Stacks and Queues are abstract data types — they can be implemented with arrays or linked lists

## Questions / Open Threads
- [ ] How do heaps differ from binary trees?
- [ ] When does a hash collision degrade to O(n)?

## Related
- [[Algorithm Complexity — Big O Notation]] — complexity analysis of operations above
