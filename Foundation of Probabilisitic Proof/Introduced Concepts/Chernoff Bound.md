---
tags: 
Created: 2025-08-08 21:25
aliases: 
related: 
link: 
Type:
---
## 1 Notes

The **Chernoff Bound** is a powerful concentration inequality that provides exponentially decreasing bounds on the probability that the sum of independent random variables deviates significantly from its expected value.

### 1.1 Formal statement (simplified):

Let $X_1, X_2, \ldots, X_n$ be independent Bernoulli random variables (taking values 0 or 1), and let

$$
X = \sum_{i=1}^n X_i,
$$

with expected value

$$
\mu = \mathbb{E}[X] = \sum_{i=1}^n \mathbb{E}[X_i].
$$

Then, for any $0 < \delta < 1$,

$$
\Pr[X \geq (1 + \delta) \mu] \leq \exp\left(-\frac{\delta^2 \mu}{3}\right),
$$

and

$$
\Pr[X \leq (1 - \delta) \mu] \leq \exp\left(-\frac{\delta^2 \mu}{2}\right).
$$

---

### 1.2 Intuition:

- The Chernoff Bound shows that the probability of large deviations from the mean decreases exponentially with the size of the deviation and the expected value.
- It is much stronger than Markov's or Chebyshev's inequalities for sums of independent random variables.

---

### 1.3 Applications:

- Used extensively in randomized algorithms and probabilistic proofs to guarantee that random sampling behaves close to expectation with high probability.
- Helps in analyzing error probabilities and confidence levels in probabilistic methods.

---

### 1.4 Summary:

The Chernoff Bound provides tight, exponentially small upper bounds on the probability that the sum of independent random variables deviates significantly from its expected value, making it a fundamental tool in probabilistic analysis.