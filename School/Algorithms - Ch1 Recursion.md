---
aliases:
  - Algorithms Chapter 1
  - Ch1 Recursion
  - Erickson Chapter 1
tags:
  - school
  - cs/algorithms
---
# Algorithms — Chapter 1: Recursion

Part of [[Algorithms Catch-Up]]

---

## 1.1 Reductions

Reduction is the most common technique used in designing algorithms. Break the problem into smaller pieces and delegate.

Think of it like a king with a math problem — he passes parts of the equation down to his attendants, who do the same, until each piece is simple enough to solve directly.

---

## 1.2 Simplify and Delegate

- If the given instance of the problem can be solved directly, solve it directly.
- Otherwise, reduce it to one or more simpler instances of the same problem.

The induction hypothesis is the same idea as recursion.

---

## 1.3 Tower of Hanoi

Ignore everything except the current bottom disk. The goal is always: move the largest remaining disk to the target peg, using the temp peg as a buffer. That's the base case. Everything else is recursion around it.

![[Pasted image 20260225083906.png]]

---

## 1.4 Merge Sort

1. Split the array in half
2. Recursively sort each half
3. Merge the sorted halves

Pretty straightforward. (Do a merge sort LeetCode problem)

---

## 1.5 Quick Sort

Next up — keep dividing sub-arrays until the base case, then build back up. Similar shape to merge sort but different pivot-based splitting logic.

Abdul Bari video: https://www.youtube.com/watch?v=-JTq1BFBwmo&list=PLAXnLdrLnQpRcveZTtD644gM9uzYqJCwr&index=2

---

## Next Time

- Add: how to design an algorithm and analyze its complexity (forgot this part but it'll be easy to remember)

---

# Abdul's Notes
Abdul Bari video: https://www.youtube.com/watch?v=-JTq1BFBwmo&list=PLAXnLdrLnQpRcveZTtD644gM9uzYqJCwr&index=2
This is the video I watched

Went over basics

---
# Top K Element

Alright now i am starting on doing leet code for this stuff



---
## Claude Notes

- **Merge sort is O(n log n), not O(n).** The recurrence is T(n) = 2T(n/2) + O(n), which resolves to O(n log n) via the Master Theorem. You split *twice* but you also merge *n* elements at each level across *log n* levels.
- Section 1.5 doesn't have real quick sort content yet — the description there is still merge sort. Quick sort uses a *pivot* to partition in place rather than merging. Come back to this.
- The induction hypothesis point in 1.2 is correct — recursive correctness proofs are literally induction. Worth connecting this back to the Big-O proofs in Ch2.

---

## Related

- [[Algorithms Catch-Up]]
- [[CS Catch-Up Roadmap]]
