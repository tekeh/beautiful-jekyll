---
layout: post
title: ABP pdf
image: /img/hello_world.jpeg
tags: []
math: true
---


<script src='https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/MathJax.js?config=TeX-MML-AM_CHTML' async></script>


This is a calculation to determine the probability density of non-interacting, elliptical ABPs in a harmonic box trap.

The Fokker Plank (FP) is

$$
0 = \partial_x \Big( D\partial_x P + \mu \partial_x V P \Big) + \partial_{\theta} \Big( \tau^{-1} \partial_{\theta} P + \mu_r \partial_{\theta} U P \Big) 
$$

<b>In the wall</b>: Assume Boltzmann weighted

$$
P = \mathcal{Z}^{-1} e^{-\frac{\mu}{D} V - \mu_r \tau U}
$$

<b>In bulk</b> ($$ U=0 \, V=0 $$) use a series solution

$$ 
P = \frac{\rho_0}{2\pi} + \frac{1}{\pi} \sum_i a_n \cos n \theta \cosh\Bigg(\frac{n (x - x_w/2)}{\sqrt{D \tau}} \Bigg)
$$

Where we've used the symmetry about centre of the box.

Continuity of $$\mathcal{P}$$ spatially leads to matching at $$x=x_w$$

$$
\mathcal{Z}^{-1} \exp \big(-\lambda \kappa \mu_r \tau \cos(2\theta)/2 \big) = \frac{\rho_0}{2\pi} + \frac{1}{\pi} \sum_i a_n \cos n \theta \cosh\Bigg(\frac{n x_w}{2\sqrt{D \tau}} \Bigg) \label{eqn:dirichlet} \tag{(1)}
$$

Which upon solving gives us 

$$
\rho_0 = \mathcal{Z}^{-1} 2 \pi I_0(\lambda \kappa \mu_r \tau/2)
$$

$$
a_{2n} = \mathcal{Z}^{-1} \frac{2 \pi I_n(-\lambda \kappa \mu_r \tau/2)}{ \cosh\Big( n x_w/\sqrt{D \tau} \Big)} $$

And from normaliation 

$$
\mathcal{Z} = 2 \pi I_0(\lambda \kappa \mu_r \tau/2) ( x_w + \sqrt{2 \pi D/\lambda \mu} )
$$

So full solution is 

$$
\begin{cases}
\frac{1}{I_0(\lambda \kappa \mu_r \tau/2) ( x_w + \sqrt{2 \pi D/\lambda \mu} } \exp \Big( -\mu V / D - \lambda \kappa \mu_r \tau \cos(2 \theta) /2  \Big) \\
\frac{1}{x_w + \sqrt{2 \pi D/\lambda \mu}} \Bigg( \frac{ 1 }{2\pi} + \frac{1}{\pi} \sum_n \frac{I_n(-\lambda \kappa \mu_r \tau/2)}{I_0(\lambda \kappa \mu_r \tau/2)}  \frac{\cosh\Big(n (2x - x_w)/ \sqrt{D \tau}\Big) }{ \cosh\Big( n x_w/\sqrt{D \tau} \Big)} \cos 2 n \theta \Bigg)
\end{cases}
$$


<h3> Rotational Work </h3>

Should consider

$$ \langle \partial_{x_w} U \rangle \qquad \langle \partial_{\lambda} U \rangle $$

which give

$$ - \frac{\lambda \kappa}{2} \langle \delta(x - x_w) \cos 2 \theta \rangle \qquad \frac{\kappa}{2} \langle \cos 2 \theta \big[ H(-x) + H(x - x_w) \big] \rangle $$ 

We can calculate each component directly to get (ignoring $$\kappa/2$$)

$$ \frac{\lambda}{x_w + \sqrt{2 \pi D/\lambda \mu} } \frac{I_1(\lambda \kappa \mu_r \tau /2)}{I_0(\lambda \kappa \mu_r \tau/2 )} \qquad  -\frac{\sqrt{2 \pi D/\lambda \mu }}{x_w + \sqrt{2 \pi D / \lambda \mu}}\frac{I_1(\lambda \kappa \mu_r \tau /2)}{I_0(\lambda \kappa \mu_r \tau/2)} \tag{2} \label{eqn:mixed-partials} $$ 

To check whether these form an exact differential we should calculate the difference between mixed partials

$$ \partial_{\lambda} \langle \partial_{x_w} U \rangle - \partial_{x_w} \langle \partial_{\lambda} U \rangle $$


Using 

$$ d(I_1/I_0)/dx = 1 - \frac{I_1}{x I_0} - \Big( \frac{I_1}{I_0} \Big)^2 $$

Explicitly this gives us

$$
\begin{equation}
\begin{aligned}
\frac{1}{x_w + \sqrt{2 \pi D/\lambda \mu}} \frac{I_1}{I_0} &+ \frac{1}{2} \frac{\sqrt{2 \pi D / \lambda \mu}}{(x_w + \sqrt{2 \pi D/\lambda \mu})^2 } \frac{I_1}{I_0} + \frac{\lambda}{x_w + \sqrt{2 \pi D/\lambda \mu}} \Big( \frac{\kappa \mu_r \tau}{2} \Big) \Big( 1 - \frac{2 I_1}{\lambda \kappa \mu_r \tau I_0} - (\frac{I_1}{I_0})^2 \Big) \\
& - \frac{\sqrt{2 \pi D/\lambda \mu}}{(x_w + \sqrt{2 \pi D/\lambda \mu})^2 } \frac{I_1}{I_0} \\
& = - \frac{1}{2} \frac{\sqrt{2 \pi D / \lambda \mu}}{(x_w + \sqrt{2 \pi D/\lambda \mu})^2 } \frac{I_1}{I_0} + \frac{\lambda}{x_w + \sqrt{2 \pi D/\lambda \mu}} \Big( \frac{\kappa \mu_r \tau}{2} \Big) \Big( 1 - (\frac{I_1}{I_0})^2 \Big) \neq 0 
\end{aligned}
\end{equation}
$$

Which is non-zero. This should be zero in equilibrium so maybe we should review our assumptions

<h5> i) Continuity </h5>

