---
tags: 
Created: 2025-07-30 09:02
aliases: 
related: 
link:
---
> PSPACE is a set of  [[Language|language]]s that are decidable polynomial space. 

> - Here decidable in polynomial space won't limit any on the time complexity.

> PSPACE, P, NP and [[coNP]] are defined on two different types of resources, and they are related. We could see that P $\subset$ coNP $\subset$ PSPACE and P $\subset$ NP $\subset$ PSPACE.
# PSPACE

## 1 DEF

The class of [[Decision Problem|decision problem]]s that are solvable in polynomial space is denoted as:

$$
\mathcal{PSPACE} := \bigcup_{c} \text{DSPACE}(n^c),
$$

where $\text{DSPACE}(n^c)$ is the set of problems decidable by a deterministic Turing machine using space bounded by a polynomial function $n^c$.

Formally,

$$
\text{PSPACE} = \{ L \mid \text{there exists a deterministic Turing machine that decides } L \text{ using space } \mathcal{O}(n^k) \text{ for some } k \}.
$$


## 2 Examples of PSPACE Problems

- Determining whether a given position in chess can lead to checkmate within $k$ moves (for fixed board size) is PSPACE-complete.
- The Quantified Boolean Formula (QBF) problem: deciding the truth of a fully quantified Boolean formula is PSPACE-complete.

## 3 Understanding PSPACE

- PSPACE focuses on the amount of memory (space) used, not the time.
- It contains NP and coNP, and many problems believed to be harder than NP-complete problems.

## 4 Relation between PSPACE and NP

- **NP**: Problems verifiable in polynomial time.
- **PSPACE**: Problems solvable in polynomial space (regardless of time).

Known relations:

$$
P \subseteq NP \subseteq PSPACE \subseteq EXPTIME.
$$

It is unknown whether these inclusions are strict, but it is widely believed that:

$$
NP \neq PSPACE.
$$

## 5 Summary Table

| Class  | Definition                    | Relation to NP        |
| ------ | ----------------------------- | --------------------- |
| NP     | Verifiable in polynomial time | $NP \subseteq PSPACE$ |
| PSPACE | Solvable in polynomial space  | Contains NP and coNP  |


PSPACE is a fundamental complexity class capturing problems solvable with polynomial memory, including many important decision problems beyond NP.
PSPACE 是所有可以在多项式空间内**由确定性图灵机解决的决策问题的集合**。

形式表达：

$\text{PSPACE} = \{L \mid \text{存在一个确定性图灵机，使用空间 } \mathcal{O}(n^k) \text{ 解出输入属于 } L \text{ 的问题} \}$

## 6 Relation between PSpace and NP

**PSpace** and **NP** are both complexity classes in computational complexity theory, but they describe different resources:

- **NP (Nondeterministic Polynomial time):**  
  The class of decision problems for which a solution can be *verified* in polynomial time by a deterministic Turing machine.

- **PSpace (Polynomial Space):**  
  The class of **decision problems** that can be *solved* using **a polynomial amount of memory (space)**, regardless of how much time it takes.

### 6.1 Relation between PSpace and NP

- **Containment:**  
  $NP \subseteq PSPACE$  
  Every problem in NP can be solved using polynomial space. This is because a nondeterministic polynomial-time computation can be simulated by a deterministic machine using polynomial space (**by exploring all possible computation paths, one at a time, using backtracking**).

- **Strictness:**  
  It is **unknown** whether $NP = PSPACE$ or $NP \subset PSPACE$. Most complexity theorists believe that $NP \neq PSPACE$, but this has not been proven.

- **Hierarchy:**  
  The known inclusions are:  
  $P \subseteq NP \subseteq PSPACE \subseteq EXPTIME$

### 6.2 Example

- **NP-complete problem:** SAT (Boolean satisfiability)
- **PSPACE-complete problem:** QBF (Quantified Boolean Formula)

SAT is in NP (and thus in PSPACE), but QBF is PSPACE-complete and believed to be harder than any NP-complete problem.

### 6.3 Summary Table

| Class    | Definition                          | Known Relation      |
|----------|-------------------------------------|---------------------|
| NP       | Verifiable in polynomial time       | $NP \subseteq PSPACE$ |
| PSPACE   | Solvable in polynomial space        |                     |

**In summary:**  
Every NP problem can be solved in polynomial space, but not every PSPACE problem is known to be in NP. The exact relationship (equality or strict containment) is an open question.
# 1 coNP

定义：

coNP 是 NP 的补类，表示所有“反例验证困难”的问题。

  
形式表达：

一个问题在 coNP 中，若它的补问题（即判断“不成立”）在 NP 中。

## 1 2.1 关系与图示

常见包含关系如下：

$\text{P} \subseteq \text{NP} \subseteq \text{PSPACE}$

$\text{P} \subseteq \text{coNP} \subseteq \text{PSPACE}$


目前不知道是否：

- $\text{NP} = \text{coNP}$？（普遍认为不相等）
- $\text{NP} = \text{PSPACE}$？（一般认为不等）
- $\text{P} = \text{NP}$？（这是著名的未解决难题）
## 2 总结对比表：

|类别|代表问题|定义特征|与 NP 关系|
|---|---|---|---|
|PSPACE|QBF（量化布尔公式）|在多项式空间内可解|包含 NP 和 coNP|
|coNP|命题公式是否恒真（TAUT）|补问题在 NP 内|一般认为与 NP 不相等|

如果你需要了解某一类问题是否属于 PSPACE 或 coNP，我可以为你列出常见的归类。