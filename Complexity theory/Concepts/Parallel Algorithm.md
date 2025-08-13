---
tags: 
Created: 2025-08-09 14:04
aliases: 
related: 
link: 
Type:
---
A **parallel algorithm** is an algorithm that carries out **multiple computations at the same time** by using more than one processing unit (or “processor”).

## 1 Key idea

- Instead of doing operations **one after another** like in a sequential algorithm, a parallel algorithm **splits the work** into independent tasks and runs them **simultaneously**.
    
- This can reduce the _time complexity_ (wall-clock time), although the **total work** (sum of all operations across processors) might be the same or even larger.
    

## 2 How we model them in theory

In complexity theory, common abstract models are:

- **PRAM** (Parallel Random Access Machine):
    
    - Many processors share a single memory space.
        
    - Processors can read/write memory in parallel (with different rules about conflicts).
        
- **Circuit complexity**:
    
    - A Boolean circuit can be seen as a parallel computation, where each gate operates simultaneously within its layer.
        
    - **Circuit depth** corresponds to the _parallel time_.
        
## 3 Example

### 3.1 Sequential addition of 8 numbers:

```
t1 = a1 + a2
t2 = t1 + a3
t3 = t2 + a4
...
```

Takes O(n)O(n) time with 1 processor.

### 3.2 Parallel addition with 4 processors:

- Step 1: add (a1+a2), (a3+a4), (a5+a6), (a7+a8) in parallel → 4 sums.
    
- Step 2: add the results in parallel → 2 sums.
    
- Step 3: add final 2 results → total sum.
    
- Depth = O(log⁡n)O(\log n) steps (parallel time), even though total work is still O(n)O(n).
    

## 4 Why it comes up in **interactive proofs**
    
- In deIP settings, we often verify computations that _could_ be parallelized — allowing the prover to compute in parallel quickly, and the verifier to check with much less work.
    
- In theory, problems in classes like $\mathsf{NC}$ (“[[Nick’s Class]]”) are exactly those that can be computed by poly-size, polylog-depth circuits → efficiently parallelizable.
    
**In short:**

> A parallel algorithm breaks a problem into independent pieces, computes those pieces at the same time, and combines them — reducing the _time to solution_ when multiple processors are available.

---

If you want, I can also explain **how “parallel algorithm” and “shallow circuit” are essentially equivalent** in complexity theory, which might be exactly why your lecturer mentioned them together. Would you like me to?