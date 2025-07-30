---
tags: 
Created: 2025-07-30 11:27
aliases:
  - IP
related: 
link:
---
## 1 DEF
> P355 Oded

**Definition 9.1** (interactive proof system – IP):  
An interactive proof system for a set $S$ is a two-party game, between a verifier executing a probabilistic polynomial-time strategy, denoted $V$, and a prover that executes a (computationally unbounded) strategy, denoted $P$, satisfying the following two conditions:

- **Completeness:** For every $x \in S$, the verifier $V$ always accepts after interacting with the prover $P$ on common input $x$.
- **Soundness:** For every $x \notin S$ and every strategy $P^*$, the verifier $V$ rejects with probability at least $\frac{1}{2}$ after interacting with $P^*$ on common input $x$.

We denote by $\mathcal{IP}$ the class of sets having interactive proof systems.


## 2 soundness error
**Soundness error（可靠性误差）**是交互式证明系统（Interactive Proof System）或概率证明系统中的一个重要概念。它描述了在“错误情况下”验证者被欺骗的最大概率。

### 2.1 详细解释

- **Soundness（可靠性）**：  
  如果输入 $x$ 不属于语言 $S$（即 $x \notin S$），那么无论证明者（哪怕是恶意的）采用什么策略，验证者都应该“高概率”拒绝。
- **Soundness error（可靠性误差）**：  
  指的是在 $x \notin S$ 时，验证者**错误接受**的最大概率。  
  换句话说，就是“骗子”证明者成功欺骗验证者的最大概率。

### 2.2 公式表达

如果 soundness error 是 $\epsilon$，则对于所有 $x \notin S$ 和所有可能的证明者 $P^*$，有：
$$
\Pr[\text{Verifier accepts after interacting with } P^* \text{ on } x] \leq \epsilon
$$

例如，在你给出的定义中，soundness error 是 $1/2$，即：
- 对于 $x \notin S$，任何证明者 $P^*$，验证者接受的概率 $\leq 1/2$。

### 2.3 降低 soundness error

通常可以通过**重复协议多次**来降低 soundness error。例如，重复 $k$ 次，soundness error 会降为 $\epsilon^k$（如果每次独立）。

### 2.4 总结

**Soundness error** 表示在输入不属于语言时，验证者被欺骗接受的最大概率。它是衡量交互式证明系统安全性的重要参数，越小越安全。

## 3 Interactive proof system with no soundness error

> P356

**Proposition 9.2:** Suppose that $S$ has an interactive proof system $(P, V)$ with no soundness error; that is, for every $x \notin S$ and every potential strategy $P^*$, the verifier $V$ rejects with probability one after interacting with $P^*$ on common input $x$. Then $S \in \mathcal{NP}$.

### 3.1 Relationship with NP

Question, is it ture that 基于零错误率（perfect soundness）的交互式证明系统所代表的语言集合是 NP。
是的，基于零错误率（perfect soundness）的交互式证明系统所代表的语言集合正好就是 NP。


#### 3.1.1 更正式地说：

- 若一个语言 S 有一个交互式证明系统 (P, V)，满足：
    - 完备性（Completeness）：如果 x \in S，则存在某个（诚实的）证明者 P，使得验证者 V 接受（概率 ≥ 2/3，或甚至是概率 1）；
    - 零错误率的可靠性（Perfect Soundness）：如果 x \notin S，那么无论证明者采用何种策略 P^*，验证者都始终拒绝（概率 1），
        
则这个语言 $S \in \text{NP}$。

此外，反过来也成立：

- 对于任意 S \in \text{NP}，我们都可以构造一个满足完备性和 perfect soundness 的交互式证明系统。

设 $\mathbf{IP}_{\text{perf}}$ 表示所有在完美 soundness 下可交互证明的语言的集合，则我们有：

$$\mathbf{IP}_{\text{perf}} = \text{NP}$$

这说明：

- 如果我们限制交互式证明系统必须具有 perfect soundness，则它的表达能力不会超出 NP；
- 想要超越 NP（比如覆盖到 coNP 或 PSPACE），就必须放宽 soundness 要求，允许一个可控的小错误概率（即标准 IP 的定义允许 soundness error ≤ 1/3）。

#### 3.1.2 延伸说明：

- 交互式证明系统 IP 的经典结果为：

$$\mathbf{IP} = \text{PSPACE}$$


也就是说，在允许随机性和有界错误概率的交互系统中，其表达能力可以扩展至 PSPACE。此结果显示了“交互+随机性”的强大力量。

