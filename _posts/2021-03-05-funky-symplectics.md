---
layout: post
title: Funky Symplectics
image: /img/hello_world.jpeg
tags: []
math: true
---


<script src='https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/MathJax.js?config=TeX-MML-AM_CHTML' async></script>

Hamiltonian mechanics occurs on a symplectic manifold, but what does that mean? Well, it means that the manifold created by the coordinate variables is equipped with a **differential two-form**. Let's zoom in on this.

The canonical coordinates for a mechanical system are denoted by $${\bf \xi} = (q_i, p_i)$$ where $$q_i$$ are the _generalised coordinates_ and $$p_i$$ are their associated _conjugate momenta_. The equations of motion are given by _Hamilton's equations_. 

$$
\dot{p_i} = - \frac{\partial \mathcal{H}}{\partial q_i}
$$

$$
\dot{q_i} = \frac{\partial \mathcal{H}}{\partial p_i}
$$

A function $$f = f(q_i,p_i)$$ has a time derivative given in terms of the _poisson bracket_:

$$
\frac{df}{dt} = \frac{\partial f}{\partial t} + \{f, \mathcal{H}\}
$$

where $$\{f, g \} = \sum_{i=1}^n \Big( \frac{\partial f}{\partial q_i} \frac{\partial g}{\partial p_i} - \frac{\partial f}{\partial q_i} \frac{\partial g}{\partial p_i} \Big)$$.

Liouvelle's theorem falls out of the Hamiltonian formulation, and tells us that the phase space evolves as an incompressible fluid. Another way of saying this is that the volume element $$dV = \prod_{i=1}^N dq_i dp_i$$ will be of constant magnitude, even if the shape distorts during the flow.

All of these equations and results can be recast into the language of differential geometry.

Our manifold $$\mathcal{M}$$ is of dimension $$2n$$, the coordinates being $$ {\bf \xi} = (q_i, p_i)_{i=1..n}$$. Our hope is to describe the time evolution of our coordinates as a flow on this manifold. To do this we need to connect different points of the manifold to one another, so calculus seems necessary. And in differential geometry this is handled using differential forms.

Define a two form by (Einstein summation assumed from here)

$$
\omega = \frac{1}{2} \tilde \omega_{\alpha \beta} d\xi^{\alpha} \wedge d\xi^{\beta}
$$

and a velocity vector field using our canonical coordinates by

$$
v = \dot q_i \frac{\partial}{\partial q_i} + \dot p_i \frac{\partial}{\partial p_i}
$$

Then the hamiltonian flov can be written by

$$ \label{eq:differential-hamiltonian-flow} \tag{1}
dH = - \omega(v, )
$$

when $$\omega$$ is in _Darboux form_ $$ dp^1 \wedge dq^1 +  dp^2 \wedge dq^2 + ...  dp^n \wedge dq^n$$ then we get exactly Hamiltons equations above. The symplectic matrix $$\tilde \omega$$ can be written in block form as below.

$$
\tilde \omega = \begin{pmatrix}
{\bf 0} & {\bf I} \\
-{\bf I} & {\bf 0} \\
\end{pmatrix}
$$

Within differential geometry there exists a natural volume element, derived from the symplectic form $$\omega^n/n! = \det(\tilde\omega) \bigwedge_{i=1}^n dp^i \wedge dq^i $$. This volume form (which describes a volume in phase space) is _invariant_. This is a recasting of Liouvelle's theorem, which says that phase space volumes are incompressible and evolve analogously to an incompressible fluid.

All of the above is a recasting of the Hamiltoniain framework. However, not that we have this recasting we can imagine how it can be extended naturally. Hamilton's equations of motion are great, and they can describe a great many systems, but their form is restrictive. It is impossible to represent certain types of forces in the vanilla framework. This is fine - in such cases we would typicaly work on the level of the equations of motion without any cosideration of a Hamiltonian or symplectic manifold. But the Hamiltonian formalism is quite a nice tool, and there are strong theorems attached to it (Liouvelle). As well as that there exists great tools for analysing symmetry within it (Noether, or whatever is to Hamiltonians what Noether is to Lagrangians). So maybe there is a way to use Hamiltonians in more peculiar situations?

Let us consider on augmentation - we could imagine a more general symplectic matrix. The idea would be that changing $$\omega$$ would allow Eq \ref{eq:differential-hamiltonian-flow} to express more general dynamical equations. As long as we can pick an appropriate $$H$$ and $$\omega$$, we can still use the power of Hamiltonian dynamics. Therefore,  consider

$$
\hat \omega = \begin{pmatrix}
{\bf \Omega}^{(q)} & {\bf S} \\
-{\bf S}^T & {\bf \Omega}^{(p)} \\
\end{pmatrix}
$$

Then the two form can be written

$$
\omega = S_{\alpha\beta} dp^{\alpha} \wedge dq^{\beta} + \Omega^{(q)}_{\alpha\beta} dq^{\alpha} \wedge dq^{\beta} + \Omega^{(p)}_{\alpha\beta} dp^{\alpha} \wedge dp^{\beta} 
$$

The natural volume is probably useful to know. In this case it is merely

$$
\det(\hat\omega) = \det({\bf \Omega}^{(q)} {\bf \Omega}^{(p)} + {\bf S}^T {\bf S } )
$$

Cool.

This will be applied to something in the future.

[//]: # Now for an application - an underdamped system  in 1-dim obeys the following ODE
[//]: # 
[//]: # $$
[//]: # m \ddot{r} = - \gamma \dot{r} + F(r) 
[//]: # $$
[//]: # 
[//]: # First we need to appreicate that for $$\gamma \neq 0$$, this equation has no Hamiltonian in the vanilla sense. (Think about the evolution of a phase space element for $$F=0$$. It's collapse to a line on $$p=0$$ shows that phase volume is not conserved)
[//]: # 
[//]: # $$
[//]: # \mathcal{L} = m(\dotr)^2/2 
[//]: # $$
[//]: # 
[//]: # which can be rewritten in terms of two 1st order SDEs
[//]: # 
[//]: # $$
[//]: # \dot{r} = \frac{\partial E(p)}{\partial p} = p/m
[//]: # $$
[//]: # 
[//]: # $$
[//]: # \dot{p} = - \gamma p  - \frac{\partial V(r)}{\partial r}
[//]: # $$
[//]: # 
[//]: # The second version makes the connection to the dynamical Hamiltonian formalism more explicit. Consider Hamiltons equations in phase space


