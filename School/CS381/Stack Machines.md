---
aliases:
  - Stack VM
  - Stack-Based VM
tags:
  - school
---
# Stack Machines

Part of [[CS381 - Notes]] — deep dive: [[Stack Machines - Deep Dive]]

---

## What is a Stack Machine?

A stack-based virtual machine is an abstraction of a computer that emulates a real machine.

It is built as an interpreter of a special bytecode that translates instructions in real time for execution on the CPU.

Unlike register-based VMs, a stack machine has **no registers** — all operations read from and write to a stack.

---

## Key Concepts

- **Bytecode** — intermediate representation executed by the VM
- **Stack** — the only working memory; operands are pushed and popped
- **Interpreter** — translates bytecode to native CPU instructions at runtime

---

## Stack Language Commands

| Command | Description |
|---------|-------------|
| `INC` | Increments the topmost element (must be an Int) |
| `SWAP` | Exchanges the two topmost elements |
| `POP k` | Pops `k` elements off the stack |

---

## Command Rank

A command's **rank** describes how it transforms the stack size:

| Command | Rank | Reason |
|---------|------|--------|
| `INC` | 0 | Replaces top element — no size change |
| `SWAP` | 0 | Exchanges elements — no size change |
| `POP k` | -k | Removes k elements |

A **well-ranked program** is one where the stack never underflows — every pop has enough elements on the stack.

---

## Abstract Syntax

```
Cmd  ::= INC | SWAP | POP Int
Prog ::= [Cmd]
```

---

## Claude Notes

- The description "translates instructions in real time for execution on the CPU" describes JIT compilation, but not all stack VMs do this — many interpret bytecode directly without translating to native code. The JVM can do both. Worth clarifying which model your class is using.
- A well-ranked program ensures no underflow, but it's also worth noting that rank alone doesn't guarantee *correctness* — a program can be well-ranked and still leave garbage on the stack.

---

## Related

- [[CS381 - Notes]]
- [[CS381 - Assignment 5]]
- [[Types and Polymorphism]]
