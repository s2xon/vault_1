---
aliases:
  - CS381 HW5
  - Assignment 5
tags:
  - school
---
# CS381 — Assignment 5

Part of [[CS381 - Notes]]

---

## Topic: Stack Language

This assignment extends the stack language interpreter covered in [[Stack Machines]].

---

## Stack Language Commands

| Command | Description |
|---------|-------------|
| `INC` | Increments the topmost element (must be an Int) |
| `SWAP` | Exchanges the two topmost elements on the stack |
| `POP k` | Pops `k` elements off the stack |

---

## Key Question

> What does it mean to **map each command to its rank**?

A command's **rank** describes how it transforms the stack size:
- Positive rank = net elements added
- Negative rank = net elements removed
- Zero rank = no change in size (e.g., `SWAP`)

For example:
- `POP 2` has rank **-2** (removes 2 elements)
- `INC` has rank **0** (replaces top with new top — no size change)
- `SWAP` has rank **0** (exchanges, no size change)

---

## Abstract Syntax

The extended abstract syntax for the stack language:

```
Cmd ::= INC | SWAP | POP Int | ...
Prog ::= [Cmd]
```

---

## Notes

- See [[Stack Machines]] for the VM fundamentals this builds on
- The assignment likely asks you to implement a rank checker/type system for programs

---

## Related

- [[Stack Machines]]
- [[CS381 - Notes]]
