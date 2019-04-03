---
layout: post
title: Optimal Finite Time Processes for Active Brownian Processes
image: /img/hello_world.jpeg
tags: [stochastic processes]
math: true
---


<script src='https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/MathJax.js?config=TeX-MML-AM_CHTML' async></script>

The Fokker Plank is


$$
\partial_t P = \partial_x \Big[ \partial_x V p + T\partial_x P - v \cos \theta P \Big] + \tau_R^{-1} \partial_{\theta}^2 P \label{eqn:fp} \tag{1}
$$

The work done on the system in time $$T$$ is simply

$$
\mathcal{W} = \int^{T}_0 \sum_i \langle  \partial_{\alpha_i} V \rangle \dot{\alpha}_i dt
$$

Where $$\alpha_i$$ are the controllable parameters. Following Seifert, we first consider two special cases

<h3> Example 1: Translational Harmonic Trap </h3>

$$V = (x - \alpha)^2/2$$ 

Call $$u = \langle x \rangle$$ and $$r_n = \langle \cos n\theta \rangle$$. The work becomes

$$
\mathcal{W} = \int^T dt \dot{\alpha} (\alpha - u + v r_0) 
$$

Multiplying by x in Eq \ref{eqn:fp} and averaging gives the relation $$ \dot{u} = \alpha -  u + r_0$$. Averaing after multiplying by $$\cos$$ yields $$ \dot{r}_0 = -n^2 \tau_R^{-1} r_0$$. If we are initally in the steady state profile, then $$r_0(0) = 0$$ which makes $$r = 0$$ at all times. Thus the presence of activity does not change the shape of the optimal prootocol. Using both these above we get the expression presented in Schmeidl and Seifert.

$$ \mathcal{W} = \int^T dt \dot{u}^2 = \dot{u}^2 \vert_0^T $$

Which is soluble EL equation (blah blah)

<h3> Example 2: Stiffening Harmonic Trap </h3>

$$V = \alpha x^2 /2 $$


Further define $$w = \langle x^2 \rangle$$ and $$f = \langle x \cos\theta \rangle $$. Multiplying Eq \ref{eqn:fp} by $$x^2$$ and averaging yields

$$ \dot{w} -2 \alpha w + 2 + 2 v f = 0 $$

Where $$f$$ obeys 

$$ \dot{f} = -(\tau_R^{-1} +  \alpha )f + v(1 + r_2)/2  = -(\tau_R^{-1} +  \alpha )f + v/2 $$. 

Which gives us the solution 

$$ f = f(0) \exp(-t(\alpha + \tau_R^{-1}) ) + \frac{v}{2(\tau_R^{-1} + \alpha)} (1 - \exp(-t(\alpha + \tau_R^{-1}) ) )$$.

$$f(0) = \alpha/2$$ from equipartition like calculation (details here).

Not that the work in this case is

$$\mathcal{W} = 1/2 \int^T \dot{\alpha} w dt = \alpha w \vert^T_0 - \int^T \alpha \dot{w} dt = \frac{1}{2}\big[ \alpha w - \ln w \big] \vert + \int \Big( \frac{\dot{w}^2}{w} + v \frac{f}{w \alpha} \Big)dt $$
