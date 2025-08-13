---
tags: 
Created: 2025-08-03 22:43
aliases:
  - \#SAT
  - Sharp-SAT
  - Counting Problem
related: 
link: 
Type:
---
# Sharp-SAT

In computer science, the **Sharp Satisfiability Problem** (sometimes called **Sharp-SAT**, **#SAT** or **model counting**) is the problem of counting **the number of interpretations** that satisfy a given Boolean formula, introduced by Valiant in 1979.

In other words, it asks in how many ways the variables of a given Boolean formula can be consistently replaced by the values TRUE or FALSE in such a way that the formula evaluates to TRUE. For example, the formula $a \lor \neg b$ is satisfiable by three distinct boolean value assignments of the variables, namely, for any of the assignments $(a = \text{TRUE}, b = \text{FALSE})$, $(a = \text{FALSE}, b = \text{FALSE})$, and $(a = \text{TRUE}, b = \text{TRUE})$, we have  
$$
a \lor \neg b = \text{TRUE}.
$$

\#SAT is different from Boolean satisfiability problem (SAT), which asks if there exists *a solution* of Boolean formula. Instead, \#SAT asks to enumerate *all the solutions* to a Boolean Formula. \#SAT is harder than SAT in the sense that, once the total number of solutions to a Boolean formula is known, SAT can be decided in constant time. However, the converse is not true, because knowing a Boolean formula has *a solution* does not help us to count *all the solutions*, as there are an exponential number of possibilities.

\#SAT is a well-known example of the class of counting problems, known as **#P-complete** (read as sharp P complete). 
In other words, every instance of a problem in the complexity class \#P can be reduced to an instance of the \#SAT problem. 
This is an important result because many difficult counting problems arise in Enumerative Combinatorics, Statistical physics, Network Reliability, and Artificial intelligence without any known formula. If a problem is shown to be hard, then it provides a complexity theoretic explanation for the lack of nice looking formulas.


#question 
1. What is p to sharp p($p^{\#p}$ )
2. 