---
tags: 
Created: 2025-08-01 00:45
aliases: 
related: 
link:
---
> Introduce in Chapter 2.4.1

## 1 Definition
**Definition 2.29** (search problems with a **promise**):  
A search problem with a **promise** consists of a binary relation $R \subseteq \{0,1\}^* \times \{0,1\}^*$ and a **promise** set $P$. Such a problem is also referred to as the search problem $R$ with **promise** $P$.

- The search problem $R$ with **promise** $P$ is solved by algorithm $A$ if for every $x \in P$ it holds that $(x, A(x)) \in R$ if $x \in S_R = \{x : R(x) \neq \emptyset\}$ and $A(x) = \perp$ otherwise, where $R(x) = \{y : (x,y) \in R\}$.  
  The time complexity of $A$ on inputs in $P$ *is defined* as  
  $$
  T_{A|P}(n)^{\text{def}} = \max_{x \in P \cap \{0,1\}^n} \{ t_A(x) \},
  $$  
  where $t_A(x)$ is the running time of $A(x)$ and $T_{A|P}(n) = 0$ if $P \cap \{0,1\}^n = \emptyset$.

- The search problem $R$ with **promise** $P$ is in the **promise** problem extension of $\mathsf{PF}$ if there exists a polynomial-time algorithm that solves *this problem*.

- The search problem $R$ with **promise** $P$ is in the **promise** problem extension of $\mathsf{PC}$ if there exists a polynomial $T$ and an algorithm $A$ such that, for every $x \in P$ and $y \in \{0,1\}^*$, algorithm $A$ makes at most $T(|x|)$ steps and it holds that $A(x,y) = 1$ if and only if $(x,y) \in R$.