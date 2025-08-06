---
tags: 
Created: 2025-07-22T17:50:00
aliases: 
related: 
link:
---

## 1 Claims

### 1.1 Mathematical Proofs = NP 

#### 1.1.1 DEF of NP

A [[Language|language]] $L \in NP \iff \exists \text{ polynomial-time decider }D$ such that:
1. $\forall x \in L, \exists \text{witness w}$ , $D(x,w)=1$
2. $\forall x \not\in L, \forall \text{witness w}$ , $D(x,w)=0$

#### 1.1.2 Example: L =[[SAT]]

- $x$: is a boolean formula $\phi(x_1,\dots,x_n)$
- $w$: is an assignment $(a_1,...,a_n) \in \{0,1\}^n$
- D: checks that $\phi(a_1,\dots,_n)$ is true.

#### 1.1.3 The way we look Mathematical proofs

- See the instance as theorem
- See the witness as proof $\pi$
- See the decider $D$ as verifier $V$ with accept case $V(x,\pi)=1$ 

- Completeness
	-  $\forall \text{theorem} \in L, \exists \text{proof w}$ , $V(x,w)=1$
- Soundness
	-  $\forall \text{theorem} \not\in L, \forall \text{proof w}$ , $V(x,w)=0$


> [!Conclusion] NP captures classical mathematical proofs
> 1. I thought these mathematic proofs are related to the deterministic proofs
> 

### 1.2 Revolutionary idea

The verifier V may:
- Use randomness
- interact with P

## 2 Interactive Proof

[[Interactive proof system]] 

### 2.1 Relationships with NP

randomness

|     | Y                            | N   |
| --- | ---------------------------- | --- |
| Y   | [[Interactive proof system]] | MA  |
| N   | NP                           | NP  |

*believed to equal NP (it does if strong PRGs exist)*

> [!NOTE] MA stands 
> In [[复杂性理论|complexity theory]], **MA** stands for **Merlin-Arthur**. It is a complexity class representing a type of interactive proof system where:
>- **Merlin** (an untrusted prover) sends a proof or certificate to 
> - **Arthur** (a randomized polynomial-time verifier) who uses randomness to verify the proof with some bounded error probability.
> MA can be seen as a probabilistic analogue of NP, where the verifier is allowed to use randomness but only receives a single message from the prover.

## 3 Example : [[Interactive proof system|IP]] for [[GNI|Graph Non-isomorphism Problem]]

## 4 An Upper Bound on IP

### 4.1 related theorem 

IP $\subseteq$ [[PSpace|PSPACE]] 

Let L $\in$ IP, and let $(P,V)$ be an IP for L,
We need to show that L $\in$  PSPACE

Fix an instance $x$ and define $$
q_x := \max_{\tilde{P}} \Pr_r \left[ \langle \tilde{P}, V(x) \rangle = 1 \right].
$$
- $\max_p$: this means the maximum over all possible prover $\tilde{p}$ （or we say prover strategies）
- $Pr$ : means the probability that the verifier accepts when interacting with the *prover strategy* $\tilde{p}$ on input $x$ #todo 
	- over the randomness $r$ 
	- used by the verifier $V$   

- $q_x$ : The maximum convincing probability of the verifier 

The conditions of completeness and soundness say that :
- if $x \in L$, then $q_x =1$ 
- if $x \not\in L$, then $q_x \leq \frac{1}{2}$ 

> Thus, it suffices to compute $q_x$ in polynomial space.

**Problem** on $$\max_{\tilde{p}}$$
When you have this iteration over all provers, we can't  expect to iterate over all provers because this includes provers that require large space to simulate.

> Coz in IP, some prover might have significant larger power which means they are using more than polynomial space to compute his proof.
 
No we reduce the problem to a computation, and we have a handle

### **Idea**
Any transcript has polynomial size (the verifier reads it), so we can afford to iterate over all transcripts in polyspace.

That is the OPTIMAL Prover strategy is computable in polyspace, and so is the probability $q_x$

 **This is true because:**

- In an interactive proof system, the **transcript** (the entire conversation between the prover and verifier) has **polynomial size** with respect to the input size. This is because the **verifier** runs in polynomial time and can only read a polynomial amount of information.

- Since the transcript is polynomially bounded, we can **enumerate all possible transcripts** using only **polynomial space**. We don't need to store all transcripts at once; we can generate and check them one by one using polynomial space.

- The prover’s strategy can be viewed as a function that, given the verifier’s messages so far, decides the next message. Because the transcript is polynomially bounded, the prover’s optimal strategy can be computed by searching over all possible transcripts in polynomial space.

- Therefore, the **optimal prover strategy** (the one that maximizes the verifier’s acceptance probability) is **computable in polynomial space**.

