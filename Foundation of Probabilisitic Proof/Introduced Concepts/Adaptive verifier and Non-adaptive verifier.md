---
tags: 
Created: 2025-08-10 20:56
aliases: 
related: 
link: 
Type: 
Status:
  - unsorted
---
Adaptive vs Non-Adaptive Verifiers

In interactive proofs, the terms **adaptive verifier** and **non-adaptive verifier** describe how the verifier chooses its *randomness* or *queries* during the interaction. 

## 1 Adaptive verifier

- **Definition**: The verifier’s later questions **can depend on** the prover’s earlier answers. 
	- This is the usual model for IPs. 
	- The randomness (or queries) is generated **on the fly** during the interaction, possibly influenced by what the verifier has learned so far. 
- **Example**: 
	- Round 1: Verifier asks “What’s the value of $g_1(X_1)$?” 
	- Round 2: Based on the answer, it chooses $r_1$ in a way that might depend on $g_1$.
	- This adaptivity lets the verifier “zoom in” on suspicious parts. 
 
## 2 Non-adaptive verifier

- **Definition**: The verifier fixes *all* its random coins / queries **in advance**, before seeing any messages from the prover. 
	- All questions are predetermined by the initial randomness; the prover’s answers do not affect which questions come next. 
	- This is sometimes called a **public-coin, non-adaptive** verifier (when all queries are sent at once). 
- **Example**: 
- Verifier flips all its random coins at the start, decides it will query $(q_1, q_2, q_3)$, sends them to the prover, and gets all answers without changing the plan. 

## 3 Why it matters
- **Adaptive**: - Often more powerful — can detect cheating more easily by following up strategically. - But harder to analyze and sometimes harder to transform into other proof systems. 
- **Non-adaptive**: - Easier to simulate in PCPs — in fact, PCPs can be seen as “fully non-adaptive, single-round” verifiers. - May be weaker in expressiveness for some problems. - There are results (e.g., Goldwasser–Sipser) showing how to transform some adaptive public-coin IPs into non-adaptive ones without losing too much power. 

- **In plain language:** 
	- Adaptive verifier = changes its questions as it learns from you. 
	- Non-adaptive verifier = decides all questions before the conversation starts. 