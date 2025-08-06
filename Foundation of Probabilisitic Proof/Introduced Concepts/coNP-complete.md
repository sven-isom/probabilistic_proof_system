---
tags: 
Created: 2025-08-03 22:34
aliases: 
related: 
link: 
Type:
  - Set
---
## 1 What is [[coNP]]-complete
coNP-complete is a complexity class in computational [[复杂性理论|complexity theory]] defined as follows:

- **coNP** is the class of decision problems whose complements are in NP. In other words, a problem is in coNP if its "no" instances can be verified efficiently (in polynomial time) by a nondeterministic Turing machine.

- A problem is **coNP-complete** if:
  1. It belongs to coNP.
  2. Every problem in coNP can be reduced to it in polynomial time.

- coNP-complete problems are considered the hardest problems in coNP, analogous to NP-complete problems in NP, but focusing on verifying "no" instances rather than "yes" instances.

For example, the problem of determining whether a Boolean formula is a tautology (true for all assignments) is coNP-complete, since it is the complement of the SAT problem, which is NP-complete.

In summary, coNP-complete problems represent the most difficult problems in coNP, capturing the complexity of efficiently verifying negative instances.