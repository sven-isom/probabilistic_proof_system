---
tags: 
Created: 2025-08-03 00:23
aliases: 
related: 
link: 
Type:
  - Note
---
## 1 [[Interactive proof system|Interactive proof]]s for counting problems

> 1. [[GNI]] is a problem in [[coNP]] not known to be in P. Yet, GNI is **not** believed to be [[coNP-complete]].
> 	Otherwise, PH collapses to 2nd level.

## 2 Theorem: UNSAT $\in$ IP, so coNP $\in$ IP

## 3 Theorem: [[Sharp-SAT Problem|Sharp-SAT]] $\in$ IP, so $P^{\#P}$ $\in$ IP

## 4 Some result from complexity theorem

![[Pasted image 20250803225035.png]]

1. Many [[Language|language]]s beyond NP!
2. The interactive proof for GNI leveraged properties of graph isomorphisms, but [[UNSAT]] and [[Sharp-SAT Problem|Sharp-SAT]] do not seem to have similar properties.

Thus (we can not permute on a circuit ), 2 new ideas are introduced here:
- Arithmetization
- [[sumcheck protocol|Sumcheck Protocol]]

## 5 [[Arithmetization of a Boolean Formula]]

## 6 sumcheck protocol

See [[sumcheck protocol]] 

## 7 Interactive Proof for UNSAT

1. #quetsion What does it mean by saying  a prime number $p < poly(n,m)$ ? 
	Saying a prime number $p < \text{poly}(n,m)$ means that the prime number $p$ is bounded above by some polynomial function in the variables $n$ and $m$. 

	More concretely, there exists a polynomial $f(n,m)$ such that:
	$$
	p < f(n,m)
	$$

	where $f(n,m)$ grows at most like $(n + m)^k$ for some constant $k$.

	This is often used in complexity theory to indicate that the size of the prime $p$ (for example, the number of bits needed to represent $p$) is polynomially bounded in the input size parameters $n$ and $m$, ensuring that operations modulo $p$ can be done efficiently within polynomial time.

2. #question What does it mean by saying  a prime number $p < 2^{poly(n,m)}$ ? 
 

3. The advantage of the sumcheck protocol
	- The sumcheck protocol provides you the advantage based on how many variable you have in the arithmetization polynomial.
	- The number of variables determined the $n$ here.

## 8 Arithmetization for Sharp-SAT

1. #question Why use different arithmetization here?
	The new arithmetization has a minor **disadvantage** which is now $x \lor y = x+y-xy$ actually increase the degree.
2. #question Why dont we need $3^n$ in this new arithmetization
	Since the change of the arithmetization, the largest number we can obtain from the circuit is now 2 rather than 3. This is the case where all the assignments are true.
	
3. #question Still confused that how could the prime $q$ be greater than $2^n$ since the verifier computes in polynomial time? 