---
layout: post
title: Simple Questions about Difficult Topics (Glasses - in progress)
image: /img/hello_world.jpeg
tags: []
math: true
---


<script src='https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/MathJax.js?config=TeX-MML-AM_CHTML' async></script>

It is hard to navigate a complex field with tons of literature, to both learn about the previous investigations and note where the gaps are. It is also hard to ask good questions that will yield fruitful discussions. So instead I will ask bad questions, and hope something useful is stumbled upon.

**What is a glass?**

A glass is an amorphous material that can behaves in a glassy way. This is characterised by mechanical rigidity despite no long range crystalline order (in fact, the spatial disorder is similar to that of a liquid). They can be characterised by an extremely long relaxation time (extremely high viscosity).

**What is the glass transition?**

The glass transition is the transition from a non-glassy (liquid) state to a glassy state. This is often achieved by performing a fast quench from high temperatures to low - it must be fast to avoid the crystalline phase. The crossover happens at the experimentally defined "glass temperature" $$T_g$$, which is roughly the temperature at which the viscoity is "quite large". The idea is that past this temperature, any evolution happens at timescales not accessible to experiment. This temperature is protocol dependent.

**Does the relaxation time increase different than what you would expect considering activation energy (Arrhenius hopping)  arguments?**

Yes.

Not all glasses follow an appropriate Arrhenius law 

$$
\tau = \tau_{\infty} \exp\Big( E_{\rm eff}/T\Big)
$$

Those which do for an appreciable range of temperature are called _strong glass formers_, but even those have an $$E_{\rm eff}$$ which increases as temperature decreases ('super-Arrhenius').

**So the glass transition is not actually thermodynamic?**

Debatable. Although the transition is not sharp, and glasses are often characterised by their dynamical slow-down, there are some who think there is a hidden thermodynamic transition at play. Perhaps in some thermodynamics theory the relaxation time _does_ formally diverge at some finite temperature.

**What is the evidence that the glass transition is thermodynamic?**

**1**, Suppose we fit the relaxation time assuming there is a finite temperature divergence at $$T_0$$ (VFT law)

$$
\tau = \tau_0 \exp\Big( DT_0/(T - T_0)\Big) 
$$

Now suppose we calculate the _excess entropy_ of a liquid compared to the solid phase. If we plot $$\mathcal{S}_{\rm exc}$$ vs $$T$$, and extend the the line past the glass transition temperature, this excess entropy vanishes at some $$T_K$$ (Kauzmann temperature) $$\approx T_0$$. The correlation isn't perfect, there can be differences of up to 20%, but they are a lot closer a lot of the time. So there seems to be some link between thermodynamics ($$T_k$$) and dynamics $$T_0$$.

**2** The specific heat is (nearly) discontinuous at $$T_K$$

**But what is the thermodynamic order parameter?**

Unknown!

To date there haven't been any static order parameters which change appreciably at a finite temperature which would correspond to the glass transition. Below we list a large collection of ones which have been studied and reported in literature:

-
-
-

**Is there a diverging static lengthscale, as is typical in thermodynamic transitions?**

tbf

**So there isn't any good order parameter?**

That is a different question, _dynamic_ order parameters can act as signatures of the transition. For example, the intermediate scattering function

$$
F({\bf q}, t) = N^{-1} \langle \rho_{\bf q}(t) \rho_{\bf -q}(0) \rangle
$$

although other dynamical probes are possible, such as the dielectric susceptibility.

**What is the mode coupling temperature?**

The temperature below which the free energy landscape fragments inty many local minima corresponding to metastable amorphous states. Above $$T_{\rm MCT}$$ there is a single minimum in the free energy. Many theories predict that the free energy s analytic at this temperature (and people seem to take this as strong evidence that it is indeed true for real systems).

**WHat is dynamical facilitation?**
Dynamic facilitation is the process whereby relaxation of a local region in a glassy system enables another local region to subsequently move and relax. This facilitation can be long ranged at low temperatures, but people debate why.

_This is constantly updated. Last edit: 050321_

**[References]**

https://arxiv.org/pdf/1011.2578.pdf
