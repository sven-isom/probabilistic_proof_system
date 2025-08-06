---
tags: 
Created: 2025-08-05 11:36
aliases: 
related: 
link: 
Type:
---
## 1 Outlines

1. private coins vs public coins
2. definition of $AM[k]$ and $MA[k]$
3. [[GNI]] is contained in $AM[2]$
    - reduction to approximate counting
    - approximate counting via pairwise-independent hashing
4. $IP[k]$ is contained in $AM[k+2]$
    - high-level intuition only

### 1.1 Related Reading Material
- **Private Coins versus Public Coins in Interactive Proof Systems** by Shaft Goldwasser and Michael Sipser

### 1.2 Related Questions on this lecture

- How are the probability inequalities calculated?
	- specially, is the understanding correct that
> Event $$\begin{align*} E_0 =\{\text{random picked h and y, }\exists x\in S:h(x)=y\} \\=\{\text{random picked h and y, }\exists ! x\in S:h(x)=y\} \cup \{\text{random picked h and y, }\exists \text{2 of } x\in S:h(x)=y\}\cup\dots\end{align*} $$
- How the lecturer convert the protocol to perfect completeness?
	- If the $\epsilon$ could be eliminated by taking a large enough $m$ , why do we still need the proof of the shift part.
	- Especially the shift part.
		- Why shift could help smoothen out the error?

## 2 Public coin and Private coin

### 2.1 Definitions

A verifier $V$ is **public-coin** if its every **message** is freshly sampled uniform random string of a prescribed length. Otherwise, it's private-coin.

#question 
> Why is the publicity of the randomness not mentioned here?
> The message here implicitly means these random strings are sent as messages to the prover.

### 2.2 Definition of AM/MA

$AM[k](MA[k])$ are [[Language|language]]s decidable via public-coin k-round [[Interactive proof system|interactive proof]]s where the verifier (prover) moves first.

## 3 [[GNI]] is contained in $AM[2]$

