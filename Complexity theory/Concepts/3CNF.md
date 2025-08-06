---
tags: 
Created: 2025-08-04 21:44
aliases: 
related: 
link: 
Type:
---
## Definition of 3-CNF

A Boolean formula is in **3-CNF (3-Conjunctive Normal Form)** if it is a conjunction (AND, denoted by $\land$) of clauses, where each clause is a disjunction (OR, denoted by $\lor$) of exactly three literals. A **literal** is either a Boolean variable or its negation.

Formally, a 3-CNF formula $\varphi$ over variables $x_1, x_2, \ldots, x_n$ has the form:

$$
\varphi = C_1 \land C_2 \land \cdots \land C_m,
$$

where each clause $C_i$ is:

$$
C_i = (\ell_{i1} \lor \ell_{i2} \lor \ell_{i3}),
$$

and each literal $\ell_{ij}$ is either $x_k$ or $\neg x_k$ for some variable $x_k$.

---

## Examples of 3-CNF formulas

### Example 1:

$$
(x_1 \lor \neg x_2 \lor x_3) \land (\neg x_1 \lor x_2 \lor x_4)
$$

- Two clauses ($m=2$).
- Each clause has exactly 3 literals.

### Example 2:

$$
(x_1 \lor x_2 \lor x_3) \land (\neg x_2 \lor x_4 \lor \neg x_5) \land (x_3 \lor \neg x_4 \lor x_6)
$$

- Three clauses ($m=3$).
- Each clause has exactly 3 literals.

### Example 3:

$$
(x_1 \lor \neg x_2 \lor x_3) \land (x_2 \lor x_4 \lor \neg x_5) \land (\neg x_1 \lor x_3 \lor x_6) \land (x_4 \lor \neg x_5 \lor \neg x_6)
$$

- Four clauses ($m=4$).
- Each clause has exactly 3 literals.

---

These formulas are widely used in computational complexity, especially in the study of SAT problems and their arithmetization in interactive proofs.