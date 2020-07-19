---
layout: post
title: Entropy post XOR
image: /img/hello_world.jpeg
tags: [cryptography, probability]
math: true
---


<script src='https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/MathJax.js?config=TeX-MML-AM_CHTML' async></script>

The XOR of two bit strings is a fundamental operation in computational logic and cryptography. For example, when implementing a One Time Pad, we encode a message and secret key as bytes and XOR both of these together.

A fundamental fact often used is that the result of a completely random bitstring XOR'ed against another bitstring, with any distribution, yields another completely random bitstring. This is easy to reason - suppose we have one length-$$\ell$$ bitstring $$r = \{0,1\}^{\ell}$$. Each bit is an iid RV which takes the value 0 or 1 with equal probability. Let $$m$$ be any other bit string of the same length, with arbitrary distributions on each bit. Consider the logic table for the first bits XOR'ed together:

$$r$$[0] | $$m$$[0] | $$r[0] \oplus m[0]$$ | prob. |
1	| 1	| 0	|$$p_1/2 $$|
0	| 1	| 1	|$$ p_1/2$$|
1	| 0 	| 1	|$$ p_0/2$$|
0	| 0	| 0	|$$p_0/2$$ |

We can see the output is uniform distributed on the output bit, regardless of the distribution of the bitstring $$m$$. Intuitively this makes some sense, the randomness stored in $$r$$ is not diminished when combined (in a reversible way) with another source of randomness. A uniformly distibuted bit has maximal "randomness", so the amount of randomness also can't increase by adding another source of randomness. To be more precise, the appropriate measure of "randomness" is the Shannon entropy

$$ H_2(p) = -\big( p \ln(p) + (1-p) \ln(1-p) \big) $$

What if we have two bit strings which are to be XOR'ed, but neither of them are uniformly random? From the above argument we don't ever expect the entropy to decrease, but since neither bit is maximally entropic there is room for the result to be "more random". Let us make this more concrete.

Suppose we once again have two bitstrings of length $$\ell$$, both of which have iid's determining the value of each of their bit according to different ditributions. Call the strings $$x_i$$ with probability of a 1 $$p_i$$ for $$i$$=A,B. Their resulting bitstring after XOR will be called $$x_C$$. The probability of 1 on the first bit of $$x_C$$ is

$$
\begin{equation}
	p_C = p_A(1-p_B) + p_B(1 - p_A) = p_A + p_B(1 - 2p_A)
\end{equation}
$$

Since $$p_C$$ is a wighted average between two probabilites, its value will be mean regressing i.e it will get closer to 0.5. As the Shannon entropy has a global maximum at $$p=1/2$$ this means the entropy of the distribution will increase. So two biased, uncorrelated distributions can be combined to produce a more uniform, more "random" one. No comment on whether this a good idea in practice.

(These statements could be see in terms of inequalities on the entropy itself. $$ H(X_1) \leq H(X_1, X_2)$$ states that upon mixing the inputs, the entropy can't decrease.)


