---
tags: 
Created: 2025-08-08 15:43
aliases: 
related: 
link: 
Type:
---
## 1 Notes

[[Game Tree]] 

#question 
1. Lecturer says that, in the Game tree, we put the randomness in the bottom layer, and they must be aligned with their parents nodes, why is that? Should we expect that the Game tree always end with success pass?
2. How would the randomness take part in the move of verifier? Why it show in the leave node?
3. How should we establish the relationship from completeness error and soundness error with the case that:
	> If $x \in L$ then $\text{val}(T) \geq \frac{2}{3}$, else if $x \notin L$ then $\text{val}(T) \leq \frac{1}{3}$. 
	So to decide if $x \in L$ or $x \notin L$ it suffices to approximate $\text{val}(T)$ to within $\pm \frac{1}{6}$.
4. Could it be different value , sum of which is not exactly one?:
   If $x \in L$ then $\text{val}(T) \geq \frac{3}{7}$, else if $x \notin L$ then $\text{val}(T) \leq \frac{1}{3}$. 


So, basically ,what we are doing here is we want to decide wether instance $x$ is in Language $L$ or not.
Thanks to the existence of the constant gap, we could decide whether the membership of $x$ by **approximating** the value of the tree, $val(T(V,x))$ , with an (additive) error. 

And, noted that we can compute $val(T)$ in poly(n) space and exp(poly(n)) time.

Why can we do that 


#question 
If exactly i bits of communication or randomness have been fixed so far, how many distinct partial transcripts can there be?

#question 
What is the inner connection between the prover and the sample size $m$, why we enlarge m could help?