The lecturer first showed that GNI is contained in $AM[2]$ which is a conclusion in ["The Knowledge Complexity of Interactive Proof-Systems"](https://epubs.siam.org/doi/epdf/10.1137/0218012)  by Shafi Goldwasser, Silvio Micali, and Charles Rackoff in 1989.

#question 
What is a non-deterministic circuit?
> A **non-deterministic circuit** is a computational model similar to a Boolean circuit but with the ability to make "guesses" or have multiple possible computation paths, analogous to non-determinism in Turing machines.
> 
> More concretely:
> 
> - It is a Boolean circuit that, in addition to the usual input bits, takes some **non-deterministic bits** (or guess bits) as extra inputs.
> - The circuit **accepts** an input if there exists some assignment to these non-deterministic bits that makes the circuit output 1 (true).
> - This models the idea of "guessing" a solution and then verifying it efficiently.
> 
> Non-deterministic circuits are used to characterize complexity classes like NP, where membership means there exists a certificate (non-deterministic guess) that can be verified efficiently by a deterministic circuit.

### 3.1 How is it proved in lecture

#### 3.1.1 Show the Probability Gap
First, define $S:= \{H|H \equiv G_0 \lor H\equiv G_1\}$

1. To show that two graphs $G_0,G_1$ are not isomorphic to each other, it suffices to show that the cardinality of $S$ is $2\cdot n!$ rather than $n!$. 
	> Here the lecturer assuming that $aut(G_0) = aut(G_1)=id$. Which means that both graphs have no non-trivial automorphisms; their only automorphism is the identity. This implies the graphs have no symmetries other than the trivial one. We do have a general way for proving on a general case, but at least now, we focus on a simpler case to demonstrate the protocol.

Second, lecturer introduce [[Pairwise Independent Hashing]] family $H_{m,l}$ to show that:
- $\forall \text{ distinct }x,x' \in \{0,1\}^m$, $\forall y,y' \in\{0,1\}^l$
- the probability of the event $E:=\{h(x)=y \land h(x')=y'\}$ :
	$$Pr(E)= \frac{1}{2^{2l}}$$
	
> The pairwise independent means: 
> - First we have 2 pairs of image and pre-image, $(x,y)$ and $(x',y')$ 
> - The hash value on $x,x'$ behave like [[independent uniform random variables]]
> 	- Uniform: equal probability of being chosen from a specific range
> 	- Uniform: Knowing the value of one variable doesn't change the probabilities associated with the other variables. #question I guess that's why we say $x \neq x'$ but we still apply the multiplication on the propabilities.


Then, lecturer introduce the **S**et **L**ower **B**ound Protocol (SLB), 

> Let $S \subset \{0,1\}^m$ and $S \in NP$

To construct this protocol, we need to show 2 things:

1. The soundness property hold with a soundness error
2. The completeness property hold with a probability greater that the soundness error

To obtain these 2 properties, prover first pick a specific bound $B$ with $2^{l-2} \leq B \leq 2^{l-1}$. And by applying the inclusion-exclusion principle, 2 inequalities are introduced.

> - The chosen range of $B$ will help us to obtain a gap later between Soundness and Completeness. We should also noticed that once $B$ is fixed, we can calculate the gap with $B$, and we don't have to convert it to a real number by the inequality at early steps which may lead to the negative gap in the lecture.
> - Notice that $l$ is aligned with the power of hash function output;

#question 
>Why we have $$Pr_{h,y}[ \exists x\in S:h(x)=y]\leq \sum_{x\in S}Pr_{h,y}[h(x)=y]$$ while proving the soundness error bound,
> but we have $$Pr_{h,y}[ \exists x\in S:h(x)=y]\geq \sum_{x\in S}Pr_{h,y}[h(x)=y]-\frac{1}{2} \sum_{x,x' \in S,x\neq x'}Pr_{h}[h(x)=y,h(x')=y]$$ while proving the completeness bound?
> 
> Okay, this question troubles me for a while, I can not easily come up how the inclusion-exclusion principle works here.
> 
> The first question I have is why it is  "$\leq$" rather than "$=$" here ?: $$Pr_{h,y}[ \exists x\in S:h(x)=y] = \sum_{x\in S}Pr_{h,y}[h(x)=y]$$
> The answer is NO, they aren't. The left hand side is the probability that at least one element $x \in S$  with its hash equal $y$ , thus this includes {only one $x$, 2 $x$'s ,.... }. But the RHS is the sum of the probabilities of all possible $x\in S \text{ with } h(x) = y$. And that's how inclusion-exclusion principle applies.
> 
> Event $$\begin{align*} E_0 =\{\text{random picked h and y, }\exists x\in S:h(x)=y\} \\=\{\text{random picked h and y, }\exists ! x\in S:h(x)=y\} \cup \{\text{random picked h and y, }\exists \text{2 of } x\in S:h(x)=y\}\cup\dots\end{align*} $$


Now, consider represent $S$ in the **Adjacency Matrix** of the graph $S:= \{H \in\{0,1\}^{n^2}|H \equiv G_0 \lor H\equiv G_1\}$ , also based on the assumption that $aut(G_0) = aut(G_1)=id$.  

> Thus here, the size of domain $m$ of the hash function is $n^2$ is $n^2$ as defined.
> 
> The bound parameter $B:= 2n!$ as $|S| \geq B$ suffices to pass the test. Then we obtain $l = O(n\log n)$ by looking at $2^{l-2} \leq B\leq {2}^{l-1}$ which lead to $l<m$ as expected.
> 

> Here we showed that $GNI\in AM[1]$

#### 3.1.2 Use the Probability Gap to construct a one round protocol

Then we have a **ONE Round** Public Coin Interactive Proof for GNI with:
- Completeness: 
	- If  $(G_0,G_1)\in GNI$ , that is $|S| =2n!$, then
		$Pr[\text{honest P convinces V}]=Pr_{h,y}[\exists H \in S:h(H)=y]\geq \frac{3}{4}\cdot \frac{B}{2^l}$
- Soundness
	- If  $(G_0,G_1) \not\in GNI$ , that is $|S| =n!$, then
		$Pr[\text{malicious P convinces V}]=Pr_{h,y}[\exists H \in S:h(H)=y]\leq \frac{1}{2}\cdot \frac{B}{2^l}$ 

#### 3.1.3 Convert the one round protocol to 2 round protocol with perfect completeness

Consider we do this in 2 steps:
1. Construct an IP
2. Simulate the IP in a one-round IP

##### 3.1.3.1 The public coin IP for GNI

To bring back the good property of perfect completeness, we now introduce a theorem

> If 
> 	L has a $k$-round public-coin interactive proof 
> then 
> 	L has a $(k+1)$-round public-coin interactive proof with perfect completeness.

Here's the detail

Suppose $\mathcal{L}$ is decidable by a probabilistic polynomial-time algorithm $M$ with error bound $\epsilon$. By repetition (& majority) we can assume that $\epsilon< \frac{1}{m}$ where $m$ is the number of random bits.

> What is error bound $\epsilon$ of a probabilistic algorithm $M$?
> 	This refers to the maximum probability that $M$ outputs an incorrect answer 
> 	(i.e **accepts** an input $x \not\in  \mathcal{L}$ or **reject** $x\in \mathcal{L}$)


Given $x$ , define $$A(x)=\{ r\in \{0,1\}^m|M(x;r)=1\}$$
> That is, $A(x)$ represents all the string $r$ could be accepted by $M$ with respect to an input $x$

If $x \in \mathcal{L}$, then

$$
|A(x)| \geq (1 - \epsilon) 2^m,
$$

and can show by probabilistic method that

$$
\exists s^{(1)}, \ldots, s^{(m)} \in \{0,1\}^m \quad \forall r \in \{0,1\}^m \quad \exists i \in [m] \quad s^{(i)} \oplus r \in A(x)
$$

If $x \notin \mathcal{L}$, then

$$
|A(x)| \leq \epsilon 2^m,
$$

and can show by union bound that

$$
\forall s^{(1)}, \ldots, s^{(m)} \in \{0,1\}^m \quad \exists r \in \{0,1\}^m \quad \forall i \in [m] \quad s^{(i)} \oplus r \notin A(x).
$$


In blue:

$$
\exists y \forall z \quad \phi(x,y,z) = 1 \implies \mathcal{L} \subseteq \Sigma_2^P,
$$

and

$$
\forall y \exists z \quad \neg \phi(x,y,z).
$$
##### 3.1.3.2 what is Repetition and Majority

A standard technique used to reduce the error probability of a probabilistic algorithm or interactive proof.

- **Repetition** means running the probabilistic algorithm multiple times independently on the same input.
- **Majority** means taking the majority vote of the multiple runs' outputs as the final decision.

For example, if a probabilistic algorithm $M$ has error probability $\epsilon$ (chance of incorrect output), then by running $M$ independently $k$ times and outputting the majority result, the error probability decreases exponentially in $k$.

This technique allows us to assume the error bound $\epsilon$ is very small (e.g., less than $1/m$ where $m$ is the number of random bits used by the algorithm), which is useful for constructing interactive proofs with strong completeness and soundness guarantees.

###### 3.1.3.2.1 what is $\sum_2^p$

Read as $\Sigma_2$ polynomial hierarchy

- **$\Sigma$ (Sigma):**  
  In complexity theory, $\Sigma$ denotes a level in the [[Polynomial Hierarchy|polynomial hierarchy]] related to existential quantifiers. It represents classes of decision problems defined by alternating quantifiers starting with an existential quantifier.

- **2:**  
  The number 2 indicates the **second level** in the polynomial hierarchy. This means the problems involve two alternating quantifiers, typically an existential quantifier followed by a universal quantifier.

- **Polynomial:**  
  Refers to computations or resources bounded by a polynomial function of the input size. For example, polynomial time means the running time is at most $O(n^k)$ for some constant $k$, where $n$ is the input size.

- **Hierarchy:**  
  A structured classification of complexity classes arranged in levels, where each level allows more complex quantifier alternations or oracle access. The polynomial hierarchy generalizes classes like NP and co-NP by allowing alternating quantifiers.


Putting it together, **$\Sigma_2$ polynomial hierarchy** refers to the second level of the polynomial hierarchy, consisting of decision problems solvable by a polynomial-time machine with an existential quantifier followed by a universal quantifier over polynomial-length strings.
###### 3.1.3.2.2 what is probabilistic method?
###### 3.1.3.2.3 what is union bound?

##### 3.1.3.3 Simulate the IP in a one-round IP

**Prover** $P^*(x)$:  

1. Find $s^{(1)}, \ldots, s^{(m)} \in \{0,1\}^m$ such that  
$$
\forall r \in \{0,1\}^m, \exists i \in [m], \quad s^{(i)} \oplus r \in A(P,x).
$$


2. Send the shifts to the Verifier

3. simulate $j$ round locally
	
	For $j = 1, \ldots, k$:  
	$$
	a_j^{(1)}, \ldots, a_j^{(m)} \to r_j.
	$$
	
	And simulate $m$ executions of previous IP 
	
	For $i = 1, \ldots, m$:  
$$
a_j^{(i)} := P(x, s_j^{(i)} \oplus r, \ldots, s_{j-1}^{(i)} \oplus r_{j-1}^{(i)}).
$$

**Verifier** $V^*(x; r)$

> where $(r_1, \ldots, r_k) \in \{0,1\}^m$ is verifier randomness:

The verifier accepts if and only if  
$$
\lor_{i=1}^m V\big(x, a_1^{(i)}, a_2^{(i)}, \ldots, a_k^{(i)}; s^{(i)} \oplus r\big) = 1.
$$