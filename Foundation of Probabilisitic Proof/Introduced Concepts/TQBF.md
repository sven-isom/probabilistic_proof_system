---
tags: 
Created: 2025-08-04 17:05
aliases:
  - True Quantified Boolean Formula
related: 
link: 
Type:
---
## 1 Notes

## 2 Definition of TQBF (True Quantified Boolean Formula)

A **True Quantified Boolean Formula (TQBF)** is a fully quantified Boolean formula that evaluates to true. It is a Boolean formula where every variable is quantified by either a universal quantifier ($\forall$) or an existential quantifier ($\exists$), and the formula evaluates to true under these quantifications.

Formally, a TQBF has the form:

$$
Q_1 x_1 \; Q_2 x_2 \; \cdots \; Q_n x_n \; \varphi(x_1, x_2, \ldots, x_n),
$$

where each $Q_i$ is either $\forall$ or $\exists$, and $\varphi$ is a Boolean formula over variables $x_1, \ldots, x_n$. The formula is **true** if the quantified expression evaluates to true.

---

## 3 Example of TQBF

Consider the formula:

$$
\forall x_1 \exists x_2 \forall x_3 \quad (x_1 \land x_2) \lor x_3.
$$

- Here, $x_1$ is universally quantified.
- $x_2$ is existentially quantified.
- $x_3$ is universally quantified.
- The formula evaluates to true if for every $x_1$, there exists an $x_2$ such that for every $x_3$, the expression $(x_1 \land x_2) \lor x_3$ is true.

---

## 4 Notes

- TQBF is a canonical **PSPACE-complete** problem.
- It generalizes SAT by allowing alternating quantifiers.
- Deciding TQBF is more complex than SAT due to the quantifier alternations.

This concept is fundamental in complexity theory and interactive proof systems.