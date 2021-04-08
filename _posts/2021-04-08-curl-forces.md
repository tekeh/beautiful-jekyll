---
layout: post
title: Hamiltonian Curl Forces
image: /img/hello_world.jpeg
tags: []
math: true
---


<script src='https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/MathJax.js?config=TeX-MML-AM_CHTML' async></script>

It is known that _conservative force_, defined as those which are the gradient of a scalar function, are curl free. This is a consequence of basic vector calculus

$$
\nabla \times {\bf F}_{\rm cons} = - \nabla \times \nabla V = 0
$$

The motion of a particle under conservative motion (motion arising under the action of a conservative force) can equally be described in the Hamiltonian mechanics framework (reviewed within [here](https://tekeh.github.io/2021-03-05-funky-symplectics/)). This Hamiltonian is most often in the form of kinetic terms + potential terms, namely

$$ \label{eq:hamiltonian} \tag{1}
\mathcal{H} = \frac{ {\bf p}^2}{2}+ V({\bf r})
$$

when considering just one particle in _d_-dim. Hamiltons equations give

$$
\dot{\bf r} = \frac{\partial \mathcal{H}}{\partial {\bf p}} = {\bf p}
$$

$$
\dot{\bf p} = -\frac{\partial \mathcal{H}}{\partial {\bf r}} = -\nabla V
$$

and when combined imply that the equaton of motion for $${\bf r}$$ alone is

$$ \label{eq:ode} \tag{2}
 \ddot {\bf r} = -\nabla V({\bf r})
$$

Note this choice isn't unique - we could have easily defined, for example, the Hamiltonian

$$
\mathcal{H}' = \frac{ {\bf p'}^2}{2 \eta}+  \eta V({\bf r'})
$$

 for constant $$\eta$$, which would also lead us to \eqref{eq:ode}. However, one should note that the definition of the conjugate momenta changes with this rewriting - the Hamiltonian still represents the systems true energy (up to a factor of $$\eta$$).

Some equations of motion, admittedly often arising from some effective description, may contain forces which are non-conservative. Clearly taking a Hamiltonian of the form of \eqref{eq:hamiltonian} can not lead to a force with a curl. Despite this the phase space of $${\bf r}$$ and $${\bf v = \dot r}$$ is still volume-preserving since

$$
\nabla_{\bf r} \dot {\bf r} + \nabla_{\bf v} \dot{\bf v} = \nabla_{\bf r} {\bf v} + \nabla_{\bf v} {\bf F}({\bf r}) = 0
$$

which is a statement of Liouville's theorem when the system is Hamiltonian with conjugate momenta given by $${\bf p = \dot r}$$, but holds despite the form of the conjugate momenta (or the existence of a Hamiltonian). Thus the dynamics are non-dissipative too. [2]

Can we create other forms of the Hamiltonian that will produce a desired (non curl-free) force? The answer is maybe. We can immediately see that there are some choices of Hamiltonian that give us forces with some amount of curl. Take for example the Hamiltonian in [1] with anisotropic kinetic energy

$$
\mathcal{H}_1 = \frac{1}{2} \alpha p_x^2 + \beta p_x p_y + \frac{1}{2} \gamma p_y^2 + V(x,y)
$$

The equation of motion for $${\bf r} = (x,y, z)$$ is

$$ \label{eq:curl-ode} \tag{3}
\ddot {\bf r} = - {\bf M} \nabla V \qquad {\rm where\ }\quad  {\bf M} = \begin{pmatrix} \alpha & \beta & 0 \\
										\beta & \gamma & 0 \\
										0 & 0 & 0
\end{pmatrix} 
$$

The $$z$$ directed curl is given by

$$
(\alpha - \gamma) \partial_{xy} V + \beta ( \partial_{yy} -\partial_{xx})V
$$

which is non zero for general $$V$$, so at least _some_ curl forces can be embedded in a Hamiltonian without doing crazy things like doubling the degrees of freedom. The Hamiltonian is obviously conserved throughout the dynamics. We confirm this by playing around with \eqref{eq:curl-ode}. Projecting down to $$(x,y)$$, and assuming $${\bf M}$$ invertible

$$
\begin{equation}
\begin{aligned}
	{\bf M}^{-1} \ddot {\bf r} &= - \nabla V \\
	\dot {\bf r}  \cdot {\bf M}^{-1} \ddot {\bf r} &= - \dot {\bf r} \cdot \nabla V \\
	\implies 0 &= \frac{d}{dt} \Big( \frac{1}{2} \dot{\bf r}^T {\bf M}^{-1} \dot {\bf r} + V({\bf r}) \Big)

\end{aligned}
\end{equation}
$$

which, after the identification of $$\dot {\bf r} = {\bf M} {\bf p}$$, is equivalent in form to the Hamiltonian.

Another pertinent example is of a **pure shear force**

$$
\ddot {\bf r} = f(y) {\bf e}_x
$$

This force has some curl for general $$f$$. Take

$$
\mathcal{H}_{\rm shear} = \frac{1}{2} p_{x}^2 + p_{y} v_{y}(0) - x f(y)
$$

Hamilton's equations yield

$$
\dot p_x = f(y) \qquad \dot x = p_x
$$

$$
\dot p_y = x f'(y) \qquad \dot y = v_y(0)
$$

which leads to 

$$
\ddot x = f(y) \qquad \ddot y = 0
$$

as required. Again the Hamiltonian is conserved, although its form is sufficiently foreign that one is hesitant to use the term "energy" to describe its constant value. Can verify constancy directly

$$
\begin{equation}
\begin{aligned}
\dot{\mathcal{H}} &= \dot{p}_x p_x + \dot{p}_y v_y(0) - \dot{x} f(y) - \dot{y} x f'(y) \\
		&= \dot{x} f(y) + x f'(y) v_y(0) -\dot{x} f(y) - v_y(0) x f'(y) \\
		&= 0
\end{aligned}
\end{equation}
$$

The Hamiltonian has the peculiarity of depending on an initial condition.

A final example - **2-dim propelled motion**

$$
\ddot \theta = 0 
$$

$$
\ddot {\bf r} = v {\bf n}(\theta) - \nabla V({\bf r})
$$

The dynamics is roughly that of a particle being pushed around at a constant self propulsion speed $$v$$, with an evolving angular direction $$\theta \in [0, 2\pi)$$.

Consider

$$
\mathcal{H}_{\rm prop} = \frac{1}{2} {\bf p \cdot p} + v_{\theta}(0) p_{\theta} - v {\bf r \cdot n} + V({\bf r}) 
$$

yielding

$$
\dot {\bf r} = {\bf p} \qquad \dot{\bf p} = v {\bf n} - \nabla V
$$

$$
\dot{\theta} = v_{\theta}(0) \qquad \dot{p}_{\theta} = - v {\bf r} \cdot {\bf e}_{\phi}(\theta)
$$

And yet again we have defined an effective Hamiltonian for the dynamics.

**[References]**

**1.** Berry, M. V. & Shukla, P. Hamiltonian curl forces. Proc. R. Soc. A. 471, 20150002 (2015).

**2.** Berry, M. V. & Shukla, P. Classical dynamics with curl forces, and motion driven by time-dependent flux. J. Phys. A: Math. Theor. 45, 305201 (2012).

