---
layout: post
title: Curl Forces in Cyclic Protocols
image: /img/hello_world.jpeg
tags: []
math: true
---


<script src='https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/MathJax.js?config=TeX-MML-AM_CHTML' async></script>

Suppose we have the followinf Fokker plank equation in a confined system

$$
\nabla \cdot \Big( \vec F \mathcal{P} + D \nabla \mathcal{P} \Big)
$$

assuming a zero flux in space (from confinement) we can write straight away the equation

$$
\rightarrow 0 = {\vec F} \mathcal{P} + D \nabla \mathcal{P} \tag{1} \label{eqn:FP}
$$

We can decompose any vector field into a curl-free and divergence components i.e $$ \vec F = \nabla f_s + \nabla \times \vec f_v $$. We can similarly solve Eq \ref{eqn:FP} by splitting $$ \mathcal{P} = \mathcal{P}_s + \mathcal{P}_v$$ for each part of the force. The part corresponding to a conservative fector field can be integrated exactly. The curl component solves the equation


$$
0 = ( \nabla \times \vec f_v ) \mathcal{P}_v + D \nabla \mathcal{P}_v \tag{2} \label{eqn:flux-free}
$$

Take the divergence of the equation $$  0 = ( \nabla \times \vec f_v ) \cdot \nabla \mathcal{P}_v + D \nabla^2 \mathcal{P}_v $$ which upon substituing Eq \ref{eqn:flux-free}


$$
0 = - D^2 \nabla^2 \mathcal{P}_v + \vert \nabla \times \vec f_v \vert^2 \mathcal{P}_v \tag{3} \label{eqn:TISE}
$$

Note this is merely the <b> Time-Independent Schrodinger Equation (TISE) </b>, and the non-conservative part of the force acts as a quantum potential.  Many solution methods, approximate and exact, are known for this style of equation. The key difference is that unlike in the quantum case, here we will normalise using the <b> $$L_1$$ norm </b>  (rather than the $$L_2$$).

At this point let's consider a specific example for concreteness. Let $$ \vec F = 
