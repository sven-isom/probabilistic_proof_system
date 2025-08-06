---
tags: 
Created: 2025-08-05 13:58
aliases: 
related: 
link: 
Type:
---
## 1 Definition of Automorphism Group

An **automorphism** of a mathematical object (such as a graph, group, or algebraic structure) is an isomorphism from the object to itself. It is a bijective mapping that preserves the structure of the object.

The **automorphism group** of an object is the set of all automorphisms of that object, equipped with the operation of composition. This set forms a group because:

- Composition of two automorphisms is an automorphism.
- There is an identity automorphism (the identity mapping).
- Each automorphism has an inverse automorphism.

---

## 2 Example: Automorphism Group of a Graph

Consider the graph $G$ with vertices $V = \{1, 2, 3\}$ and edges $E = \{\{1,2\}, \{2,3\}\}$:

```
1 — 2 — 3
```

- An automorphism of $G$ is a permutation of the vertices that preserves adjacency.
- For this graph, the automorphisms are:
  - The identity mapping: $(1 \to 1, 2 \to 2, 3 \to 3)$
  - The reflection swapping vertices 1 and 3: $(1 \leftrightarrow 3, 2 \to 2)$

Thus, the automorphism group of $G$ has two elements and is isomorphic to the group $\mathbb{Z}_2$.

---

Automorphism groups capture the symmetries of structures and are fundamental in many areas of mathematics and theoretical computer science.