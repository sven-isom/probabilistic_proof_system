---
tags: 
Created: 2025-08-09 14:26
aliases: 
related: 
link: 
Type:
---
The **butterfly algorithm** is a famous dataflow pattern used to compute the **[[FFT|Fast Fourier Transform]] (FFT)** and similar divide-and-conquer transforms (like Walsh–Hadamard transform) efficiently.
It gets its name because, if you draw the data dependencies, the connections between stages look like butterfly wings.

## 1 Context
The FFT computes the **Discrete Fourier Transform (DFT)**:
$$
X_k = \sum_{n=0}^{N-1} x_n \cdot \omega_N^{nk}
$$
where $\omega_N = e^{-2\pi i / N}$ is an $N$-th root of unity.
Naively, this costs $O(N^2)$ operations.
The Cooley–Tukey FFT algorithm reduces it to $O(N \log N)$ by recursively splitting the computation into halves — **this recursion is implemented using butterflies**.

## 2 What a butterfly operation is
A **butterfly** takes two complex numbers $(a, b)$ and a twiddle factor $w$ (a root of unity) and outputs:
$$
u = a + w \cdot b
$$
$$
v = a - w \cdot b
$$
These are the **combined results** from two subproblems in the FFT recursion.

## 3 Why it’s called “butterfly”
If you draw the dataflow for $N=8$ over the $\log_2 N$ stages:
- Inputs start on the left,
- Outputs end on the right,
- Lines cross between stages forming an “X”,
- Each pair of crossings with their connections looks like a butterfly’s wings.
Example diagram for 4-point FFT stage:
```
a ----\ /---- u
X-----X
b ----/ \---- v
```
The “cross” represents the butterfly computation.

## 4 Algorithm structure
For $N$ a power of 2:
```
function FFT(x):
N = length(x)
if N == 1:
return x
X_even = FFT(x[0], x[2], x[4], ...)
X_odd = FFT(x[1], x[3], x[5], ...)
for k = 0 to N/2 - 1:
t = ω_N^k * X_odd[k] // twiddle factor multiply
X[k] = X_even[k] + t
X[k+N/2] = X_even[k] - t
return X
```
The last `for` loop is exactly the **butterfly stage**.

## 5 Properties
- **Time complexity**: $O(N \log N)$.
- **Parallelism**: Each butterfly in a stage is independent → can be computed in parallel.
- **Circuit viewpoint**: An FFT circuit has $\log N$ layers, each made of $N/2$ butterflies.

## 6 Where it appears outside FFT
- Fast Walsh–Hadamard Transform (FWHT).
- Polynomial multiplication via FFT.
- Certain error-correcting codes (e.g., Reed–Solomon decoding).
- In complexity theory, the FFT/butterfly structure is a classic example of a **shallow, highly regular circuit** that is **log-space uniform**.

If you want, I can also show **how the butterfly algorithm corresponds to an $O(\log N)$-depth circuit**, which is exactly the kind of **shallow circuit** your lecturer refers to in deIP settings. Would you like me to prepare that?