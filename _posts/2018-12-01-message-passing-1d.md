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

Let us define a state vector $$\boldsymbol{s} = (p_{ \uparrow }, p_{ \downarrow }) = p_{\uparrow} \uparrow + p_{\downarrow} \downarrow $$ which describes the probability of being in a certain spin state. For our initial spin $$ \boldsymbol{s}_0 $$ $$ p_{\uparrow} = 1 $$ and $$ p_{\downarrow} = 0$$. After going through one of the channels we have the following recursion between spins on neighbouring sites

$$ \boldsymbol{s}_n = W \boldsymbol{s}_{n-1} \qquad \qquad W = \pmatrix{1 - f & f \\ f & 1 - f} $$

So what is the probability of a specific spin config conditionally on the first spin? Lets further define some projection operators  that will project a state into the $$\uparrow$$ or $$\downarrow$$ configuration.

$$ P_{\uparrow} = \pmatrix{1 & 0 \\ 0 & 0} \qquad \qquad P_{\downarrow} = \pmatrix{0 & 0 \\ 0 & 1} $$ 

So if the spin config in order after the seed spin is $$ [\Updownarrow] = \uparrow \downarrow \uparrow ... \uparrow $$ the the probability of the configuration should be

$$ \mathcal{P} ( [ \Updownarrow ] ) = P_{\uparrow} W ... W P_{\uparrow} W P_{\downarrow} W P_{\uparrow} W \boldsymbol{s}_0 $$.

In terms of the spin variables $$ s_n = \pm 1 $$

$$ \mathcal{P} ( [ \Updownarrow ] \vert  \boldsymbol{s}_0 ) =\frac{ \boldsymbol{s}_0 \cdot  W Q(s_{N-1}) W ... W Q(s_3) W Q(s_2) W Q(s_1) W \boldsymbol{s}_0}{\boldsymbol{s}_0 \cdot W^n \boldsymbol{s}_0} \qquad Q(s) = \frac{1}{2} \mathbb{1} + \frac{1}{2} s \sigma_z $$.

From this point you can argue by analogy that this form is identical to the transfer matrix representation of the 1D Ising spin chain. To see this note that the $$Q(s)$$ matrices are essentially selecting for specific compoenents of the neighbouring $$W$$ matrices. 


$$ \mathcal{P}( [ \Updownarrow ] \vert \boldsymbol{s}_0) = \frac{W_{s_0 s_{N-1}} W_{s_{N-1} s_{N-2}} ... W_{s_{1} s_0} }{\mathcal{N}}$$ 

 For an unbiased ising Hamiltonian $$ - \beta \mathcal{H} = K \sum s_{i} s_{i+1}$$ the transfer matrix matrix form of the Boltzmann distribution takes the form



$$ \mathcal{P}_{\text{Boltz}}( [ \Updownarrow ] ) = \frac{T_{s_0 s_1} T_{s_1 s_2} ... T_{s_{N-1} s_0} }{\mathcal{Z}} \qquad T = \pmatrix{e^{K} & e^{-K} \\ e^{-K} & e^{K}}$$
 
 $$f$$, which is a measure of the information channel noise, should therefore be related to the spin coupling, and we can basically just see that $$ f = \frac{1}{1 + e^{2K}} = n_{\text{Fermi}}(2K) $$. So if $$f < 1/2$$ (good transmission) then the chain is ferromagnetic whereas if $$f > 1/2 $$ (poor transmission) then the chain is antiferromagnetic. The extremes also makes sense in this correspondence.

Above we've shown that we can see a set of ising spins subject to some interaction of thermal bath can be built up from a sequence of directed information channels. Through this link, we can then use the tools of information theory to analyse known features of the distribution. The <b>Data Processing Theorem</b> (DPT) , which says that the mutual information between input and output of an information channel should only decrease after going through more channels, gives a nice explanation of why you don't get system-wide ordering.

There are some other potentially interesting ideas to do with this rewriting, but more on this later. The most pressing question for me now is - how do I generalise the directed information channel geometry to describe 2D ising spins on a square lattice, in the presence of an equilibrium bath? From the informational point of view (if it still exists), how does the ordering emerge mathematically, especially since we still have to obey DPT? Graph theory seems like it would lend itself to this problem.

TE

References:

[1] David MacKay, <i> Information Theory, Inference, and Learning Algorithms </i>

[2] RJ Baxter, <i> Exactly Solved Models in Statistical Mechanics </i>
