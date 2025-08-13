---
tags: 
Created: 2025-08-13 12:45
aliases: 
related: 
link: 
Type: 
Status:
  - unsorted
---
## 1 Brief Introduction

In this lecture, the professor introduced another benefit : Zero Knowledge.

We now know the meaning that the word zero knowledge wants to transfer.
But what about a rigorous definition? The lecturer introduce it by HVZK

Some important cryptography methods are mentioned in this lecture:
- In cryptography, using [[Simulator Paradigm|simulator paradigm]] to formalise some privacy condition = Clarify yourself some protocol that what I expect other party to know anyway of some necessary info must be leaked.
- [[Rejection Sampling 拒绝采样|Rejection sampling]]
## 2 Outlines

1. GI problem in ZKIP
2. HVZK
3. (MV)ZK

## 3 Feasibility on ZKIP: GI problem in ZKIP

The lecturer first show an example of implementing ZKP in ZKIP with the GI problem.

## 4 The HVZK & HVZK for GI problem

To show what Zero Knowledge stands for, the lecturer introduced the definition of HVZK with the concept [[View of HVZK|View]].

## 5 (MV)ZK

#DEF 
The definition of (MV)ZK is:

If there exists a probabilistic polynomial time (in expectation) simulator $S$ such that:
$\forall x\in L \forall \text{ppt } \tilde{V},S(\tilde{V},x) \equiv \text{View}_\tilde{V}(<P,\tilde{V}>(x))$

1. the ppt $\tilde{V}$ means: what the MV could learn beyond polynomial time is little.
2. Even the Verifier that deviate from the prescribed protocol can not learn any information besides the bit which represent "$x \in L$".
3. In expectation here means that its's a useful and meaning relaxation.
4. By $\equiv$, it means that the output distribution of the simulator $S$ given the verifier $\tilde{V}$ and input $x$ is **computationally indistinguishable**. The definition shows that the simulator function could produce a simulated transcript that looks "the same" as what the verifier would see in a real interaction.
5. It means in the view of the verifier who don't know the secret, the proof itself looks like a randomly generated representation of the knowledge that the secrets statement is true.
   This shows that nothing else other than the "fact" is leaking in the view of verifier.

### 5.1 MVZK of GI

Later, the lecturer claimed that, the MVZK GI happens to be the same as HVZK for GI by showing how the simulator works.

Here, the lecturer mentioned the concept of rejection sampling. He claimed that the simulator $S$ works since it's doing rejection sampling:

$$Pr[\tilde{b}=0|\tilde{b}=b]= \frac{{Pr[\tilde{b}=0\land \tilde{b}=b]}}{Pr[\tilde{b}=b]}=\frac{{Pr[\tilde{b}=0]\cdot \frac{1}{2}}}{\frac{1}{2}} = Pr[\tilde{b}=0]$$

Review the definition of rejection sampling:
Rejection sampling is a technique where you:
1. Generate samples from an easy-to-sample distribution. 
   In this case, the simulator $S$ samples $\tilde{b}$ randomly
2. Accept or reject each sample based on some condition, so that the accepted samples follow the target distribution.
   In this case, the simulator $S$ reject the cases where $\tilde{b}\neq b$ as we see, the simulator will go to step 1 to resample b and do the computation again.

In this case, the simulator tries to produce a view that matches the verifier's view distribution. 

The key point is that the simulator samples candidate transcripts and only "accepts" those that satisfy certain conditions (e.g., the verifier's challenge bit $\tilde{b}$ matches the simulated bit $b$).

The formula 
$$
Pr[\tilde{b}=0|\tilde{b}=b] = \frac{Pr[\tilde{b}=0 \land \tilde{b}=b]}{Pr[\tilde{b}=b]} = \frac{Pr[\tilde{b}=0] \cdot \frac{1}{2}}{\frac{1}{2}} = Pr[\tilde{b}=0]
$$

shows that conditioning on the event $\tilde{b} = b$ does not change the distribution of $\tilde{b}$. This means the simulator can generate samples and reject those where $\tilde{b} \neq b$, and the accepted samples still follow the correct distribution.

Thus, the simulator effectively uses rejection sampling to produce a simulated transcript whose distribution is indistinguishable from the real interaction, ensuring zero-knowledge.

In summary:

- The simulator samples candidate views.
- It rejects those that don't meet the verifier's challenge condition.
- The accepted samples have the correct distribution.
- This is why the simulator's operation is described as rejection sampling.