---
aliases:
  - Catch-Up Roadmap
  - CS Gaps
  - Go Back References
tags:
  - academic
---

# CS Catch-Up Roadmap

Things I need to go back and actually learn. Prioritized in the order I want to hit them.

Part of [[Academic]]

---

## Priority Order

1. [[#Algorithms]] — get Big O solid, everything past it
2. [[#Networking]] — TCP, IP, WebSockets, servers, byte encoding/encryption
3. [[#Databases]] — light, just get good at PostgreSQL and MySQL
4. [[#Operating Systems]] — concurrency, scheduling, memory
5. [[#Language Fundamentals]] — write compilers and interpreters in C
6. [[#Math]] — do last, still taking these classes

---

## Algorithms

Active plan: [[Algorithms Catch-Up]] — Jeff Erickson + Abdul Bari + LeetCode

**Courses:** CS 325 — Analysis of Algorithms (Fall 2025), CS 261 — Data Structures (Spring 2025)

### Big O / Complexity

- [ ] Big O, Omega, Theta notation — formal definitions
- [ ] Asymptotic analysis — best, average, worst case
- [ ] Amortized analysis (aggregate, accounting, potential methods)
- [ ] Sorting lower bounds — why O(n log n) is optimal for comparison sorts

### Recurrences

- [ ] Writing and solving recurrence relations
- [ ] Master theorem (all three cases)
- [ ] Substitution method, recursion tree method

### Divide and Conquer

- [ ] Merge sort — implementation + recurrence
- [ ] Quicksort — partitioning, pivot strategies, worst vs average case
- [ ] Binary search — iterative and recursive
- [ ] Strassen's matrix multiplication

### Dynamic Programming

- [ ] Memoization vs tabulation
- [ ] Classic problems: Fibonacci, 0/1 Knapsack, Longest Common Subsequence, Matrix Chain Multiplication, Edit Distance, Coin Change
- [ ] Identifying overlapping subproblems and optimal substructure

### Greedy Algorithms

- [ ] Activity selection problem
- [ ] Huffman encoding
- [ ] When greedy works vs when it doesn't

### Graph Algorithms

- [ ] BFS — level-order traversal, shortest path in unweighted graphs
- [ ] DFS — stack-based, recursion, timestamps
- [ ] Topological sort
- [ ] Dijkstra's algorithm — single-source shortest path (non-negative weights)
- [ ] Bellman-Ford — handles negative weights, detects negative cycles
- [ ] Floyd-Warshall — all-pairs shortest path
- [ ] Prim's and Kruskal's — minimum spanning trees

### Data Structures (from CS 261)

- [ ] Hash tables — hash functions, chaining vs open addressing, load factor
- [ ] BSTs — insert, delete, search, traversals
- [ ] AVL trees — rotations, balance factor
- [ ] Red-black trees — rules, why they stay balanced
- [ ] Heaps / priority queues — heapify, heap sort
- [ ] Graph representations — adjacency list vs adjacency matrix

### NP Completeness

- [ ] P vs NP — what the question actually is
- [ ] NP-hard vs NP-complete
- [ ] Reductions — how to prove a problem is NP-complete
- [ ] Classic NP-complete problems (SAT, 3-SAT, vertex cover, traveling salesman, clique)

---

## Networking

**Courses:** CS 372 — Intro to Computer Networks (Fall 2025)

### OSI Model / TCP/IP Stack

- [ ] All 7 OSI layers — what each does, where protocols live
- [ ] TCP/IP 4-layer model vs OSI
- [ ] Encapsulation — how data gets wrapped going down the stack

### Application Layer

- [ ] HTTP/HTTPS — request/response cycle, methods (GET, POST, PUT, DELETE, PATCH), status codes
- [ ] HTTP/1.1 vs HTTP/2 vs HTTP/3
- [ ] DNS — how domain resolution works, recursive vs iterative lookup, record types (A, AAAA, CNAME, MX, TXT)
- [ ] SMTP, FTP basics
- [ ] DHCP — how devices get IPs

### Transport Layer

- [ ] TCP — 3-way handshake (SYN, SYN-ACK, ACK), 4-way teardown
- [ ] TCP flow control (sliding window) and congestion control (slow start, AIMD, congestion avoidance)
- [ ] UDP — connectionless, when to use it
- [ ] Ports — well-known vs ephemeral, how port multiplexing works
- [ ] Sockets — socket programming, binding, listening, accept, connect

### Network Layer

- [ ] IP addresses — IPv4 structure, IPv6 basics
- [ ] Subnetting — CIDR notation, subnet masks, calculating network/broadcast addresses
- [ ] NAT — how address translation works, why it exists
- [ ] Routing — how routers forward packets, routing tables
- [ ] Routing protocols — OSPF (link-state), BGP (path-vector), RIP (distance-vector)
- [ ] ICMP — ping, traceroute, how they work under the hood

### Data Link Layer

- [ ] Ethernet frames — structure, preamble, MAC addresses, FCS
- [ ] ARP — how IP maps to MAC, ARP table, ARP request/reply
- [ ] Switches vs routers — what layer they operate at

### WebSockets

- [ ] WebSocket handshake — how it upgrades from HTTP
- [ ] Full-duplex communication — why this matters vs HTTP
- [ ] WebSocket frames — opcodes, masking
- [ ] Building a basic WebSocket server in C

### Security / Encryption / Encoding

- [ ] Symmetric encryption — AES, why keys matter
- [ ] Asymmetric encryption — RSA, public/private key pairs
- [ ] TLS/SSL — handshake process, certificates, certificate authorities
- [ ] HTTPS — what TLS adds on top of HTTP
- [ ] Hashing — SHA-256, MD5, why hashing is one-way
- [ ] Base64 encoding — what it is, when and why it's used
- [ ] UTF-8 encoding — how text maps to bytes, byte order mark
- [ ] Binary/hex — reading raw packet data

---

## Databases

See also: [[CS340 - Notes|CS 340]]

**Courses:** CS 340 — Introduction to Databases (Summer 2025)

### Relational Model

- [ ] Tables, rows, columns — primary keys, foreign keys, constraints
- [ ] ER diagrams — entities, attributes, relationships, cardinality (1:1, 1:N, M:N)
- [ ] Converting ER diagrams to relational schema

### SQL

- [ ] CRUD — CREATE, READ (SELECT), UPDATE, DELETE
- [ ] WHERE, ORDER BY, GROUP BY, HAVING
- [ ] Aggregate functions — COUNT, SUM, AVG, MIN, MAX
- [ ] Joins — INNER, LEFT, RIGHT, FULL OUTER, CROSS, self-join
- [ ] Subqueries and CTEs (WITH clause)
- [ ] Indexes — when to use them, how they speed up queries

### Normalization

- [ ] 1NF — atomic values, no repeating groups
- [ ] 2NF — no partial dependencies
- [ ] 3NF — no transitive dependencies
- [ ] BCNF — every determinant is a candidate key

### Transactions

- [ ] ACID — Atomicity, Consistency, Isolation, Durability
- [ ] Transaction isolation levels — READ UNCOMMITTED, READ COMMITTED, REPEATABLE READ, SERIALIZABLE
- [ ] Deadlocks in databases

### PostgreSQL / MySQL

- [ ] Setting up PostgreSQL locally
- [ ] psql CLI basics
- [ ] Setting up MySQL locally
- [ ] mysql CLI basics
- [ ] Differences between PostgreSQL and MySQL

---

## Operating Systems

**Courses:** CS 374 — Operating Systems I (Fall 2025), CS 271 — Computer Arch & Assembly Language (Spring 2025)

### Processes and Threads

- [ ] Process vs thread — what's shared, what's not
- [ ] Process states — new, ready, running, waiting, terminated
- [ ] PCB (Process Control Block) — what the OS tracks
- [ ] Context switching — what happens, why it's expensive
- [ ] Fork and exec — how Unix spawns processes

### CPU Scheduling

- [ ] FCFS, SJF, SRTF, Round Robin, Priority scheduling
- [ ] Preemptive vs non-preemptive
- [ ] Metrics — turnaround time, waiting time, throughput, response time
- [ ] Multilevel queue and multilevel feedback queue

### Synchronization and Concurrency

- [ ] Race conditions — why they happen
- [ ] Critical section problem — mutual exclusion, progress, bounded waiting
- [ ] Mutex locks — implementation
- [ ] Semaphores — counting vs binary, P and V operations
- [ ] Monitors and condition variables
- [ ] Classic problems: Producer-Consumer, Readers-Writers, Dining Philosophers
- [ ] Spinlocks vs blocking locks

### Deadlocks

- [ ] Coffman conditions — mutual exclusion, hold and wait, no preemption, circular wait
- [ ] Deadlock prevention — breaking one Coffman condition
- [ ] Deadlock avoidance — Banker's algorithm
- [ ] Deadlock detection and recovery

### Memory Management

- [ ] Paging — page tables, page size, fragmentation
- [ ] Segmentation — segments vs pages
- [ ] TLB (Translation Lookaside Buffer) — why it exists, how it speeds up translation
- [ ] Virtual memory — demand paging, page faults
- [ ] Page replacement algorithms — FIFO, LRU, Optimal, Clock
- [ ] Thrashing — what it is, how to avoid it

### File Systems

- [ ] File system structure — boot block, superblock, inodes, data blocks
- [ ] Inodes — what they store, how they point to data
- [ ] Directory structure
- [ ] FAT vs ext4 concepts

### IPC and System Calls

- [ ] System calls — how userspace calls the kernel
- [ ] Pipes — unnamed and named
- [ ] Message queues
- [ ] Shared memory
- [ ] Signals — SIGINT, SIGKILL, SIGTERM, signal handlers

### Low-Level (from CS 271)

- [ ] x86 assembly basics — registers (RAX, RBX, RCX, RDX, RSP, RBP, RIP), MOV, ADD, SUB, CMP, JMP
- [ ] Stack frames — how function calls work in assembly, push/pop, calling conventions
- [ ] Interrupts — hardware vs software, how the OS handles them
- [ ] Memory hierarchy — registers, L1/L2/L3 cache, RAM, disk — latency differences
- [ ] Two's complement — signed integer representation
- [ ] Binary and hex — fluency with both

---

## Language Fundamentals

See also: [[CS381 - Notes|CS 381]], [[Stack Machines]], [[Types and Polymorphism]]

**Courses:** CS 381 — Programming Language Fundamentals (Winter 2026, current), CS 271 — Computer Arch & Assembly Language (Spring 2025)

**Goal:** Be able to write compilers and interpreters from scratch in C.

### Formal Languages and Grammars

- [ ] Chomsky hierarchy — Type 0, 1, 2, 3 grammars
- [ ] Regular languages — regular expressions, finite automata (DFA, NFA)
- [ ] Context-free grammars — BNF, EBNF
- [ ] Parse trees and derivations — leftmost vs rightmost
- [ ] Ambiguous grammars — how to identify and fix

### Lexing / Tokenization

- [ ] What a lexer does — turning raw text into tokens
- [ ] Token types — keywords, identifiers, literals, operators, punctuation
- [ ] Writing a lexer in C

### Parsing

- [ ] Top-down vs bottom-up parsing
- [ ] Recursive descent parsing — implementing by hand in C
- [ ] LL(1) parsing — FIRST and FOLLOW sets, parsing table
- [ ] LR parsing — shift-reduce, LR(0), SLR, LALR — conceptual understanding

### Abstract Syntax Trees

- [ ] What an AST is and why it matters
- [ ] Building an AST from a parse tree
- [ ] Traversing an AST

### Type Systems

- [ ] Static vs dynamic typing
- [ ] Strong vs weak typing
- [ ] Type inference basics
- [ ] Polymorphism — subtype, parametric, ad-hoc, coercion (from CS 381)

### Interpreters

- [ ] Tree-walking interpreter — eval over AST
- [ ] Environment / scope — how variable lookup works
- [ ] Closures — what they are at the implementation level

### Compilers

- [ ] Compilation pipeline — source → tokens → AST → IR → code gen → binary
- [ ] Symbol tables
- [ ] Intermediate representations (IR)
- [ ] Code generation basics — targeting x86 or a simple VM

### Stack Machines

- [ ] Stack-based VM — push/pop model, instruction dispatch
- [ ] Bytecode — encoding instructions
- [ ] Writing a stack machine in C (connects to CS 381 content)

### Lambda Calculus

- [ ] Syntax — variables, abstraction, application
- [ ] Beta reduction
- [ ] Church encodings (booleans, numbers)

---

## Math

**Goal:** Do these last — still in the middle of some of these courses.

### Already Taken

**MTH 112Z — Precalculus II / Trigonometry (Summer 2024)**
- [ ] Unit circle — all angles in radians and degrees
- [ ] Trig identities — Pythagorean, sum/difference, double angle, half angle
- [ ] Inverse trig functions
- [ ] Polar coordinates — converting between polar and rectangular
- [ ] Complex numbers in polar form

**MTH 231 — Elements of Discrete Mathematics (Fall 2024)**
- [ ] Propositional logic — truth tables, logical equivalences, tautologies
- [ ] Predicate logic — quantifiers, nested quantifiers
- [ ] Proof techniques — direct proof, proof by contradiction, proof by contrapositive, mathematical induction, strong induction
- [ ] Sets — operations, power sets, Cartesian products, set identities
- [ ] Functions — injective, surjective, bijective, composition, inverse
- [ ] Relations — equivalence relations, partial orders
- [ ] Combinatorics — permutations, combinations, pigeonhole principle, binomial theorem
- [ ] Recurrence relations — solving linear recurrences
- [ ] Graph theory — paths, cycles, trees, planarity, coloring, Euler/Hamiltonian paths

**MTH 251 — Differential Calculus (Fall 2024)**
- [ ] Limits — definition, one-sided limits, limits at infinity
- [ ] Continuity
- [ ] Derivatives — definition as limit, geometric meaning
- [ ] Differentiation rules — power, product, quotient, chain rule
- [ ] Implicit differentiation
- [ ] Related rates
- [ ] Optimization — local/global extrema, first/second derivative tests
- [ ] L'Hôpital's rule

**MTH 252 — Integral Calculus (Winter 2025)**
- [ ] Antiderivatives
- [ ] Riemann sums — left, right, midpoint, trapezoidal
- [ ] Fundamental Theorem of Calculus — both parts
- [ ] Integration techniques — u-substitution, integration by parts, trig substitution, partial fractions
- [ ] Applications — area between curves, volume of solids of revolution, arc length

### Still To Take

**Linear Algebra** (need to take this — will be relevant to computer graphics, ML, everything)
- Vectors and vector spaces
- Matrix operations — addition, multiplication, transpose, inverse
- Determinants
- Linear transformations
- Eigenvalues and eigenvectors
- Dot product, cross product, projections

**Vector Calculus / Multivariable Calculus**
- Partial derivatives and gradients
- Directional derivatives
- Multiple integrals
- Line integrals and surface integrals
- Divergence and curl
- Green's, Stokes', and Divergence theorems
