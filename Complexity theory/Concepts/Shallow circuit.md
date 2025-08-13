---
tags: 
Created: 2025-08-09 14:01
aliases: 
related: 
link: 
Type:
---
# Shallow circuit

> In the lecture 06, lecturer mention the noun Shallow circuit to try to interpret the bounded-Depth Circuit.

A **shallow circuit** means a Boolean (or arithmetic) circuit with **small depth** — meaning the maximum number of gates from any input to the output is small, often _polylogarithmic_ in the input size.

## 1 Formal idea

- **Circuit depth** = length of the longest path from an input wire to the output gate.
- **Shallow** = depth much smaller than the number of inputs, often
    $\text{depth} = O(\log^k n) \quad\text{or}\quad O(1)$
    instead of $O(n)$ or worse.

## 2 Examples

- **Depth 2**: An **AND of ORs** or **OR of ANDs** — essentially CNF or DNF formulas.
- **Depth $O(\log n)$**: Balanced binary tree of gates computing, e.g., addition via divide-and-conquer.
    
## 3 Why it matters in complexity & IP/deIP

- **Shallow circuits** can be evaluated in parallel quickly → they belong to classes like $\mathsf{NC}^0$ , $\mathsf{NC}^1$, $\mathsf{AC}^0$.
    
- In _interactive proofs_ or _doubly-efficient interactive proofs_, shallow circuits are often easier to **verify** than to **compute from scratch** for large instances.
    
- Many delegation protocols use the fact that “verifying” a shallow circuit (via sumcheck, GKR protocol, etc.) can be done in **time much less** than evaluating it directly.

## 4 Quick picture

If we think of a circuit as a DAG:

```
depth = 3  (shallow)
input --> gate --> gate --> output
```

vs.

```
depth = 20 (deep)
input --> ... many layers ... --> output
```

---

In your lecture, when they mention **shallow circuit**, they likely mean:

> A Boolean or arithmetic circuit of low depth, so that the verifier can exploit structure to check correctness more efficiently than naive recomputation.

---

If you want, I can connect this directly to the **GKR protocol**, which is the standard way deIP verifiers handle shallow circuits in quasilinear time. That’s probably why your lecturer brought it up.