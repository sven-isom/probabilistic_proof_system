---
tags: 
Created: 2025-08-08 18:55
aliases: 
related: 
link: 
Type:
---
# Savitch’s theorem
Savitch’s theorem is a fundamental result in computational [[复杂性理论|complexity theory]] that relates deterministic and nondeterministic space complexity classes. It states that:

> For any function $f(n) \geq \log n$,  
> $$
 \text{NSPACE}(f(n)) \subseteq \text{DSPACE}(f(n)^2).
 $$

In other words, any problem that can be solved by a nondeterministic Turing machine using space $f(n)$ can also be solved by a deterministic Turing machine using space proportional to the square of $f(n)$.


## 0.1 Significance

- This theorem shows that nondeterminism does not provide an exponential advantage in terms of space complexity, unlike time complexity.
- It implies that the class [[PSPACE]] (problems solvable in polynomial space deterministically) is equal to NPSPACE (problems solvable in polynomial space nondeterministically).


## 0.2 Formal statement

If a language $L$ can be decided by a nondeterministic Turing machine using space $f(n)$, then there exists a deterministic Turing machine that decides $L$ using space $O(f(n)^2)$.

---

Savitch’s theorem is a key tool in understanding the power of nondeterminism in space-bounded computations.