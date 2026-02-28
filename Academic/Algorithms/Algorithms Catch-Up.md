---
aliases:
  - Algs Catch-Up
  - Jeff Erickson Algorithms
  - Algorithms Review
tags:
  - academic
---

# Algorithms Catch-Up

Part of [[CS Catch-Up Roadmap]] — back to [[School]]

## Study Loop

For each topic:
1. Skim previous notes on the topic
2. 30 min — Jeff Erickson's *Algorithms* textbook (free at [jeffe.cs.illinois.edu](http://jeffe.cs.illinois.edu/teaching/algorithms/))
3. 20 min — Abdul Bari on YouTube for visual walkthrough
4. 40 min — LeetCode problem to lock it in

---

## Topics to Cover

### 1. Recursion & Induction → [[Algorithms - Ch1 Recursion]]

- Mathematical induction (proof technique)
- Writing recursive algorithms
- Solving recurrence relations
- Classic problems: Fibonacci, tiling a 1×n board, Tower of Hanoi, pancake sorting, merge sort, Quickselect, Karatsuba multiplication

**Focus on:**
- Writing and analyzing recursive code
- Proving correctness via induction
- Deriving time complexity from recurrences

---

### 2. Asymptotic Analysis

- Big-O, Big-Ω, Big-Θ
- Comparing growth rates
- Running time analysis

**Focus on:**
- Formal definitions of O, Ω, Θ
- Proving bounds
- Comparing functions
- Master Theorem

---

### 3. Dynamic Programming

- Fibonacci (DP version)
- Maximum Independent Set on a path
- Longest Increasing Subsequence (LIS)
- Edit Distance
- Subset Sum
- DP on trees

**Focus on:**
- Identifying overlapping subproblems
- Defining subproblems cleanly
- Building recurrence relations
- Memoization vs. bottom-up
- Reconstructing solutions

---

### 4. Graph Algorithms

- Graph theory basics
- Representations: adjacency list vs. matrix
- BFS and DFS

**Focus on:**
- How BFS and DFS work step-by-step
- Time complexity
- Tree vs. graph differences

---

### 5. Minimum Spanning Trees

- Kruskal's Algorithm
- Prim's Algorithm

**Focus on:**
- Greedy choice property
- Cut property
- Why MST algorithms are correct

---

### 6. Greedy Algorithms

- Job scheduling
- Huffman coding

**Focus on:**
- When greedy works (and when it doesn't)
- Proving greedy correctness
- Counterexamples

---

### 7. Computational Complexity

- Decision problems
- P, NP, NP-complete, NP-hard
- Polynomial-time reductions
- NP-hardness proofs

**Focus on:**
- What it means for a problem to be in NP
- How reductions work
- Classic NP-complete problems: SAT, 3SAT, Subset Sum

---

## Relearn Order

1. Recursion → Big-O → Recurrences
2. Dynamic Programming (highest ROI)
3. Graphs + MST
4. Complexity Theory

---

## Claude Notes

- Merge sort is the best first LeetCode target for recursion — it directly demonstrates divide-and-conquer and recurrence relations (T(n) = 2T(n/2) + O(n) → O(n log n)).
- For Dynamic Programming, start with Fibonacci (memoized vs bottom-up) before jumping to LIS or Edit Distance — the simpler problems build the exact intuition you need.
- The Master Theorem listed under Asymptotic Analysis is crucial — it's the fast way to solve most divide-and-conquer recurrences without doing the full tree expansion.