- Consequently, the maximum acceptance probability $q_x$ can also be computed in polynomial space by iterating over all transcripts and choosing the best prover responses.

A partial transcript is a tuple $(a_1,b_1,a_2,b_2,\dots,a_i,b_i)$.
Here $a_i,b_i$ is the information in round $i$.

Now, **define** a function $p^*(x,(a_1,b_1,a_2,b_2,\dots,a_i,b_i))$ output $a_{i+1}$ that maximizes convincing probability conditioned on interaction so far being $tr=(a_1,b_1,\dots,a_i,b_i)$

### **Claim**

$p^* \in \text{PSPACE} \to q_x \in \text{PSPACE}$ . That is computing the theorem above is sufficient for the final goal.

- $p^*$ is a function, $\text{PSPACE}$ is a set of Language, $p^* \in \text{PSPACE}$ indicates that $p^*$ is computable in $\text{ PSPACE}$ .

### **Proof** 
Since $p^*$ is optimal, we have the maximum acceptance probability as a ratio 
	$$q_x = \frac{{\sum_{r\in R}d(x,r)}}{|R|}$$ 
where $d(x,r)$ is the *decision* of $V(x;r)$ using randomness $R$ when interacting with $p^*$

- $r\in R$: All possible random strings , this is in Polynomial space #question 
	- This is true since the verifier $V$ runs in polynomial time, so the length of each random string  it uses is polynomial in the input size.
- For each random string, we're going to look at the bit, which is called $d$ for decision
	- This bit is the *decision* of $V$ 
-  The right side represents the fractions of yes. 



For any fixed $r$, $d(x,r)$ is computable in polynomial space:
- $a_1^* = p^*(x,\perp)$
- $b_1 = V(x,r,a_1^*)$
- $a_2^* = p^*(x,(a_1^*,b_1))$
- $b_2 = V(x,r,a_1^*,a_2^*)$
- ...
- $a_k^* = p^*(x,(a_1^*,b_1,\dots,a_{k-1}^*,b_{k-1}))$
- $b_k = V(x,r,a_1^*,\dots,a_{k}^*)$


Now **claim** that : $$p^* \in \text{PSPACE}$$
### **Proof**
Let $tr = (a_1,b_1,\dots,a_i,b_i)$ be a transcript of  $i$ rounds. And let $R[x,tr]$ be the set of a random strings $r$ consistent with $(x,tr)$:
- $b_1=V(x,r,a_1)$,
- $b_2=V(x,r,a_1,a_2)$
- ...
- $b_i=V(x,r,a_1,a_2,\dots,a_i)$

Proof is by induction on $i$:

- Base case is $i=k-1$, 
	- where $k$ is the total number of rounds
	$$p^*(x, tr) = \arg\max_{a_k}  \mathbb{E}_{r \in R[x, tr]} \left[ V(x, r, a_1, \ldots, a_{k-1}, a_k) \right]$$
	- We can iterate over all messages $a_k$ and randomness $r$ in polyspace.
- Inductive case is $i< k-1$ (Assuming $p^* \in \text{PSPACE}$ for $|tr|>i$):
	$$p^*(x, tr) = \arg\max_{a_{i+1}}  \mathbb{E}_{r \in R[x, tr]} \left[ V(x, r, a_1, \ldots, a_{i},a_{i+1},a_{i+2}^*,\dots, a_k^*) \right]$$
	where $a_{i+2}^*, \dots, a_k^*$ are optimal prover messages for $(x, tr, r, a_{i+1})$:

$$
\begin{align*}
b_{i+1} &= V(x, r, a_1, \dots, a_i, a_{i+1})\\
a_{i+2}^* &= p^*(x, (a_1, b_1, \dots, a_i, b_i, a_{i+1}, b_{i+1}))\\
b_{i+2} &= V(x, r, a_1, \dots, a_i, a_{i+1}, a_{i+2}^*)\\
&\vdots\\
a_k^* &= p^*(x, (a_1, b_1, \dots, a_{i}, b_i, a_{i+1}, b_{i+1}, a_{i+2}^*, b_{i+2}, \dots, a_{k-1}^*, b_{k-1}))\\
\end{align*}\\
$$
> $p^*$ on transcripts longer than $i$ rounds

Each of the above is computable in polyspace, given $(x, tr, r, a_{i+1})$.  
We can iterate over all messages $a_{i+1}$ and randomness $r$.
We deduce that $p^*$ is computable in polynomial space.

> The key idea here is using the max-optimal, max-optimal strategy to prove it in polynomial space . 
> **The game is a tree of polynomial depth (polynomial round) with polynomial fan out(number of child nodes).**