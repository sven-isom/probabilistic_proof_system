---
tags: 
Created: 2025-07-30 09:10
aliases: 
related: 
link:
---
## 1 Definition 

> Oded : P244

### 1.1 Definition by Oded_Goldreich

**Definition 7.1** (one-way functions): A function $f : \{0, 1\}^* \to \{0, 1\}^*$ is called one-way if the following two conditions hold:

1. Easy to evaluate: *There exists a polynomial-time algorithm $A$ such that $A(x) = f(x)$ for every $x \in \{0, 1\}^*$.*
2. Hard to invert: For every probabilistic polynomial-time algorithm $A'$, every polynomial $p$, and all sufficiently large $n$,
   $$
   \Pr_{x \in \{0,1\}^n}[A'(f(x), 1^n) \in f^{-1}(f(x))] < \frac{1}{p(n)}
   $$

	where the probability is taken uniformly over all the possible choices of $x \in \{0, 1\}^n$ and all the possible outcomes of the internal coin tosses of algorithm $A'$.

- $\Pr_{x \in \{0,1\}^n}[\cdots]$：表示对所有长度为 $n$ 的二进制字符串 $x$，均匀随机选择 $x$ 的情况下，括号内事件发生的概率。
- $A'$：是任意一个概率多项式时间算法（攻击者/逆算法）。
- $f(x)$：是单向函数的输出。
- $A'(f(x), 1^n)$：算法 $A'$ 得到 $f(x)$ 和 $n$ 的一串 $1$（用来指明输入长度），试图“逆向”计算出 $x$。
- $f^{-1}(f(x))$：表示所有能映射到 $f(x)$ 的原像（即 $f(y) = f(x)$ 的所有 $y$）。
- $A'(f(x), 1^n) \in f^{-1}(f(x))$：表示 $A'$ 成功找到了一个 $y$，使得 $f(y) = f(x)$，即逆向成功。

**整体意思：**
对于任意多项式 $p(n)$，当 $n$ 足够大时，任何概率多项式时间算法 $A'$ 想要通过 $f(x)$ 逆推出 $x$（或任何 $y$ 使 $f(y) = f(x)$）的概率都小于 $\frac{1}{p(n)}$。也就是说，逆向的成功概率会随着 $n$ 的增大而迅速变小，几乎不可能成功。

**简要总结：**
这个公式形式化地表达了“单向函数难以逆向”，即即使给定 $f(x)$，用任何高效算法也几乎无法找回 $x$。