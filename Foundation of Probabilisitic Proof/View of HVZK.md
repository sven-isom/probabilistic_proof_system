---
tags: 
Created: 2025-08-13 12:54
aliases:
  - View
related: 
link: 
Type: 
Status:
  - unsorted
---
## 1 Definition

The view of an [[Interactive proof system|IP]] on input $x$ is notated as $\text{View}_V(<P,V>(x))$ and defined as:

$$\text{View}_V(<P,V>(x)):= (r,x,a_1,\dots,a_n) $$

Which is all the information **sent by V**:
- The randomness $r$
- Its input $x$
- the prover's msg $a_1,\dots,a_k$

> The HV could have simulated the whole interaction by himself without talking to the honest prover.
> The simulator formalizes this by sampling in polynomial time, the view of the honest verifier.


> [!NOTE] Note
> HVZK is a joint property of honest prover $P$ and honest verifer $V$.



