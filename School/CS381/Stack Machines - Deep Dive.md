---
aliases:
  - Stack Machines Deep Dive
  - Stack VM Deep Dive
tags:
  - school
  - school/cs381
  - cs/vm
---
# Stack Machines — Deep Dive

Companion to [[Stack Machines]] — Part of [[CS381 - Notes]]

---

## Why Stack Machines Exist

The reason stack machines are popular for VMs is that they are **easy to compile to**. In a register machine (like x86), the compiler has to figure out which values go in which registers — this is called *register allocation*, and it's a hard problem. Stack machines sidestep this entirely: you just push operands and pop results.

**Famous stack machines:**
- **JVM** (Java Virtual Machine) — Java, Kotlin, Scala, Clojure all compile to JVM bytecode
- **CPython** — Python's default interpreter is a stack machine
- **WebAssembly (WASM)** — the "assembly language of the web" is a stack machine
- **CLR** (.NET) — C#, F#, VB.NET compile to CLR bytecode, also stack-based

**Register machines (for contrast):**
- x86/x86-64 — your actual CPU. Has registers (RAX, RBX, RCX...). Much faster than a VM.
- ARM — iPhones, Apple Silicon Macs, most mobile chips

---

## Step-by-Step Execution Example

A fuller command set than what's in your notes (common in CS 381 context):

| Command | Effect |
|---------|--------|
| `PUSH n` | Push integer n onto stack |
| `POP k` | Pop k elements off stack |
| `INC` | Increment top element |
| `SWAP` | Swap top two elements |
| `ADD` | Pop two, push their sum |
| `DUP` | Duplicate top element |
| `NOP` | No operation |

**Tracing a program:**

```
Program: PUSH 3, PUSH 4, ADD, PUSH 2, SWAP, POP 1

Step 0:           Stack: []
PUSH 3  →         Stack: [3]
PUSH 4  →         Stack: [3, 4]     ← top is right
ADD     →         Stack: [7]         (pops 4 and 3, pushes 7)
PUSH 2  →         Stack: [7, 2]
SWAP    →         Stack: [2, 7]
POP 1   →         Stack: [2]
```

---

## Rank — The Full Picture

Your notes define rank correctly. Here's the part worth internalizing:

**Rank of a program ≠ safety of a program at every step.**

A well-ranked *program* means the total rank is ≥ 0 and the stack never goes negative at any intermediate step. Both conditions must hold.

**Example — well-ranked at the end, but underflows in the middle:**

```
Program: POP 2, PUSH 1, PUSH 1
Ranks:    -2       +1      +1     = 0 total

If stack starts with [x]:
POP 2 → tries to pop 2 from [x] → UNDERFLOW (only 1 element)
```

Even though the program's total rank is 0, it's not well-ranked because it underflows at step 1.

**How to check well-rankedness properly:**
- Track the *running rank* (cumulative sum at each step)
- The running rank must never go below the negative of the initial stack size
- For a program that must work on an *empty* initial stack: the running rank must never go negative

**Rank checker algorithm (what Assignment 5 is testing):**
```
rank_of_program = 0
for each command in program:
    rank_of_program += rank(command)
    if rank_of_program < 0:
        return "ill-ranked"
return "well-ranked"
```

---

## JIT vs Interpretation — Clarified

Your notes say the VM "translates instructions in real time for execution on the CPU" — that's JIT, but not all VMs do this.

| Mode | How it works | Speed | Example |
|------|-------------|-------|---------|
| **Interpretation** | Read bytecode instruction, execute immediately | Slower | Early Python, Ruby MRI |
| **JIT compilation** | Compile bytecode to native machine code at runtime | Much faster | Modern JVM (HotSpot), V8 (JavaScript) |
| **AOT compilation** | Compile everything before running | Fastest startup | Go, Rust, C |

The JVM starts by interpreting, then JIT-compiles "hot" code paths (code that runs frequently). This is why Java has a warm-up period.

---

## Abstract Syntax — What It Actually Means

```
Cmd  ::= INC | SWAP | POP Int
Prog ::= [Cmd]
```

This is a **grammar** written in BNF (Backus-Naur Form). It defines the *structure* of valid programs:
- A `Cmd` (command) is one of three things: INC, SWAP, or POP applied to an Int
- A `Prog` (program) is a list of commands

In Haskell, this translates directly to:
```haskell
data Cmd = INC | SWAP | POP Int
type Prog = [Cmd]
```

This is why Haskell is used in CS 381 — the abstract syntax maps almost 1:1 to Haskell data types.

---

## Things to Know for Exams

- Stack machines use a stack as their only working memory — no registers
- Rank of `INC` = 0, `SWAP` = 0, `POP k` = −k
- A well-ranked program never underflows at any step (not just at the end)
- Total program rank = sum of all command ranks
- The rank checker must track running rank, not just final rank
- JVM is the most important real-world stack machine example

---

## Related

- [[Stack Machines]]
- [[CS381 - Notes]]
- [[CS381 - Assignment 5]]
- [[Types and Polymorphism]]
