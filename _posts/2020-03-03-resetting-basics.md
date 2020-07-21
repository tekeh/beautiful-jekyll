---
layout: post
title: Plastic Events and Resets
image: /img/hello_world.jpeg
tags: [statistical physics, rheology, quantum mechanics]
math: true
---


<script src='https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/MathJax.js?config=TeX-MML-AM_CHTML' async></script>


Imagine a stochastic reset of a certain type. Each site of our rheologicla material has a stress associtaed with it, but due to mechanical noise (rather than thermal fluctations) the stress at each site is going to fluctuate according to some effective Stochastic ODE i.e for each site (assuming they are statistically identical):

$$
\dot{\sigma}_i = - \mu V_0 ' (\sigma_i) + \eta
$$

Where for simplicity we've taken the noise to be white and gaussian. On top of this we have added a local potential, which is simoply to do with the elastic nature of each site. For example, by imposing external stresses on our rheological sample we might find that the local stresses ten dot relax down to some typical steady value due to elastic restoring forces. 

Now we've said something about how local stresses evolve, but how do they relax? In real rheological flows we often have plastic reorganisation events when the system locally overcomes its yield stress $$ \sigma_Y$$. So imagine a model where we reset with some constant rate $$r$$ if the magnitude of the local stress is  above the yield stress. Using a <a href=""> recent stochastic path integral formulation</a>, we could write this as 

$$
P_{\text{no reset}}(x, t) = \int \mathcal{D} \sigma(t) \exp(-S_{\text{res}}[\sigma(t)]) \\
\text{with} \\
S_{\text{res}} = \int^t_0 dt \Bigg[ \frac{ [(d\sigma/dt) - \mu F ]^2 }{4D} + \frac{\mu F'}{2} + r(\sigma) \Bigg]
$$

Where $$F = -  V_0 '$$ and $$r(\sigma) = H(\sigma - \vert \sigma_Y \vert )$$. This formalism allows us to map unto a 1D schrodinger equation, where many solution and approximations methods are known. In this case the effective Hamiltonian can be written

$$ H =  -\frac{1}{2 m_{\text{eff}}} \partial_x^2 + V_{\text{eff}} \\
\text{where} \\
m_{\text{eff}} = (2D)^{-1} \qquad V_{\text{eff}} = \frac{\mu^2 F^2}{4 D} + \frac{\mu F'}{2} + r(\sigma)
$$

With this connection, and some more manipulation of probabilities, the steady state dynamics of resetting stress can be studied using the Green's function of the associated quantum problem.
