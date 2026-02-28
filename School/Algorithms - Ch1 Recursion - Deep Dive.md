---
aliases:
  - Ch1 Deep Dive
  - Recursion Deep Dive
tags:
  - cs
---
# Algorithms — Ch1 Recursion: Deep Dive

Companion to [[Algorithms - Ch1 Recursion]] — Part of [[Algorithms Catch-Up]]

---

## 1.1 Reductions — Going Deeper

The king analogy is the right intuition. The formal version: if you can solve problem B using a solution to problem A, you've *reduced* B to A.

**Real examples:**

| Problem | Reduction |
|---------|-----------|
| Find GCD of two numbers | GCD(a, b) = GCD(b, a mod b) — reduce to smaller numbers |
| Binary search | Search in array → search in *half* the array |
| Merge sort | Sort n elements → sort two halves, then merge |
| Factorial | n! = n × (n−1)! — reduce to smaller factorial |

The pattern: you don't solve the whole thing. You make it slightly smaller and trust that the smaller version works.

---

## 1.2 Simplify and Delegate — The Recursion Template

Every recursive function answers exactly two questions:

1. **Base case** — can I solve this directly? If yes, do it.
2. **Recursive case** — if not, reduce to a smaller version and delegate.

**Template:**
```python
def solve(problem):
    if is_base_case(problem):
        return direct_solution(problem)
    smaller = reduce(problem)
    return combine(solve(smaller))
```

**Concrete examples:**

```python
# Factorial
def factorial(n):
    if n == 0: return 1          # base case: 0! = 1
    return n * factorial(n - 1)  # delegate to n-1

# Sum of a list
def sum_list(lst):
    if len(lst) == 0: return 0           # base case: empty list sums to 0
    return lst[0] + sum_list(lst[1:])    # head + sum of tail

# Fibonacci
def fib(n):
    if n <= 1: return n                  # base cases: fib(0)=0, fib(1)=1
    return fib(n-1) + fib(n-2)          # two recursive calls (binary recursion)
```

**Why induction is the same thing:** When you prove a recursive algorithm correct by induction, you say "assume it works for n−1 (induction hypothesis), prove it works for n." That's exactly the recursive case. The base case is the base case. Same idea, different vocabulary.

**Common recursion patterns:**

| Pattern | Description | Example |
|---------|-------------|---------|
| Linear | One recursive call, size shrinks by 1 | Factorial, list sum |
| Binary | Two recursive calls, size halves | Merge sort, Fibonacci |
| Tail | Recursive call is the last operation | Factorial with accumulator |
| Tree | Multiple calls, branching structure | Tree traversal |

**Tail recursion** is worth knowing — if the recursive call is the *last* thing the function does, some languages (not Python, but Haskell and most functional languages) can optimize it into a loop with no stack growth.

```haskell
-- Tail recursive factorial (accumulator pattern)
factorial :: Int -> Int -> Int
factorial 0 acc = acc
factorial n acc = factorial (n-1) (n * acc)
```

---

## 1.3 Tower of Hanoi — The Recurrence

The key insight your notes got right: ignore everything except the bottom disk. Here's the full mechanical breakdown:

**To move n disks from peg A to peg C using peg B:**
1. Move n−1 disks from A to B (using C as buffer) → T(n−1) moves
2. Move the largest disk from A to C → 1 move
3. Move n−1 disks from B to C (using A as buffer) → T(n−1) moves

**Recurrence:** T(n) = 2T(n−1) + 1, with T(0) = 0

**Solving it:**
```
T(1) = 2T(0) + 1 = 1
T(2) = 2T(1) + 1 = 3
T(3) = 2T(2) + 1 = 7
T(4) = 2T(3) + 1 = 15
Pattern: T(n) = 2ⁿ − 1
```

This is exponential — and it's proven to be *optimal*. You cannot solve Tower of Hanoi in fewer moves. No matter what algorithm you use, you need at least 2ⁿ − 1 moves.

---

## 1.4 Merge Sort — The Full Picture

**Recurrence:** T(n) = 2T(n/2) + O(n)

**Solving via Master Theorem** (a=2, b=2, f(n)=n):
- log_b(a) = log₂(2) = 1
- f(n) = n = n¹ = n^(log_b(a))
- → Case 2: T(n) = **O(n log n)**

**Worked example — sorting [3, 1, 4, 1, 5, 9]:**
```
Split:  [3, 1, 4]        [1, 5, 9]
Split:  [3] [1, 4]       [1] [5, 9]
Split:  [3] [1] [4]      [1] [5] [9]
Merge:  [1, 3] [4]  →   [1, 3, 4]    [1, 5, 9]
Merge:              →   [1, 1, 3, 4, 5, 9]
```

**Properties:**
- **Time:** O(n log n) — always, guaranteed. No bad inputs.
- **Space:** O(n) — needs a temporary array for merging
- **Stable:** yes — equal elements stay in original relative order
- **In-place?** No (standard merge sort). There are in-place variants but they're complex.

**Why merge sort beats insertion sort for large n:**
- Insertion sort: O(n²) — fine for small arrays
- Merge sort: O(n log n) — scales much better
- For n=1000: insertion sort → ~500,000 ops; merge sort → ~10,000 ops

---

## 1.5 Quick Sort — The Full Picture

Quick sort's core idea is different from merge sort: instead of splitting evenly by position, you split by *value* using a **pivot**.

**Steps:**
1. Choose a pivot element
2. Partition: all elements < pivot go left, all elements > pivot go right
3. Recursively sort left and right partitions

```python
def quicksort(arr):
    if len(arr) <= 1: return arr
    pivot = arr[len(arr) // 2]
    left  = [x for x in arr if x < pivot]
    mid   = [x for x in arr if x == pivot]
    right = [x for x in arr if x > pivot]
    return quicksort(left) + mid + quicksort(right)
```

**Recurrence:** T(n) = T(k) + T(n−k−1) + O(n), where k is the pivot's final position

**Time complexity:**
| Case | When | Time |
|------|------|------|
| Best | Pivot always splits exactly in half | O(n log n) |
| Average | Random data | O(n log n) |
| Worst | Pivot is always min or max (sorted array, bad pivot) | O(n²) |

**Pivot strategies:**
- First/last element: simple, but O(n²) on sorted arrays
- Random element: avoids worst case in practice
- Median-of-three: take median of first, middle, last — good in practice

**Quick sort vs Merge sort:**

| | Quick Sort | Merge Sort |
|--|-----------|-----------|
| Average time | O(n log n) | O(n log n) |
| Worst case | O(n²) | O(n log n) |
| Space | O(log n) in-place | O(n) |
| Stable | No | Yes |
| Cache friendly | Yes | Less so |
| Used in practice | Yes (std::sort in C++) | Yes (Python's sorted(), Java Arrays.sort for objects) |

---

## Things to Know for Exams / Interviews

- Always identify the **base case** first when writing recursive functions
- **Recurrence relation** → use Master Theorem to solve (learn all three cases)
- Tower of Hanoi = 2ⁿ − 1 moves (exponential, unavoidable)
- Merge sort = O(n log n) guaranteed, O(n) space
- Quick sort = O(n log n) average, O(n²) worst, in-place
- The difference between merge sort and quick sort: merge sort splits by *position*, quick sort splits by *value*

---

## Related

- [[Algorithms - Ch1 Recursion]]
- [[Algorithms Catch-Up]]
