---
tags: 
Created: 2025-08-08 19:12
aliases: 
related: 
link: 
Type:
---
In that notation the three parameters, $pc,vc,vr$, measure **total resources consumed by the whole protocol**, not per-round resources.

|Symbol|What it counts|Scope|
|---|---|---|
|**pc**|Number of bits the _prover_ transmits in the entire conversation|Sum over all prover messages|
|**vc**|Number of bits the _verifier_ transmits in the entire conversation|Sum over all verifier messages|
|**vr**|Number of _private_ random bits the verifier draws over the entire execution|All coins tossed during every verifier move|

Thus an [[Interactive proof system|interactive proof]] belongs to IP[pc,vc,vr]
if, on every input x of length n,

- the prover’s total outbound communication never exceeds pc(n) bits,
- the verifier’s total outbound communication never exceeds vc(n) bits,
- the verifier’s private randomness never exceeds vr(n) bits,

where each of pc,vc,vr is a function—usually a polynomial—of the input size.

**Why it matters**

1. **Tree-size arguments**
    Earlier we bounded the game tree by $2^{O(c)}$ nodes with c=pc+vc+vr. That bound only works if c is the total number of bits across _all_ rounds.
    
2. **Round-independent description**
    Interactive protocols often allow an _unbounded_ number of rounds as long as the _aggregate_ communication and randomness are suitably limited. Counting totals makes the definition independent of how those bits are distributed among rounds.
    
3. **Comparison with AM\[pc,vc,vr\]**  
    In the Arthur–Merlin (public-coin) setting the same aggregate limits apply; the only difference is that the verifier’s random bits are revealed to the prover immediately. Again, the budget is measured over the entire interaction.

