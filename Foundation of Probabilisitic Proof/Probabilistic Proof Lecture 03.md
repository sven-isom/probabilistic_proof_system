---
tags: 
Created: 2025-08-04 17:00
aliases: 
related: 
link: 
Type:
---
## 1 Theorem : PSPACE $\subset$ IP

### 1.1 Similar approach

1. choose complete problem
2. arithmetization
	1. #question is the arithmetization isomorphic to the circuit?
	2. 
3. protocol for the algebraic problem

4. #question  what is the case for $3m$? That is when the $\tilde{p}_j(X_i)$ would have degree of 3m

The case where $\tilde{p}_j(X_i)$ has degree $3m$ typically arises when the polynomial $\tilde{p}_j$ corresponds to the arithmetization of a Boolean formula in **3-CNF form** with $m$ clauses.

Explanation:

- In arithmetization, each clause of a 3-CNF formula contributes a polynomial factor of degree at most 3 (since each clause involves at most 3 literals).
- When you multiply these clause polynomials together to represent the entire formula, the total degree in each variable can grow up to $3m$, where $m$ is the number of clauses.
- Thus, the polynomial $\tilde{p}_j(X_i)$, representing the arithmetized formula or its components at round $j$, can have degree up to $3m$ in the worst case.

So, the degree $3m$ reflects the maximum degree resulting from the product of $m$ clauses, each contributing degree up to 3 in the arithmetized polynomial.


5. #question Why is the probability of intervening ones of pass the check is $\frac{2}{|\mathbb{F}|}$
6. 