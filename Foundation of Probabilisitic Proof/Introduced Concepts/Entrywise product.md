---
tags: 
Created: 2025-08-11 14:02
aliases:
  - Hadamard product
related: 
link: 
Type: 
Status:
  - unsorted
---
The **entrywise product** (also called the **Hadamard product**) is when you multiply two matrices or vectors of the same shape **component by component**, instead of using matrix multiplication.

---

### 0.1 Definition

If AA and BB are two matrices (or vectors) of the same dimensions, their entrywise product is:

$(A \circ B)_{ij} = A_{ij} \cdot B_{ij}$

Here “∘\circ” is a common symbol for entrywise product.

---

### 0.2 Example

For vectors:

a=(2,3,4),b=(5,6,7)a = (2, 3, 4), \quad b = (5, 6, 7) a∘b=(2⋅5,  3⋅6,  4⋅7)=(10,18,28)a \circ b = (2\cdot 5, \; 3\cdot 6, \; 4\cdot 7) = (10, 18, 28)

For matrices:

A=(1234),B=(5678)A = \begin{pmatrix} 1 & 2 \\ 3 & 4 \end{pmatrix}, \quad B = \begin{pmatrix} 5 & 6 \\ 7 & 8 \end{pmatrix} A∘B=(1⋅52⋅63⋅74⋅8)=(5122132)A \circ B = \begin{pmatrix} 1\cdot 5 & 2\cdot 6 \\ 3\cdot 7 & 4\cdot 8 \end{pmatrix} = \begin{pmatrix} 5 & 12 \\ 21 & 32 \end{pmatrix}

---

### 0.3 Where it shows up

- In **algebraic proof systems**, entrywise products of coefficient arrays or indicator vectors appear when checking consistency of assignments to polynomial constraints.
    
- In **signal processing** and **machine learning**, it's used for elementwise scaling or masking.
    
- In **probability**, multiplying indicator vectors entrywise corresponds to taking intersection of events (in 0–1 form).
    

---

If you want, I can also explain how **entrywise product** connects to your lecturer’s remark about “linear in the monomials xixjx_i x_j” — because those xixjx_i x_j terms can be represented as an entrywise product of two vectors of variables. Would you like me to do that?