---
tags: 
Created: 2025-08-01 07:43
aliases: 
related: 
link:
---
## 1 **Exponential Time Hypothesis

The **Exponential Time Hypothesis (ETH)** for SAT states:

> There is no algorithm that can solve the 3-SAT problem on $n$ variables in time $2^{o(n)}$, i.e., in subexponential time.

In other words, ETH conjectures that any algorithm solving 3-SAT must take at least exponential time in the worst case, and no significantly faster (subexponential) algorithm exists.

This hypothesis is fundamental in computational complexity and is widely used as a basis for proving conditional lower bounds in algorithms and complexity theory.

**Formal statement:**

$$
\nexists \text{ algorithm } A \text{ such that } A \text{ solves 3-SAT in time } 2^{o(n)},
$$

where $n$ is the number of variables.

**Cited paper:**

The ETH was introduced by Impagliazzo and Paturi in their influential paper:

> Impagliazzo, R., & Paturi, R. (2001). *On the complexity of k-SAT*. Journal of Computer and System Sciences, 62(2), 367–375.  
> DOI: 10.1006/jcss.2000.1727

This paper formalizes ETH and explores its implications for the complexity of SAT and related problems.

If you want, I can help you add a summary or more details from the paper.