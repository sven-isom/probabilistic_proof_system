---
tags: 
Created: 2025-07-22 17:39
aliases: 
related: 
link:
---
# Language

> Language is not mentioned in the Textbook but mentioned in the Lecture by Chiesa

> In my opinion, a language $L$ is the **solution set** to a [[Decision Problem|decision problem]], where:
> 
> - Every string $x \in L$ **satisfies** the property or condition described by the decision problem.
> - The decision problem asks: *Given an input string $x$, does $x$ belong to $L$?*  
> - If yes, then $x$ is a "yes" instance of the problem; if no, then $x$ is a "no" instance.

> In other words:
> A language $L$ is the set of all inputs for which the answer to the decision problem is "yes."

> 
> For example, for the language
> 
> $$
 L_{prime} = \{ x \mid x \text{ is a binary representation of a prime number} \},
  $$
> 
> the decision problem is *"Is the number represented by $x$ prime?"* and $L_{prime}$ contains exactly those strings $x$ for which the answer is yes.
> 
> This perspective is fundamental in [[复杂性理论|complexity theory]] because it allows us to study computational problems by analyzing the languages that represent their "yes" instances.

## 1 Definition

In complexity theory, a language is **a set of strings**, where these strings are usually formed from some alphabet (such as the binary alphabet $\{0,1\}$). Each string represents **an instance of a problem**. 

Essentially, a *language* describes "which inputs are the problem instances we care about that have the answer 'yes'."

**Formal expression:**  
- Let $\Sigma$ be a finite alphabet (e.g., $\Sigma = \{0,1\}$).  
- $\Sigma^*$ denotes the set of all finite-length strings over $\Sigma$.  
- A language $L$ is a subset of $\Sigma^*$: $L \subseteq \Sigma^*$.

**Examples:**  
- $L_{prime} = \{x \mid x \text{ is a binary representation of a prime number}\}$  
	By definition of language, L is a set of strings, where these strings are formed from alphabet, and $\forall x\in L$ , $x$ represents an instance of problem, in this case, the statement is that : $x$ is a prime number.
	- $L_{prime}$ is the set of all binary strings encoding prime numbers.
	- Deciding membership in $L_{prime}$ means testing primality.
	- It exemplifies how languages represent computational problems in complexity theory.
- $L_{SAT} = \{\varphi \mid \varphi \text{ is a satisfiable Boolean formula}\}$

**Role in decision problems:**  
Most problems in complexity theory are formulated as deciding whether a given string belongs to a language. For example, given an input $x$, an algorithm must decide whether $x \in L$ holds.

**Relation to complexity classes:**  
- Class $P$: all languages decidable by polynomial-time algorithms.  
- Class $NP$: all languages decidable by polynomial-time nondeterministic algorithms.  
- Class $IP$: all languages that have interactive proof systems.

**Summary:**  
In complexity theory, a **language is a set of strings satisfying certain properties**, serving as the fundamental unit to describe and study computational problems.

## 2 Notes

- Sounds like some kinds of free group
- Might be related to promise problems