---
tags: 
Created: 2025-07-30 09:02
aliases: 
related: 
link:
---
在计算复杂性理论中，PSPACE 和 coNP 是两个非常重要的复杂性类，它们分别描述了在不同计算资源限制下可以解决的决策问题集合。
## 1 PSPACE

### 1.1 DEF

PSPACE 是所有可以在多项式空间内**由确定性图灵机解决的决策问题的集合**。

形式表达：

$\text{PSPACE} = \{L \mid \text{存在一个确定性图灵机，使用空间 } \mathcal{O}(n^k) \text{ 解出输入属于 } L \text{ 的问题} \}$


### 1.2 Example

- 国际象棋是否在给定局面下可以在 k 步内被将死？（对于固定棋盘大小，这是 PSPACE 完全问题）
- Quantified Boolean Formula（QBF）问题：是否存在一个布尔公式，其对所有变量赋值成立？这是 PSPACE 完全问题

### 1.3 Understanding

- 不关心算法运行的时间快不快，只关心它是否能在有限（多项式）内存中完成。
- PSPACE ⊇ NP，也 ⊇ coNP，甚至包含很多更难的问题。

### 1.4 Relation between PSpace and NP

**PSpace** and **NP** are both complexity classes in computational complexity theory, but they describe different resources:

- **NP (Nondeterministic Polynomial time):**  
  The class of decision problems for which a solution can be *verified* in polynomial time by a deterministic Turing machine.

- **PSpace (Polynomial Space):**  
  The class of **decision problems** that can be *solved* using **a polynomial amount of memory (space)**, regardless of how much time it takes.

#### 1.4.1 Relation between PSpace and NP

- **Containment:**  
  $NP \subseteq PSPACE$  
  Every problem in NP can be solved using polynomial space. This is because a nondeterministic polynomial-time computation can be simulated by a deterministic machine using polynomial space (**by exploring all possible computation paths, one at a time, using backtracking**).

- **Strictness:**  
  It is **unknown** whether $NP = PSPACE$ or $NP \subset PSPACE$. Most complexity theorists believe that $NP \neq PSPACE$, but this has not been proven.

- **Hierarchy:**  
  The known inclusions are:  
  $P \subseteq NP \subseteq PSPACE \subseteq EXPTIME$

#### 1.4.2 Example

- **NP-complete problem:** SAT (Boolean satisfiability)
- **PSPACE-complete problem:** QBF (Quantified Boolean Formula)

SAT is in NP (and thus in PSPACE), but QBF is PSPACE-complete and believed to be harder than any NP-complete problem.

#### 1.4.3 Summary Table

| Class    | Definition                          | Known Relation      |
|----------|-------------------------------------|---------------------|
| NP       | Verifiable in polynomial time       | $NP \subseteq PSPACE$ |
| PSPACE   | Solvable in polynomial space        |                     |

**In summary:**  
Every NP problem can be solved in polynomial space, but not every PSPACE problem is known to be in NP. The exact relationship (equality or strict containment) is an open question.
## 2 coNP

定义：

coNP 是 NP 的补类，表示所有“反例验证困难”的问题。

  

形式表达：

一个问题在 coNP 中，若它的补问题（即判断“不成立”）在 NP 中。

  

理解：

- NP 是“存在性证明容易验证”，例如：SAT 问题。
    
- coNP 是“否定性证明容易验证”，例如：TAUT 问题（判断一个命题公式是否总为真）。
    

  

举例：

- 命题公式是否是重言式（即对所有输入都成立）？→ TAUT ∈ coNP
    
- 若能有效验证某个命题不是重言式（即找出一个反例），那问题就在 coNP 中。
    

---

### 2.1 三、关系与图示

  

常见包含关系如下：

  

\text{P} \subseteq \text{NP} \subseteq \text{PSPACE}

\text{P} \subseteq \text{coNP} \subseteq \text{PSPACE}

  

目前不知道是否：

- \text{NP} = \text{coNP}？（普遍认为不相等）
    
- \text{NP} = \text{PSPACE}？（一般认为不等）
    
- \text{P} = \text{NP}？（这是著名的未解决难题）
    

---

### 2.2 总结对比表：

|类别|代表问题|定义特征|与 NP 关系|
|---|---|---|---|
|PSPACE|QBF（量化布尔公式）|在多项式空间内可解|包含 NP 和 coNP|
|coNP|命题公式是否恒真（TAUT）|补问题在 NP 内|一般认为与 NP 不相等|

如果你需要了解某一类问题是否属于 PSPACE 或 coNP，我可以为你列出常见的归类。