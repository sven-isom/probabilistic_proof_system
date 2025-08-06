---
tags: 
Created: 2025-08-06 12:31
aliases: 
related: 
link: 
Type:
---
## 1 Definition of RP (Randomized Polynomial time)

In [[复杂性理论|complexity theory]], **RP** (Randomized Polynomial time) is the class of [[Decision Problem|decision problem]]s for which there exists a [[Randomized algorithm|randomized algorithm]] (a [[Probabilistic Proof Lecture 04|probabilistic]] [[Turing Machine|Turing machine]]) that runs in polynomial time and satisfies the following conditions:

- If the answer is **NO**, the algorithm always returns NO (no false positives).
- If the answer is **YES**, the algorithm returns YES with probability at least 1/2 (or any fixed constant greater than 0), and NO with some probability less than 1/2.

In other words, RP algorithms have one-sided error: they never incorrectly accept a NO instance, but may incorrectly reject a YES instance with bounded probability.

---

### 1.1 Summary:

- **YES instances:** accepted with probability ≥ 1/2.
- **NO instances:** always rejected.
- Runs in polynomial time.

RP is a fundamental class in randomized complexity theory, capturing problems efficiently solvable with randomness and one-sided error.