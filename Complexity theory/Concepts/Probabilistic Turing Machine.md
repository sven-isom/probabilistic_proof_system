---
tags: 
Created: 2025-08-09 11:41
aliases:
  - PTM
related: 
link: 
Type:
---
# Probabilistic Turing machine

## 1 Definition: Probabilistic Turing Machine (PTM)

A **probabilistic Turing machine** is a nondeterministic Turing machine in which **each nondeterministic choice is made according to a fixed probability distribution** — usually uniform.
Formally:
- A PTM has the same components as a deterministic Turing machine (states, tape alphabet, transition function, etc.).
- In each step, instead of having exactly one next move:
    - The machine may have **two or more possible next configurations**.
    - The machine’s _transition function_ includes probabilities (most often each branch has probability $\frac{1}{2}$ if there are two).
- The computation is a **probability distribution over computation paths**.
- The probability that the machine outputs a given result (accept/reject) is the sum of probabilities of all paths leading to that result.
### 1.1 Accept/reject criteria in complexity theory
For decision problems:
- Given input $x$, the PTM **accepts** $x$ with probability $p$ if the sum of probabilities of all accepting computation branches equals $p$.
- Complexity classes like **BPP**, **RP**, **coRP**, and **ZPP** are defined by bounding this probability in certain ways.
## 2 Informal intuition
Think of a PTM as:
- A deterministic Turing machine **with an extra “coin-tossing tape”** that contains random bits.
- Each move can depend on the next random bit(s).
- Every run of the machine corresponds to **one particular sequence of random bits**.
- The output distribution is obtained by averaging over all random bit sequences.
## 3 Examples
### 3.1 **Example 1 — Coin-flip simulator**
A PTM can simulate flipping a fair coin:
- State $q$ reads the next random bit $r$:
    - If $r=0$, go to branch 1.
    - If $r=1$, go to branch 2.
- Each branch has probability 1/2.
This is the basis for all randomized algorithms — e.g., generating random integers, shuffling, etc.
### 3.2 **Example 2 — Miller–Rabin primality test**
- Input: integer $n > 2$.
- Randomly pick $a \in \{2, \dots, n-2\}$ using coin tosses.
- Run modular exponentiation to check if $a$ is a “witness” that $n$ is composite.
- Accept if no witness found, reject if witness found.
- The PTM’s random bits decide which aa to try.
- This runs in polynomial time and has bounded error → $\text{BPP}$ (actually $\text{coRP}$).

### 3.3 **Example 3 — Polynomial identity testing (PIT)**
- Input: arithmetic circuit computing polynomial $p(x_1, \dots, x_n)$.
- PTM picks random values for $x_i$ from a set $\{1,2,\dots, k\}$ using coin tosses.
- Evaluate pp at that point.
- Accept if the value is nonzero, reject otherwise.
- If pp is identically zero, the PTM always rejects (zero error in NO case).  
    If not, it accepts with probability $≥1 - \frac{d}{k}$ by the Schwartz–Zippel lemma.

### 3.4 **Example 4 — Monte Carlo integration**
- Suppose we want to decide if the integral of f(x) over [0,1][0,1] is ≥ 0.6.
- PTM samples mm random points $x$ using random bits.
- It computes the fraction where $f(x) > threshold$.
- Accept if fraction ≥ 0.6 (within tolerance), reject otherwise.

In short:

> A probabilistic Turing machine is just a standard Turing machine **equipped with randomness** — allowing it to “flip coins” and make random choices during computation.  
> Complexity classes like [[BPP]], **RP**, and **ZPP** are defined using PTMs with different acceptance probability requirements.

If you want, I can also give you **the exact formal tuple definition** of a PTM (states, alphabet, transition probability function) as it appears in Goldwasser–Sipser style complexity theory papers. That’s often used in IP and BPP definitions. Would you like me to include that?