By multiplying the FP equation by a cosine and integrating we can derive the spatial equations for the angular moments.

$$
\tau^{-1} n^2 m_n  + \frac{\lambda \kappa \mu_r n}{2} \big( m_{n-2} - m_{n+2} \big) = \partial_x \Big( \mu \partial_x V m_n + D \partial_x m_n \Big) \label{eqn:moments} \tag{3} 
$$

The $$n = 0$$ case gives us an equation for the density, and we can confirm that the equation requires it to be continuous (we also expect this physically, but it is also present from a mathematical perspective).

$$
\begin{equation}
\begin{aligned}
0 &= \mu \int^{x_w + \epsilon}_{x_w - \epsilon} \partial_x V \rho + D \int^{x_w + \epsilon}_{x_w - \epsilon} \partial_x \rho \\
0 &= \mu \int^{x_w + \epsilon}_{x_w} \partial_x V \rho + D ( \rho^{+} - \rho^{-} ) \\
0 &= \lim_{\epsilon \rightarrow 0 }  D ( \rho^{+} - \rho^{-} ) \qquad \checkmark
\end{aligned}
\end{equation}
$$

Let's repeat this for the higher moments to check for their mathematical continuity. Integrating Eq (\ref{eqn:moments})

$$
\tau^{-1} n^2  \int^{x_w + \epsilon}_{x_w - \epsilon} m_n dx  + \frac{\lambda \kappa \mu_r n}{2} \int^{x_w + \epsilon}_{x_w} \big( m_{n-2} - m_{n+2} \big) =  \mu \int^{x_w + \epsilon}_{x_w} \partial_x^2 V m_n dx + \mu \int^{x_w + \epsilon}_{x_w} \partial_x V \partial_x m_n dx + D \Big( \partial_x m_n \vert^{+} - \partial_x m_n \vert^{-} \Big) = 0 
$$

Which leads to a continuity condition on the <i>gradients</i> of the moments $$ n > 0$$ across a boundary, rather than the moments themselves.

$$
0 = \lim_{\epsilon \rightarrow 0 } D \Big( \partial_x m_n \vert^{+} - \partial_x m_n \vert^{-} \Big) 
$$

For $$\rho$$, both conditions hold. With this condition, let us again reexamine the solution to the FP equation. The dirichlet boundary condition in Eq \ref{eqn:dirichlet} is replaced by a Neumann condition. The first of the Dirichlet conditions concerning the density is un changed, but on top of this we also have that all $$ a_n =0 $$ for $$n>0$$. This returns us to the naive solution



$$
\begin{cases}
\frac{1}{I_0(\lambda \kappa \mu_r \tau/2) ( x_w + \sqrt{2 \pi D/\lambda \mu} } \exp \Big( -\mu V / D - \lambda \kappa \mu_r \tau \cos(2 \theta) /2  \Big) \\
\frac{1}{x_w + \sqrt{2 \pi D/\lambda \mu}} \frac{ 1 }{2\pi} 
\end{cases}
$$

<h5> ii) Fluxes </h5>

