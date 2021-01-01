---
layout: post
title: Random Decreasing Sequence
image: /img/hello_world.jpeg
tags: [probability]
math: true
---


<script src='https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/MathJax.js?config=TeX-MML-AM_CHTML' async></script>

Suppose we have a decreasing sequence defined in the following way. First consider a random number generator $$R$$ that takes a non-negative integer, $$n$$, as input and returns one of $$\{0,1,...,n-1\}$$, the choice being made uniformly at random. Now pick some integer $$x_0$$ and define a sequence of $$x_i$$ by the recurrence relation:

$$
x_i = R(x_{i-1}) \qquad i \geq 1
$$

Clearly the sequence is strictly decreasing. Moreover it has some finite, non-deterministic running time ($$x_i=0$$ is an absorbing state). How long do we expect it to run for, given some (large) initial integer seed $$x_0$$?

We can solve this fairly rapidly using the **tower rule**. Let us call $$\mathcal{E}_r$$ the expected running time for $$x_{0} = r$$. Then

$$
\begin{equation}
\begin{aligned}
\mathcal{E}_{N} &= 1 \cdot \frac{1}{N} + \frac{1}{N} \sum_{k=1}^{N-1} (1 + \mathcal{E}_k) \\
	& = 1 + \underbrace{\frac{1}{N} \sum_{k=1}^{N-1} \mathcal{E}_k}_{\mathcal{S}_{N-1}}
\end{aligned}
\end{equation}
$$

The labelled term $$S_N$$ has a rather simple recursion relation itself,

$$
\begin{equation}
\begin{aligned}
	\mathcal{S}_{m-1} &= \frac{1}{m} \sum_{k=1}^{m-1} \mathcal{E}_k \\
			  &= \frac{1}{m} \mathcal{E}_{m-1} + \frac{m-1}{m} \frac{1}{m-1}\sum_{k=1}^{m-2} \mathcal{E}_k \\
			  &= \frac{1}{m} (1 + \mathcal{S}_{m-2}) + \frac{m-1}{m} \mathcal{S}_{m-2} \\
	\implies \mathcal{S}_{m-1} &= \frac{1}{m} + \mathcal{S}_{m-2}
\end{aligned}
\end{equation}
$$

$$\mathcal{S}_1 = \frac{1}{2}$$, so we can clearly see that $$\mathcal{S}_m = \sum_{k=2}^{m+1} \frac{1}{k}$$ which gives us $$\mathcal{E}_{x_0} = \sum_{k=1}^{x_0} \frac{1}{k}$$. For large initial seed this is $$\approx \log(x_0)$$. 
