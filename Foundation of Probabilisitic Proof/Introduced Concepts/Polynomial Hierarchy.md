---
tags: 
Created: 2025-08-03 22:37
aliases:
  - Polynomial Hierarchy
  - PH
related: 
link: 
Type:
---
## 1 Notes

PH 指的是 **Polynomial Hierarchy（多项式层级）**，是计算复杂性理论中的一个复杂度类层级结构，用来描述一系列包含 NP 和 [[coNP]] 等复杂度类的更广泛的层级。

- **Polynomial Hierarchy (PH)** 是由多个层级组成的，每一层级都对应着某种形式的交替量词计算问题。  
- 第一层是 NP 和 coNP。  
- 第二层（2nd level）包括复杂度类如 $\Sigma_2^P$ 和 $\Pi_2^P$，它们分别对应于“存在-所有”交替量词和“所有-存在”交替量词的问题。

具体来说：

- **第一层**：  
  - $\Sigma_1^P = NP$  
  - $\Pi_1^P = coNP$

- **第二层**：  
  - $\Sigma_2^P = NP^{NP}$，即带有 NP oracle 的 NP 机器  
  - $\Pi_2^P = coNP^{NP}$，即带有 NP oracle 的 coNP 机器
