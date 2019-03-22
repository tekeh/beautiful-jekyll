---
layout: post
title: Stress Functions 
image: /img/hello_world.jpeg
tags: [rheology, tensors, classical mechanics]
math: true
---


<script src='https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/MathJax.js?config=TeX-MML-AM_CHTML' async></script>

In this post we'll discuss a certain description of stresses in 2D mechanical systems, which has proved useful in the study of granular systems and other such packings in mechanical equilibrium. It is called the <b> Airy stress function </b>, $$\psi$$.

Consider the stress tensor of an arbitrary 2D system $$ [\hat \sigma ] = \sigma_{ij}$$ which is a field over space (and time, if you wish, although we will look at the static case). Force balance is given by a divergenceless tensor  $$  \nabla \cdot \hat \sigma = 0 $$ (as the normal forces on a volume should balance) and torque balance, which must be considered in frictinal systems, requires the tensor to be symmetric $$ \sigma_{ij} = \sigma_{ji}$$

The airy stress representation comes from us noticing that both of these force balance conditions can be met by writing

$$
\sigma_{ij} = \epsilon_{im} \epsilon_{jn} \partial_{m} \partial_{n} \psi \tag{1} \label{eqn:airy-stress}
$$ 

For some scalar field $$\psi$$. $$\epsilon_{ij}$$ is the totally anti-symmmetric tensor with $$\epsilon_`{12} = 1$$. The airy stress function is a <b> gauge field </b>, and so there is from freedom in it's representation ( similar to the freedom in defining a vector potential $${\bf A}$$ from a $${\bf B}$$ field in electromagnetism). As there are two derivatives in the Eq \ref{eqn:airy-stress} the stress is invariant under the transformation

$$
\psi \rightarrow \psi + {\bf a} \cdot {\bf r} + b
$$

for constant $${\bf a}, b$$. Such transformations clearly form a Lie group, called a <b> gauge group </b>.  This function has been used extensively to study 2D elastic systems, and in these settings $$\psi$$ usually is determined by minimisaing some elastic energy functional. The contruction is general enough to handle even granular packings (under something something smoothness assumptions no doubt) which are not in thermal equilibrium and don't always deform elastically. 

For 3D packings the representation is follows analogosly.

$$
\sigma_{il} = \epsilon_{ijk} \epsilon_{lmn} \partial_{j} \partial_{m} \Psi_{kn}
$$

Where $$\hat \Psi$$ is called the <b> Beltrami stress tensor </b>. The extra dimension saw us promote a scalar field to a rank 2 tensor field. By construction mechanical equilibrium is still satisfied. As before there is some gauge freedom, but this time it is a local symmetry transformation.

$$
\Psi_{ij} \rightarrow \hat \Psi_{ij} + \partial_i p_j({\bf r})
$$

For any vector field $${\bf p}$$. The gauge freedome is usually fixed using either the Maxwell gauge ($$ \Psi_{ij} = \delta_{ij} \phi_j$$) or the Morera gauge ($$\Psi_{ij} = 0 \text{ if } i = j$$) although of course there you can make up any gauge you like as long as it account for the right number of redundant DOFs.

We observe living in 3 spatial dimensions, but in light of [some work](https://arxiv.org/abs/1810.01213) that focuses on infinite dimnesional glasses, it might be interesting to deduce properties of the representation when $$d$$ become larger, past the $$d=3$$ we live in. More to come.

References:

[1] Edwards field theory for glasses and granular matter, Eric DeGiuli  [link](https://) 

[2] Statistical mechanics framework for static granular matter, Silke Henkes and Bulbul Chakraborty [link](https://)

