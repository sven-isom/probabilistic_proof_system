---
tags: 
Created: 2025-07-30 10:28
aliases: 
related: 
link:
---
# BPP

**Definition 6.2** (the class $\mathcal{BPP}$): *A [[Decision Problem|decision problem]] $S$ is in $\mathcal{BPP}$ if there exists a probabilistic polynomial-time algorithm $A$ such that for every $x \in S$ it holds that $\Pr[A(x) = 1] \geq 2/3$ and for every $x \notin S$ it holds that $\Pr[A(x) = 0] \geq 2/3$.*


## 1 Definition of BPP\mathbf{BPP}

BPP stands for **Bounded-Error Probabilistic Polynomial-Time**.

A [[Language|language]] $L \subseteq \{0,1\}^*$ is in **BPP** if there exists a [[Probabilistic Turing Machine]] $M$ running in time polynomial in the input length nn such that:

- (**Completeness**) If $x \in L$:
    $\Pr[M(x) = 1] \ge \tfrac{2}{3}$

- (**Soundness**) If $x \notin L$:
    $\Pr[M(x) = 1] \le \tfrac{1}{3}$

Here:

- The probability is taken over the machine’s internal random coin tosses.
    
- The constants $2/3$ and $1/3$ are **arbitrary** — any constants $>1/2$ and $< 1/2$ will do, because we can amplify the gap by [[Repetition and taking the majority vote]]
    

**Equivalently**:  
BPP\mathbf{BPP} is the class of decision problems solvable in polynomial time by a randomized algorithm whose error probability is bounded away from 1/21/2 for all inputs.

---

## 2 Intuition

Think of BPP algorithms as:

- Efficient (polynomial time),
    
- Allowed to toss fair coins,
    
- Usually right (at least 2/3 of the time),
    
- May be wrong sometimes, but only with small probability.
    

You can make the error probability exponentially small (2−n2^{-n}) by running the algorithm many times and taking the majority.

---

## 3 Examples of problems in BPP

### 3.1 Example 1 — **Primality testing** (historical)

- Before the AKS primality test (2002), the fastest known practical primality tests were randomized (e.g., **Miller–Rabin**).
    
- Miller–Rabin runs in polynomial time and has a one-sided error (if it says “composite,” it’s always right; if it says “prime,” it may be wrong with probability ≤ 1/41/4).
    
- This fits within BPP (actually even in the smaller class RP).
    

---

### 3.2 Example 2 — **Polynomial identity testing** (PIT)

- Given an arithmetic circuit computing a polynomial p(x1,…,xn)p(x_1, \dots, x_n), check whether it’s the zero polynomial.
    
- Deterministic algorithms are not known for general PIT (in polynomial time), but a simple randomized algorithm:
    
    1. Pick random values for x1,…,xnx_1, \dots, x_n from a large enough set.
        
    2. Evaluate pp at this point.
        
    3. If it’s nonzero, output “not identically zero,” else output “zero.”
        
- By the Schwartz–Zippel lemma, if pp is not the zero polynomial, the probability of mistakenly outputting “zero” is small.
    

---

### 3.3 Example 3 — **Monte Carlo approximation of counting problems**

- Suppose you want to estimate the size of a huge set S⊆{0,1}nS \subseteq \{0,1\}^n defined by some predicate.
    
- You can sample uniformly from the domain, check the predicate, and use the fraction of successes to estimate ∣S∣|S|.
    
- If the predicate can be evaluated in polynomial time, this falls into BPP.
    

---

## 4 Quick hierarchy note

We have:

P⊆BPP⊆P#P\mathbf{P} \subseteq \mathbf{BPP} \subseteq \mathbf{P^{\#P}}

And it is widely believed that P=BPP\mathbf{P} = \mathbf{BPP}, because most natural randomized algorithms are thought to have deterministic polynomial-time equivalents (derandomization conjecture).

---

If you’d like, I can also give **a visual example of how the 2/3 vs 1/3 gap is amplified** to exponentially small error — this is the core trick used in both BPP and interactive proofs. Would you like me to do that?