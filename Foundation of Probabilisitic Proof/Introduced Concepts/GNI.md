---
tags: 
Created: 2025-08-03 22:28
aliases:
  - Graph Non-isomorphism Problem
related: 
link:
---
## 1 Definition of Graph isomorphism

Given 2 graphs:
$G_0=(V,E_0)$ and $G_1 = (V,E_1)$ on the same vertices $V$, with potentially 2 different edge set $E_0$ and $E_1$.

#DEF Graph isomorphism

We say $G_0$ and $G_1$ are Graph Non-isomorphic (i.e. notated  as $G_0 \equiv G_1$) if there exists permutation:

$\pi : V \to V$ s.t. 

> preserve the edge relation, namely

$\forall (u,v) \in E_0 \iff (\pi(u),\pi(v))\in E_1$

In this case,  we write $G_1 = \pi(G_0)$

## 2 Description of the Problem

### 2.1 Question: How to prove that $G_0 \not\equiv G_1$

Answer : By Interactive Proof

Solution:

Theorem: GNI(Graph Non-isomorphism) $\in$ [[Interactive proof system|IP]] (The set of Languages that have Interactive proofs)

Here are *prover*: $P(G_0,G_1)$ and *verifier* $V(G_0,G_1)$. 
1. The verifier sample 2 objects:
	- The random bit: $b \leftarrow [0,1]$
	- The random permutations: $\pi \leftarrow (\text{permutations on } V)$
	And it will permute the the graph of $G_b$, $$H:=\pi(G_b)$$
	And then verifier send the permuted graph $H$ to Prover
2. The honest prover is going to 
	- choose the bit $\tilde{b}$ such that $H$ is isomorphic or in the so-called equivalent class of $G_\tilde{b}$,  
	- and then sent $\tilde{b}$ to the verifier
3. The verifier accepts if and only if $b = \tilde{b}$


#### 2.1.1 Properties in this case

- Completeness 
	If, indeed , the 2 graphs are not isomorphic, 
		that is $(G_0,G_1) \in GNI$ or we write $G_0 \not\equiv G_1$:
	Then
		All the graphs isomorphic to $G_0$ are in a set, and all the graphs isomorphic to $G_1$ are in another set. (Since the isomorphism relation is an [[Week 6 Stirling number, equivalence class, modulo|equivalence class]], it's reflexive, symmetric and transitive.)
		
	This means:
		The honest prover can figure out which graph is $H$ isomorphic to
- Soundness
	Supposed that theorem is false, that is 
		$(G_0,G_1) \not\in GNI$ or we write $G_0 \equiv G_1$:
	Then 
		the random variable $\pi(G_b)$	 is identical to $\pi(G_{1-b})$
	So 
		$H$ and $b$ are independent no matter which $\tilde{b}$ is sent, $P[\tilde{b} =b] =\frac{1}{2}$ 
	
#### 2.1.2 Conclusion

From the properties statements, we show that:

We can use interactive proofs to show that $G_0 \not \equiv G_1$


> [!NOTE] For now we ignore the prover time 
> Contents

#### 2.1.3 points

1. the GNI problem is not known to be tractable. So generally for Hard Problem, we shouldn't expect an efficient prover , the prover should work at least as hard 

## 3 Theorem: GNI is IP-Complete

This is proved by Shamir in 1992, ["IP = PSPACE"](https://dl.acm.org/doi/pdf/10.1145/146585.146609).