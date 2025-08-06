---
tags: 
Created: 2025-08-04 17:05
aliases:
  - quantified boolean formula
related: 
link: 
Type:
---
## 1 DEF of QBF(quantified boolean formula)

A fully quantified boolean formula is a logical expression such as  
$$
\forall x_1 \exists x_2 \exists x_3 \quad (x_1 \land x_2) \lor x_3,
$$
or  
$$
\forall x_1 \exists x_2 \forall x_3 \quad (x_1 \land x_2) \lor x_3.
$$  
(every variable is quantified via $\forall$ or $\exists$)  

The expression evaluates to true or false.  
Let us evaluate the examples:

1) TRUE  
$$
\begin{array}{c}
x_1 = 0 \\
\quad \xrightarrow{x_2=0} \quad x_3=1 \quad (0 \land 1) \lor 1 = 1 \\
\quad \xrightarrow{x_2=1} \quad x_3=1 \quad (1 \land 1) \lor 1 = 1
\end{array}
$$

2) FALSE  

$$\begin{array}{c}
x_1 = 0 \\
\quad \xrightarrow{x_2=0} \quad x_3=0 \quad (0 \land 0) \lor 0 = 0 \\
\quad \xrightarrow{x_2=0} \quad x_3=1 \quad (0 \land 0) \lor 1 = 1 \\
\quad \xrightarrow{x_2=1} \quad x_3=0 \quad (1 \land 1) \lor 0 = 1 \\
\quad \xrightarrow{x_2=1} \quad x_3=1 \quad (1 \land 1) \lor 1 = 1
\end{array}$$

## 2 Relationship with NP and coNP

### 2.1 NP
$$
NP \sim \{\varphi \mid \exists x_1 \exists x_2 \ldots \exists x_n, \varphi(x_1, \ldots, x_n) = 1 \}
$$  
### 2.2 coNP
$$
coNP \sim \{\varphi \mid \forall x_1 \forall x_2 \ldots \forall x_n, \varphi(x_1, \ldots, x_n) = 1 \}
$$

## 3 TQBF

### 3.1 Definition

$$
TQBF = \{ \varphi(x_1, \ldots, x_n) \mid \forall x_1 \exists x_2 \forall x_3 \ldots \varphi(x_1, \ldots, x_n) = 1 \}
$$

### 3.2 TQBF related to PSPACE

> TQBF is PSPACE-Complete