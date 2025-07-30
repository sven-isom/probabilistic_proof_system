---
tags: 
Created: 2025-07-30 09:58
aliases: 
related: 
link:
---
## 1 Definition

> Oded P52

**Definition 2.5** (efficiently verifiable proof systems):

- *A [[Decision Problem|decision problem]] $S \subseteq \{0, 1\}^*$ has an efficiently verifiable proof system if there exists a polynomial $p$ and a polynomial-time (verification) algorithm $V$ such that the following two conditions hold:*
  1. Completeness: *For every $x \in S$, there exists $y$ of length at most $p(|x|)$ such that $V(x, y) = 1$.*
     
     (Such a string $y$ is called an NP-witness for $x \in S$.)
  2. Soundness: *For every $x \notin S$ and every $y$, it holds that $V(x, y) = 0$.*

*Thus, $x \in S$ if and only if there exists $y$ of length at most $p(|x|)$ such that $V(x, y) = 1$.*

*In such a case, we say that $S$ has an NP-proof system, and refer to $V$ as its verification procedure (or as the proof system itself).*

- *We denote by $\mathcal{NP}$ the class of decision problems that have efficiently verifiable proof systems.*

We note that the term *NP-witness* is commonly used. In some cases, $V$ (or the set of pairs accepted by $V$) is called a witness relation of $S$. We stress that the same set $S$ may have many different NP-proof systems (see Exercise 2.2), and that in some cases the difference is not artificial (see Exercise 2.3).