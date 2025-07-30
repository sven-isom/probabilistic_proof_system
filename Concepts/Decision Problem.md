---
tags: 
Created: 2025-07-30 10:09
aliases: 
related: 
link:
---
## 1 DEF

We often identify the decision problem of $S$ with $S$ itself, and identify $S$ with its **characteristic function** (i.e., with the function $\chi_S : \{0, 1\}^* \to \{0, 1\}$ defined such that $\chi_S(x) = 1$ if and only if $x \in S$). Note that if $f$ solves the search problem of $R$ then the Boolean function $f' : \{0, 1\}^* \to \{0, 1\}$ defined by $f'(x) \stackrel{\text{def}}{=} 1$ if and only if $f(x) \neq \perp$ solves the decision problem of $\{x : R(x) \neq \emptyset\}$.

## 2 Solving a decision problem

> P20 Oded

**Definition 1.2** (solving a decision problem): 

*Let $S \subseteq \{0, 1\}^*$. A function $f : \{0, 1\}^* \to \{0, 1\}$ solves the decision problem of $S$ (or decides membership in $S$) if for every $x$ it holds that $f(x) = 1$ if and only if $x \in S$.*