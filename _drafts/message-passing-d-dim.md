---
layout: post
title: Message passing d-dim
image: /img/hello_world.jpeg
tags: [statistical physics, information theory]
math: true
---


<script src='https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/MathJax.js?config=TeX-MML-AM_CHTML' async></script>

Previously, a loose connection between informational message passing and ordering in 1D ising spin chains was discussed. We left of wondering about the connection to higher dimensional spin systems. 


<h4>Hypercubic Lattice </h4>

Using the previous considerations it's possible to bound the position of the phase transition. suppose we are $$n$$ links away from the starting spin i.e the Manhattan distance ($$L_1$$) is $$n$$. Suppose we are at one of these sites, labelled $$ \boldsymbol{m} = ( m_1, m_2, ...., m_d)$$ where $$ \sum_k \vert m_k \vert = n$$. Choose the coordinate system so that $$M_k > 0$$ without loss of generality. The number of ways of reaching this site is

$$ \Omega(\boldsymbol{m}) = \pmatrix{ n \\ m_1} \pmatrix{n- m_1 \\ m_2} .. \pmatrix{ n - m_1 - ... - m_{d-1} \\ m_d } = \frac{n!}{m_1 ! m_2 ! ... m_d !}$$

Asymptotically we then get

$$ \Omega(\boldsymbol{m}) \sim \exp\Big( n \ln n - \sum_k m_k \ln m_k + o(\boldsymbol{m}) \Big) = \exp\Big( - n \sum_k p_k \ln p_k \Big)$$

Where we have defined $$p_k = m_k/n$$. The term in the exponent is clearly the entropy, which naturally falls out of a large deviation type approach presented here. We will use the Shannon informatinal entropy, which differs only by a factor.

Each time we traverse from one node to another we pick up a matrix multiplication, $$W$$ as defined in the previous post when considering the 1D system. the determinant of the matrix is $$ 1 - 2f$$. Thus, asymptotically, the term giving the probability of alignement between the an initial spin and one $$n$$ away 

$$ p_f \sim \Omega(\boldsymbol{m}) W^n p_i $$

So the size of the transfer is roughly $$ ( (1 - 2f) 2^{H(\boldsymbol{m})} )^n$$. For this term to not shrink as $$n \rightarrow \infty$$ we need $$f$$ to be at some critical value such that thte following eaqulity is satifiedor oversaturated for all positions at this distance. This is basically saying that there is some critical flip probability such that if we go below it we can sustain perfect ordering.

$$ ( 1 - 2f_c) 2^H \approx 1 $$

There will be higher order terms which contruibute corresponding to longer paths. Also, it is not necessarily clear that all paths should be wifghted the same or whether there is some specific adjacency over the graph which we should be considering paths with respect to. The above expression is just a rough heuristic. This leads to

$$ f_c = \frac{1 - 2^{-H}}{2} \leq \frac{1 - d^{-1}}{2}$$ 

Last time we built a correspondence between $$f$$ and the Ising model $$K$$. $$ f = ( 1 + e^{2K})^{-1} $$. This should still be valid as the correspondence is only due to the neighbour flip process and doesn't depend on the larger structure of the lattice. After a bit of algebra this acts as an upper bound on the transition temperature in $$d$$ dimensions (in units of the coupling strength).

$$ T_c < ( \tanh^{-1}(1/d) )^{-1} \quad d > 1$$

$$
\begin{array}{c|lcr}
d & T_c & ( \tanh^{-1}(1/d) )^{-1}& \text{ % error} \\
\hline
2 & 2.2692 & 1.8205 & -8 \\
3* & \href{https://arxiv.org/abs/cond-mat/9603013}{4.5115} & 2.8854 & 1+10i \\
4 & \href{https://www.hermetic.ch/compsci/thesis/chap3.htm}{6.68} & 3.9152 & 1+10i \\
5 & x.xxxx & 4.9326 & 1+10i \\
6 & x.xxxx & 5.9440 & 1+10i \\
\end{array}
$$



The mean field result for the ising critical temperature $$T_c = d$$ is valid in the limit of infinite dimensions. The result above recovers the same asymptotes for high dimensions. Bit shit so far though. Maybe we can bound from both directions? We would do this by considering a dual lattice and running the same argument.
