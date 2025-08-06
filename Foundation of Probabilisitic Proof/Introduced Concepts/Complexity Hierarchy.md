---
tags: 
Created: 2025-08-05 18:27
aliases: 
related: 
link: 
Type:
---
## 1 Definition of Complexity Hierarchy

A **complexity hierarchy** is a structured classification of computational problems or complexity classes arranged according to their relative computational resources required, such as time, space, or alternation depth.

These hierarchies show how increasing resource bounds or computational power leads to strictly larger classes of problems that can be solved.

---

### 1.1 Examples of Complexity Hierarchies

- **Time Hierarchy Theorem:** For time-constructible functions $t_1(n)$ and $t_2(n)$ with $t_2(n) \gg t_1(n) \log t_1(n)$,  
  $$
  \text{DTIME}(t_1(n)) \subsetneq \text{DTIME}(t_2(n)),
  $$  
  meaning more time allows solving strictly more problems.

- **Space Hierarchy Theorem:** For space-constructible functions $s_1(n)$ and $s_2(n)$ with $s_2(n) \gg s_1(n)$,  
  $$
  \text{DSPACE}(s_1(n)) \subsetneq \text{DSPACE}(s_2(n)),
  $$  
  meaning more space allows solving strictly more problems.

- **Polynomial Hierarchy (PH):** A hierarchy of complexity classes defined by alternating quantifiers, generalizing NP and coNP, with levels $\Sigma_k^P$ and $\Pi_k^P$.


### 1.2 Notation of 2nd level of Complexity Hierarchy

