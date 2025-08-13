---
tags: 
Created: 2025-08-09 12:06
aliases: 
related: 
link: 
Type:
---
# Repetition and taking the majority vote

Repetition and taking the majority vote is one of the most important probability-amplification tricks in randomized algorithms and [[复杂性理论|complexity theory]] (including [[BPP]], [[RP]], and interactive proofs).

## 1 Problem setting

Suppose we have a **[[Randomized algorithm|randomized algorithm]]** $A$ for some [[Decision Problem|decision problem]] such that:

- **If $x \in L$** (YES case):
    $\Pr[ A(x) \ \text{outputs YES} ] \ge p > \tfrac12$

- **If $x \notin L$** (NO case):
	$\Pr[ A(x) \ \text{outputs YES} ] \le q < \tfrac12$

For BPP , we typically have $p = \tfrac23$ and $q = \tfrac13$ .

We want to make the **error probability** _much smaller_, say $\le 2^{-n}$, while still running in polynomial time.

## 2 The method

### 2.1 Step 1 — **Independent repetition**

Run $A$ independently $k$ times on the same input $x$, using fresh random bits each time:
$$A_1(x), A_2(x), \dots, A_k(x)$$

Each run is correct with probability at least $p$ in YES case, at most $q$ in NO case.


### 2.2 Step 2 — **Majority vote**

Let $\text{YES\_count}$ be the number of runs that output YES.

- Output **YES** if:
    $$\text{YES\_count} > \frac{k}{2}$$
- Output **NO** otherwise.

This is the **majority vote rule**.

## 3 Why it works ([[Chernoff Bound|Chernoff bound]] intuition)

- **YES case**:  
    Expected number of $YES’s = p k$, which is strictly more than $k/2$.  
    Chernoff bound ⇒ Probability that the majority is wrong decays **exponentially** in $k$:
    $$\Pr[\text{Majority vote wrong in YES case}] \le e^{-c \cdot k}$$
    
    for some constant $c > 0$.
    
- **NO case**:  
    Expected number of $YES’s = q k$, which is strictly less than $k/2$.  
    Chernoff bound ⇒ Probability that majority flips to YES is also $\le e^{-c' \cdot k}$.
    
By picking $k = O(\log n)$, we can make the error probability $\text{poly}(n)$.  
By picking $k = O(n)$, we can make it $≤ 2^{-n}$.

## 4 Example — [[BPP]] amplification

Original:

- Completeness: $\ge 2/3$
- Soundness: $\le 1/3$
- Gap = 1/3
    

Amplified with k = 9 repetitions:

- YES case: Expected YES count = 6 (out of 9), wrong side of majority requires ≥4 incorrect runs.
- NO case: Expected YES count = 3, wrong side of majority requires ≥5 incorrect runs.
- Using binomial probabilities:
    $\text{Error}\approx 0.052$

Increasing $k$ further drives error to almost zero.


## 5 Where it’s used

- **[[复杂性理论|Complexity theory]]**: To make completeness/soundness error in BPP, [[RP]], coRP, ZPP, and [[Interactive proof system|IP]] protocols arbitrarily small.
- **Cryptography**: To boost success probability in randomized verification steps.
- **Monte Carlo methods**: To reduce variance in randomized estimates.
    
**In short**:

> _Repetition and majority vote_ is the standard error-reduction technique: run the [[Randomized algorithm|randomized algorithm]] multiple independent times, then accept if a majority of runs accept. This exponentially decreases the error probability while keeping the runtime polynomial.


If you want, I can **draw the binomial curve** showing how the probability of wrong majority decays with kk using Chernoff bounds — that’s how textbooks in complexity theory usually present this lemma. Do you want me to prepare that visual?