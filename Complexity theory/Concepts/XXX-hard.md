---
tags: 
Created: 2025-08-13 15:41
aliases: 
related: 
link: 
Type: 
Status:
  - unsorted
---
An “XXX-hard problem” means a problem that is **at least as hard as every problem in the complexity class XXX**, under some standard type of reduction (often polynomial-time reduction).

Formally:  
A problem BB is **XXX-hard** if

∀A∈XXX,  A≤pB\forall A \in \text{XXX},\; A \leq_p B

where A≤pBA \leq_p B means there exists a polynomial-time computable function ff such that for all inputs xx,

x∈A  ⟺  f(x)∈Bx \in A \iff f(x) \in B

- **If XXX = PSPACE**, “PSPACE-hard” means: every problem in PSPACE can be reduced in polynomial time to it (e.g., **TQBF** is PSPACE-complete).
    
- **If XXX = NP**, “NP-hard” means: every problem in NP can be reduced to it in polynomial time.
    
- **If a problem is both XXX-hard and in XXX**, we call it **XXX-complete**.
    

So:

- **XXX-hard** → “At least as hard as any problem in XXX” (may not belong to XXX itself).
    
- **XXX-complete** → “XXX-hard” **and** “in XXX.”
    
## 1 Example

Let’s take **NP-hard but not NP-complete**.

- **The [[Halting Problem]]** (deciding whether a given program halts on a given input) is **NP-hard** because you can reduce any NP problem to it in polynomial time.
- But it is **not NP-complete** because it’s **not even in NP** — in fact, it’s undecidable, so it’s outside the whole decidable-problems world.

Same pattern works for other classes:

- A **PSPACE-hard** problem that is not PSPACE-complete could be an _undecidable_ problem to which every PSPACE problem reduces. For example, “Given a Turing machine, does it halt with exactly 17 configurations visited?” — suitably encoded — could be made PSPACE-hard but lie outside PSPACE because it’s undecidable.
    

The point:

- **Hard** just means “at least as hard as everything in the class.”
    
- **Complete** means “hard” **and** “in the class.”
    

Do you want me to also give an example of a **PSPACE-hard** but _not_ PSPACE-complete problem from within the decidable problems? That’s a bit trickier but doable.