---
layout: post
title: Message Passing in 1D
image: /img/hello_world.jpeg
tags: [information theory, probability]
math: true
---


<script src='https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/MathJax.js?config=TeX-MML-AM_CHTML' async></script>

Suppose we have a 1D array of N spins on a ring, which can be either $$\uparrow$$ or $$\downarrow$$. Suppose further that we fix one of the $$N$$ previously identical spins such that it is $$\uparrow$$. Now inagine that between each pair of spins is a directed information channel that aims to transfer the value of each spin to it's neighbour. All the channels are noisy with the same statistics, and because of this the input spin will have a probability $$f$$ of being flipped (independent of which way up it is). 

So we start with a spin $$\uparrow$$ at position $$0$$ and try to transmit this spin along the channels. Once we've got to the $$N-1$$th position we have some ordering of spins. What is the probability of seeing a specific spin configuration?

Let us define a state vector $$\boldsymbol{b} = (p_{ \uparrow }, p_{ \downarrow })$$ which describes the probability of being in a certain spin state. Further define $${\bf b}_{\uparrow}$$ and $${\bf b}_{\downarrow}$$ to be the state of being up or down with certainty, respectively. After going through one of the channels we have the following recursion between spins on neighbouring sites

$$ \boldsymbol{b}_n = W \boldsymbol{b}_{n-1} \qquad \qquad \hat W = \pmatrix{1 - f & f \\ f & 1 - f} $$

Further, we can write down the probability of a certain spin configuration. For the configuration $$ [\Updownarrow] = \uparrow ...\uparrow \downarrow \uparrow s_0  \equiv s_N ... s_3 s_2 s_1 s_0$$ with the first spin rightmost, the probability is

$$ \mathcal{P} ( [ \Updownarrow ] \vert {\bf s}_0) = \prod_{k=1}^N \mathcal{P}({\bf s}_k \vert {\bf s}_{k-1}) = \prod_{k=1}^{N} {\bf s}_k^T \hat W {\bf s}_{k-1} =  {\bf b}_{\uparrow}^T \hat W ... \hat W {\bf b}_{\uparrow}  {\bf b}^T_{\uparrow} \hat W {\bf b}_{\downarrow}  {\bf b}^T_{\downarrow} \hat W{\bf b}_{\uparrow}  {\bf b}^T_{\uparrow} \hat W \boldsymbol{s}_0 $$.


Define $$W_{ss'} = {\bf s}^T \hat W {\bf s'}$$. Then we could equivalently write


$$ \mathcal{P}( [ \Updownarrow ] \vert \boldsymbol{s}_0) = W_{s_N s_{N-1}} W_{s_{N-1} s_{N-2}} ... W_{s_{1} s_0} $$ 

Note here that since the states each spin site $${\bf s}_k$$ can take are finite, so the new $$W_{ss'}$$ act as components of a matrix. The probability is necessarily normalised.

By marginalising our product we can write the probability of a spin at site $$k$$ given the value at site $$l < k$$ straightforwardly 

$$
\mathcal{P}({\bf s}_k \vert {\bf s}_l) = {\bf s}_k W^{\vert k - l\vert} {\bf s}_l
$$

Okay.

If we think of this transfer probability as resulting from an effective channel, then what is the capacity of this channel? As a reminder, the capacity $$C$$ is the supremum of the mutual information $$I(X;Y)$$. This mutual information can be written explicitely (with some calculation)

$$
I({\bf s}_k; {\bf s}_l) = H_2\big(p_{\downarrow}^{l} [ 1 - g_{\vert k - l \vert}(\uparrow\uparrow)] + [1 - p_{\downarrow}^{l}] g_{\vert k-l \vert}(\uparrow\uparrow) \big) - H_2\big(g_{\vert k - l \vert}(\uparrow\uparrow) \big)
$$

Where $$g_x(ss') = {\bf b}_s W^x {\bf b}_{s'}$$. This is maximised using a uniform input distribution at site $$l$$, which leads to a capacity of

$$ C_{kl} = \sup_{\mathcal{P}({\bf s}_k)} I({\bf s}_k;{\bf s}_l) = 1 - H_2(g_{\vert k - l \vert}(\uparrow\uparrow)\big) $$ 

And we can also write $$g$$ on terms of the original flip probability for neighbours using a recursive method.

$$g_{\vert k - l \vert}(\uparrow\uparrow) = \frac{1}{2} (1 + (1-2f)^{\vert k - l \vert})$$

The <b>Data Processing Theorem</b> (DPT) , which says that the mutual information between input and output of an information channel should only decrease after going through more channels, so all this is consistent.

 For an unbiased ising Hamiltonian $$ - \beta \mathcal{H} = K \sum s_{i} s_{i+1}$$ the transfer matrix form of the Boltzmann distribution takes the form

$$ \mathcal{P}_{\text{Boltz}}( [ \Updownarrow ] ) = \frac{T_{s_0 s_1} T_{s_1 s_2} ... T_{s_{N-1} s_N} }{\mathcal{Z}} \qquad T = \pmatrix{e^{K} & e^{-K} \\ e^{-K} & e^{K}}$$
 
 $$f$$, which is a measure of the information channel noise, should therefore be related to the spin coupling, and we can basically just see that $$ f = \frac{1}{1 + e^{2K}} = n_{\text{Fermi}}(2K) $$. So if $$f < 1/2$$ (good transmission) then the chain is ferromagnetic whereas if $$f > 1/2 $$ (poor transmission) then the chain is antiferromagnetic. The extremes also makes sense in this correspondence.

This is all just set up for tackling the case of 2D.


References:

[1] David MacKay, <i> Information Theory, Inference, and Learning Algorithms </i>

[2] RJ Baxter, <i> Exactly Solved Models in Statistical Mechanics </i>
