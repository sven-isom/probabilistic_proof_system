---
tags: 
Created: 2025-07-22 17:39
aliases: 
related: 
link:
---
## 1 Notes

> Language is not mentioned in the Textbook but mentioned in the Lecture by Chiesa

In Computational Complexity Theory, the concept of **Language** has a very clear and fundamental definition:
### 1.1 Definition

In complexity theory, a language is **a set of strings**, where these strings are usually formed from some alphabet (such as the binary alphabet $\{0,1\}$). Each string represents an instance of a problem. Essentially, a language describes "which inputs are the problem instances we care about that have the answer 'yes'."

**Formal expression:**  
- Let $\Sigma$ be a finite alphabet (e.g., $\Sigma = \{0,1\}$).  
- $\Sigma^*$ denotes the set of all finite-length strings over $\Sigma$.  
- A language $L$ is a subset of $\Sigma^*$: $L \subseteq \Sigma^*$.

**Examples:**  
- $L_{prime} = \{x \mid x \text{ is a binary representation of a prime number}\}$  
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