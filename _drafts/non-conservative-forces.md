---
layout: post
title: Non-Conservative Forces
image: /img/hello_world.jpeg
tags: [classical mechanics]
math: true
---


<script src='https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/MathJax.js?config=TeX-MML-AM_CHTML' async></script>

Consider the basic force equation of classical mechanics

$$ m \frac{d^2 \boldsymbol{q}}{d t^2} =  \boldsymbol{F} $$

When $$ \boldsymbol{F}$$ is derived from the gradient of a potential $$- \nabla U$$, this system is integrable. We have at least one conserved quantity (the Hamiltonian $$ \mathcal{H} = \frac{1}{2} m \Big( \frac{d \boldsymbol{q}}{dt} \Big)^2 + U$$) and the dynamics is restricted to some surface of constant energy in phase space. Once the Hamiltonian is known many things open up. We can easily write the equilibrium probability of the systems energy given it is connected to a bath at a certain temperature (via Boltzmann weight). It also it easy to quantize a classical system once you have the Hamiltonian - the procedure is merely promoting the dynamical variables to quantum operators.

A lot of this doesn't hold for more general forces. If $$ \nabla \times \boldsymbol{F} \neq \boldsymbol{0}$$ then we we have a <i> non-conservative force</i> i.e one which can't be written as the gradient of some potential function. An example would be $$(x^2yz, y^2 + x, z^2)$$. This situation is tricker as in general you will not be able to find a Hamiltonian.  However, we still wish to do the same things as in the Hamiltonian systems - talk about the equilibrium distributions, quantize etc etc.


Let's for the moment consider 3-dim space. Decompose $$\boldsymbol{F} = \boldsymbol{q} \times \boldsymbol{f}_1 + g(\boldsymbol{q}) \boldsymbol{q} $$ and further impose $$\boldsymbol{f}_1 \cdot \boldsymbol{q} = \boldsymbol{0}$$. $$\boldsymbol{f}_1$$ and $$g$$ are uniquely defined in terms of the given $$\boldsymbol{F}(\boldsymbol{q} ) $$.In the case where $$g = g(q^2)$$ (some sort of rotational symmetry overlain with an aziumuthal vector field, $f$_1 may have further restrictions due to hair ball etc etc) then we can see that the second term is really a gradient of a potential, namely $$ \mathcal{K} = - \frac{1}{2} \int^{q^2} g(x) dx $$.

Inspired by the Hamiltonian framework we can rewrite as two equations

$$ \frac{d \boldsymbol{q}}{dt} = \boldsymbol{p}/m $$

$$ \frac{d \boldsymbol{p}}{dt} = \boldsymbol{q} \times \boldsymbol{f}_1  - \nabla \mathcal{K}$$


Consider a subset of possible forces $$ \boldsymbol{F} = \nabla \times \boldsymbol{f} $$. Call $$\boldsymbol{f}$$ the <i>vector potential</i> of $$\boldsymbol{F}$$, and take it to be divergenceless without loss of generality (gauge-like freedom). Clearly it must also not be a conservatove vector field. The non vanishing curl condition then gives us that $$ \nabla^2 \boldsymbol{f} \neq \boldsymbol{0}$$.

 
$$ m \frac{d^2 \boldsymbol{r}}{d t^2} =  \nabla \times \boldsymbol{f} $$



In the langauge of differential geometry, Hamiltonian mechanics on a symplectic manifold (those with a closed 2-form).


References:

[1] M Berry and  P Shakula, <i>Classical Dynamics with curl forces, and motion driven by time-dependent flux </i> , J Phys A Math Theor <b>45</b> (2012)

[2] 