Suppose we seek a solution which contains fluxes, such that within the wall

$$
D \partial_x P + \mu \partial_x V P = \mathcal{L}_x P = \partial_{\theta} f(x, \theta)  \\
\tau^{-1} \partial_\theta P + \mu_r \partial_\theta U P = \mathcal{L}_{\theta} P = -\partial_x f(x, \theta)  \\
$$

In the bulk we'll have

$$
D \partial_x P  = \partial_{\theta} f_b(x, \theta)  \\
\tau^{-1} \partial_\theta P = -\partial_x f_b(x, \theta)  \\
$$


The usual flux free case is then the case where $$f (f_b) = $$const. We can solve these individual equations directly (here $$x > x_w$$)

$$
P(x, \theta)  = \exp(-\mu V /D) \Big[ P(x =x_w, \theta) + \int_{x_w}^{x} \exp( \mu V(x') /D) \partial_{\theta} f(x', \theta) dx'  \Big] \\
P(x, \theta)  = \exp(-\mu_r \tau U ) \Big[ P( x, \theta = 0) - \int_0^{\theta} \exp( \mu_r \tau U(\theta')) \partial_{x} f(x, \theta') d\theta'  \Big]  \\
$$

We expect the spatial pdf to be BOltzmann weighted in both cases, so integrating with respect to $$\theta$$ should give us this spatial density. Integratig the second equation then gives

$$
P(x, \theta)  = \Big[ I_0(\lambda \kappa \mu_r \tau/2) P( x, \theta = 0) -\int^{2\pi}_0 d\theta \exp( -\mu_r \tau U(\theta)) \int_0^{\theta} \exp( \mu_r \tau U(\theta')) \partial_{x} f(x, \theta') d\theta'  \Big]  \\
$$

This second term must then be equal to $$ \mathcal{A} \exp(-\mu V/D)$$, where $$ \mathcal{A}$$ could be $$0$$.



In the bulk we have

$$
D \partial_x P  = \partial_{\theta} f_b(x, \theta)  \\
\tau^{-1} \partial_\theta P = -\partial_x f_b(x, \theta)  \\
$$

The bulk flux therefore obeys the same differential equation as the FP pdf itself within the bulk (by considering mixed partials in $$P$$). In full generality the solution is

$$
f_b(x,\theta) = \frac{1}{2\pi} f_b^{(0)} ( A + B x) + \frac{1}{\pi} \sum_n  \cos (n\theta)  \Big[ f_b^{(n, +)}\exp( n x/ \sqrt{D \tau} ) + f_b^{(n, -)} \exp(-n x/ \sqrt{D \tau})) \Big]
$$

They are not the same function however, because $$f_b$$ will have different boundary conditions and constraints.  We collect them below

$$
\begin{cases}
 \\
\frac{1}{x_w + \sqrt{2 \pi D/\lambda \mu}} \frac{ 1 }{2\pi} 
\end{cases}
$$

<b> iii) State equation </b>

We expect the work output to be 0 with any quasistatic protocol. Therefore we require that $$ \partial_{\lambda} \langle \partial_{x_w} U \rangle - \partial_{x_w} \langle \partial_{\lambda} U \rangle $$ vanishes. 

Note that the only way for this to be identically zero we need

$$
\begin{equation}
\begin{aligned}
	&\frac{\partial_{x_w} U }{\partial_\lambda U }= \frac{\partial_{x_w} P}{\partial_\lambda P} \\
	\implies &\frac{\partial x_w}{\partial \lambda}\Big)_{U} = \frac{\partial x_w}{\partial \lambda}\Big)_{\rho}
\end{aligned}
\end{equation}
$$

Which would imply further that $$P = P(U)$$ i.e a state function. Generalising this idea, we make an ansatz that $$ P = P(U,V)$$, we can then write the FP equation in the following form (using expressions like $$\partial_V (\partial_x V) = 0$$)

$$
0 = D (\partial_x V)^2 \partial_V \big( e^{-V} \partial_V \big( e^V P \big) \big) + \tau^{-1} (\partial_\theta U)^2 \partial_U \big( e^{-U} \partial_U \big( e^U P \big) \big) + D \partial_xV \partial_x U \partial_U \partial_V P

0 = D (\partial_x V)^2 \partial_V \big( e^{-V} \partial_V \big( e^V P \big) \big) + \tau^{-1} (\partial_\theta U)^2 \partial_U \big( e^{-U} \partial_U \big( e^U P \big) \big) + D \partial_xV \partial_x U \partial_U \partial_V P
$$ 
