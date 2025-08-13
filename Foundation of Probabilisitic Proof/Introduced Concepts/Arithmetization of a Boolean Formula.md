---
tags: 
Created: 2025-08-03 22:59
aliases: 
related: 
link: 
Type:
---
## 1 What is Arithmetization of a Boolean Formula

A boolean formula $\phi(x_1, \ldots, x_n)$ is a tree where:
- every leaf node is labeled by a variable $x_i$;
- every internal node is a logical operator on its children $(\lor, \land, \neg)$.
![[Pasted image 20250803230559.png]]

Arithmetization replaces each logical operator with an arithmetic operator:
- $\neg x \mapsto 1 - x$
- $x \land y \mapsto x \cdot y$
- $x \lor y \mapsto x + y$

Thus a boolean formula $\phi(x_1, \ldots, x_n)$ is mapped to a polynomial $p(x_1, \ldots, x_n)$ such that $\deg_{\text{tot}}(p) \leq |\phi|$,

evaluating $p$ at a point takes $|\phi|$ operations, and:

### 1.1 claim
- If $\phi \in \text{UNSAT} \implies \sum_{a_1, \ldots, a_n \in \{0,1\}} p(a_1, \ldots, a_n) = 0$  
- If $\phi \notin \text{UNSAT} \implies 0 < \sum_{a_1, \ldots, a_n \in \{0,1\}} p(a_1, \ldots, a_n) \leq 2^n \cdot 3^m$  
  (let's assume $\phi$ is 3CNF)

### 1.2 corollary

For all prime $q > 2^n 3^m$,

$$
\phi \in \text{UNSAT} \iff \sum_{a_1, \ldots, a_n \in \{0,1\}} p(a_1, \ldots, a_n) = 0 \mod q
$$

## 2 Why do we do the Arithmetization


The Corollary tell us that, if we start working over a [[prime field]], where the prime is large enough, that is large than $2^n3^m$ 

Then
	I have encoded the unsatisfiability of the formula into the zeroness of this sum over this field. 
	
> We started with a problem about Boolean logic. And we ended up with an arithmetic condition about a low degree polynomial that we can evaluate at any location efficiently.

And by the Corollary, we encoded the unsatisfiability of a formula into a sumcheck problem.