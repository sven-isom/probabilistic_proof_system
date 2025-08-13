---
tags: 
Created: 2025-08-11 11:11
aliases: 
related: 
link: 
Type: 
Status:
  - unsorted
---
## 1 Questions

#question 
1. Again, Does every complexity class have a complete problem?

---
Question

What does the lecturer mean by: They are not linear polynomials while thery are linear in the monimials x_i times x_j

Answer

What your lecturer means can be unpacked like this:

 1. "They are not linear polynomials"

A **linear polynomial** means a polynomial where each term is degree ≤ 1 in the variables — e.g.

a1x1+a2x2+⋯+anxn+ca_1 x_1 + a_2 x_2 + \cdots + a_n x_n + c

No products of variables appear.  
So something like

x1x2+x3x_1 x_2 + x_3

is **not** linear in the variables x1,x2,x3x_1, x_2, x_3 — because x1x2x_1 x_2 is a degree-2 term.

 2. "They are linear in the monomials xi×xjx_i \times x_j"

If you _treat_ each product xixjx_i x_j as a **single new variable** (a monomial), say:

yij:=xixjy_{ij} := x_i x_j

then the same polynomial might look _linear_ in the yijy_{ij}.

Example:  
Suppose you have

f(x1,x2,x3)=3x1x2+2x2x3+7x1x1f(x_1, x_2, x_3) = 3 x_1 x_2 + 2 x_2 x_3 + 7 x_1 x_1

This is **quadratic** in xx, but if we introduce:

y12=x1x2,y23=x2x3,y11=x1x1y_{12} = x_1 x_2, \quad y_{23} = x_2 x_3, \quad y_{11} = x_1 x_1

then:

f=3y12+2y23+7y11f = 3 y_{12} + 2 y_{23} + 7 y_{11}

— which is linear in the yy-variables.

 3. Why this matters

This viewpoint is common in:

- **Quadratic Equation SAT (QESAT)** and algebraic proof systems:  
    Quadratic constraints can be represented as _linear_ constraints over a larger set of variables (the monomials).
    
- **Sum-check protocols**:  
    When verifying polynomial identities, treating monomials as independent variables can simplify certain arguments.
    
- **Tensor representation**:  
    The coefficient structure of quadratic terms can be stored in a **matrix or tensor** indexed by i,ji, j.

---
#question 
Is $M,c$ Prover local stored?


---
#question 

Still confused on how $l\log|\mathbb{F}|$ makes $m$ small enough.
