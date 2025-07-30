---
tags: 
Created: 2025-07-30 11:47
aliases:
  - NPI
related: 
link:
---
## 1 Notes

**NPI 集合**（NPI set）是计算复杂性理论中的一个术语，NPI 是 “NP-Intermediate” 的缩写，意为“NP-中间问题集合”。

### 1.1 详细解释

- **NP 类**：包含所有可以在多项式时间内验证解的问题。
- **P 类**：包含所有可以在多项式时间内**求解**的问题。
- **NP-Complete（NP 完全）**：NP 中最难的问题，所有 NP 问题都可以多项式时间归约到它们。

**NPI 集合**指的是那些：
- 属于 NP，
- 但既不属于 P，
- 也不是 NP-Complete 的问题。

用数学语言表示：
$$
\text{NPI} = \{ L \in NP \mid L \notin P \text{ 且 } L \text{ 不是 NP-Complete} \}
$$

---

### 1.2 相关理论

- **Ladner 定理**（Ladner’s Theorem）：如果 $P \neq NP$，那么必然存在 NPI 问题，也就是说，NP 中确实存在既不容易也不极难的“中间问题”。
- 这些问题被称为**NP-中间问题**（NP-intermediate problems）。

---

### 1.3 例子

目前没有被证明是 NPI 的具体自然问题，但有一些被广泛怀疑是 NPI 的问题，例如：
- 图同构问题（Graph Isomorphism）
- 整数因式分解问题（Integer Factorization）

这些问题目前已知在 NP 中，但既没有多项式时间算法，也没有被证明是 NP 完全的。

---

### 1.4 总结

**NPI 集合**是指那些在 NP 中，但既不属于 P，也不是 NP 完全的问题。如果 $P \neq NP$，这样的“中间问题”一定存在。