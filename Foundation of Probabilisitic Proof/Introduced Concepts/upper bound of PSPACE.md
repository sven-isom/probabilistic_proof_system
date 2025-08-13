---
tags: 
Created: 2025-08-08 18:48
aliases: 
related: 
link: 
Type:
---
## 1 Why `val(T)` can be evaluated in **polynomial space** though it may take **exponential time**

### 1.1 The input size and the tree size  

**Input size**
* Let $n = |x|$ be the length of the instance fed to the protocol.  
* The protocol has at most $p(n)$ rounds and each message / coin string is at most $p(n)$ bits for some fixed polynomial $p$.  

**Tree size**
* Therefore the **height** of the [[Game Tree|game tree]] $T$ is $O(p(n))$, but the **number of leaves** can be as large as  
  $$
  2^{\,p(n)} ,
  $$  
  because each verifier-random layer branches on every possible sequence of coin flips.


### 1.2 How the value `val(T)` is defined  

Defined in [[Probabilistic Proof Lecture 05]], check [[Game Tree]]

### 1.3 Why polynomial space: depth-first algorithm  深度优先算法

We can traverse $T$ **depth-first**:

1. **Recurse** to a child until a leaf is reached.  
2. **Return** the leaf’s value up one level; combine according to the rule (max or average).  
3. **Backtrack** to process the next child, and so on.

Key observation: at any moment we only need to store

* the current path (depth $O(p(n))$);  
* a running aggregate (e.g., current maximum or partial sum) for at most one parent node.

Both require **space $O(p(n))$**, i.e. polynomial in $n$.  
No part of the algorithm ever needs to keep *all* children or *all* subresults simultaneously.

### 1.4 Why the running time is exponential  

Although we reuse space, we must **visit every leaf** to compute exact averages and maxima.  
With up to $2^{p(n)}$ leaves, the worst-case running time is

$$
\exp\bigl(p(n)\bigr) = 2^{\Theta(p(n))},
$$

which the lecturer described informally as **exp(poly($n$))**.

### 1.5 Complexity-theoretic viewpoint  

Evaluating such a min–max tree is equivalent to deciding a fully quantified Boolean formula whose quantifier block alternates $\forall/\exists$ on $p(n)$ variables.  
That task is complete for **PSPACE**.  

[[Savitch’s theorem]] tells us that PSPACE ⊆ EXPTIME, mirroring the “poly-space, exp-time” statement made in the lecture.

---

**Bottom line:**  
We cannot avoid touching exponentially many leaves, hence the exponential time, but by processing them one branch at a time we never need more than a polynomial-sized working tape.