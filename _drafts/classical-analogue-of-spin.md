---
layout: post
title: Classical Analogue of Spin through Differential Geometry
image: /img/hello_world.jpeg
tags: [quantum mechanics, classical mechanics, differential geometry]
math: true
---


<script src='https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/MathJax.js?config=TeX-MML-AM_CHTML' async></script>

Some features of quantum physics, at a passing glance, seem analogous to some corresponding classical system from a phenomenological point of view. Others aspects are free of any classical analogue for us to exploit for intuition. The dynamics of a quantum spin is often an example of a non intuitive quantum effect with no classical analogue. The spin components obey the commutation relation

$$
[S_i, S_j] = i \epsilon_{ijk} S_k
$$

Although this is of course a truly quantum effect, it is untrue that there is no classical analogue - it just requires differential geometry. The following closely mirrors the book <i> Mathematics for Physics </i> by michael Stone and Paul Goldbart.

Typically when makinga connection between classical mechanics and quantum mechanics we compare brackets. In quantum mechanics we have a commutator whereas in classical mechanics we have the Poisson bracket 

$$ \{ f, g \} = \sum_{i} \Bigg( \frac{\partial f}{\partial q_i}\frac{\partial g}{\partial p_i} - \frac{\partial f}{\partial p_i}\frac{\partial g}{\partial q_i} \Bigg) $$

And to pass from classical to quantum behaviour we usually just perform $$ \{ \cdot , \cdot \} \rightarrow -i [ \cdot, \cdot ] $$. As a basic exmaple $$ \{q_i, p_j \} = \delta_{ij}$$ which passes to $$ [q_i, p_j] = i \delta_{ij } $$ under the quantisation procedure. Even the Hamiltons equations of motion can be quantised in this way.

Consider a classical unit vector in 3 dim, parametrised by spherical angles in the usual way $$ S_x = \cos \phi \sin \theta $$, $$ S_y = \sin \phi \sin \theta $$, and $$ S_z = \cos \theta $$. Define a symplectic 2-form on this space $$\omega =  \sin \theta d \theta d\phi$$.
