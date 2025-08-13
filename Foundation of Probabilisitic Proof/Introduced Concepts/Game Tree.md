---
tags: 
Created: 2025-08-08 15:56
aliases: 
related: 
link: 
Type:
---
# Game Tree

In an [[Interactive proof system|interactive proof]] (or more generally, any two-party _game_ between a probabilistic verifier _V_ and an (unbounded) prover _P_), the _game tree_ is the explicit unfolding of every possible transcript:

- The root is the initial configuration.
- Levels alternate between 
	- **prover nodes** 
		- the prover chooses the outgoing edge deterministically as a function of the transcript seen so far  
	- **verifier-random nodes** 
		- the verifier flips fresh coins and moves along the edge labelled by the outcome
- Leaves are labelled according to the verifier’s final decision rule.
	- 1 (accept) or 
	- 0 (reject) 

Formally, the game tree encodes a probability space
	the verifier’s random choices induce a distribution on the leaves, and the acceptance probability of the protocol is the measure of the “1(accepted)” leaves.
	
## 1 Questions
### 1.1 Why we say the randomness in the leave node aligns with its path to the root

### 1.2 What is the relationship with the language L

