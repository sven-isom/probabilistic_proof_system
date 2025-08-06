---
tags: 
Created: 2025-08-06 12:31
aliases: 
related: 
link: 
Type:
---
## 1 Definition of RNC (Randomized Nick’s Class)

In complexity theory, **RNC** is the class of decision problems that can be solved by a **randomized parallel algorithm** running in polylogarithmic time using a polynomial number of processors.

More precisely:

- The algorithm runs in time $(\log n)^k$ for some constant $k$ (polylogarithmic time).
- It uses a polynomial number of processors (parallelism).
- It is a randomized algorithm with bounded error probability (usually one-sided or two-sided error).
- The class RNC is the randomized analogue of the class NC (Nick’s Class), which consists of problems solvable in polylogarithmic time on a parallel computer with polynomial processors but without randomness.

---

### 1.1 Summary:

- **RNC** = problems solvable efficiently in parallel with randomness.
- Runs in **polylogarithmic time** on a parallel machine.
- Uses **polynomially many processors**.
- Has **bounded error probability**.

RNC captures efficient parallel algorithms that leverage randomness to solve problems faster than known deterministic parallel algorithms.