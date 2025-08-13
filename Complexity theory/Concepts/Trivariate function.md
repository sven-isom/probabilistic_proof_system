---
tags: 
Created: 2025-08-09 14:50
aliases: 
related: 
link: 
Type:
---
> A **trivariate function** is simply a function of **three variables**.
## 1 Formal definition
If $X, Y, Z$ are sets, a **trivariate function** is:
$$
f: X \times Y \times Z \to W
$$
That is, $f$ takes **three inputs** — one from $X$, one from $Y$, one from $Z$ — and produces an output in $W$.

## 2 Examples
### 2.1 Numeric example
$$
f(x, y, z) = x^2 + y^2 + z^2
$$
Here:
- Domain: $\mathbb{R} \times \mathbb{R} \times \mathbb{R}$
- Codomain: $\mathbb{R}$
### 2.2 Boolean example
$$
g(a, b, c) = (a \land b) \lor (\lnot c)
$$
- Inputs: $a,b,c \in \{0,1\}$
- Output: in $\{0,1\}$

## 3 In circuit/complexity theory context
When your lecturer talks about **trivariate functions**, they might be referring to:
- A gate or subcircuit computing $f(u,v,w)$ from three inputs.
- In polynomial-based protocols (like sumcheck), a trivariate polynomial $g(x,y,z)$ — meaning it has three variables — is just a trivariate function over a field.
Example from sumcheck:
$$
g(x,y,z) = x y + y z + z x
$$
is a trivariate function over $\mathbb{F}_p$.

**In short**:
> “Trivariate” just means “three-variable.” A trivariate function takes three arguments and produces a single output.


If you want, I can show you how **trivariate functions show up in the sumcheck protocol**, since that’s a very likely reason it came up in your lectures. Would you like me to?