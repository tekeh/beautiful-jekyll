---
layout: post
title: An Integral
image: /img/hello_world.jpeg
tags: [statistical physics, approximation]
math: true
---


<script src='https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/MathJax.js?config=TeX-MML-AM_CHTML' async></script>

A function of this form came up while doing calculations on active particle dynamics

$$ f(x ; \alpha, \beta, \gamma) = e^{-\beta x^2/2} \int^{\pi}_{-\pi} \frac{d\theta}{2 \pi} \exp \big(\alpha x \cos \theta - \gamma \cos^2 \theta \big) \label{eqn:f-function} \tag{1} $$

All the parameters of $$f$$ are non-negative, but the variable $$x$$ can take any real value. The function is defined implicitely in terms of this integral which has no closed form expressions which Mathematica could identify. We can still look at interesting properties of this expression, even if we can't find a closed form for it.

For the physical situation this arises from, $$\gamma$$ will typically be a small variable compared to $$1$$. So a natural thing to try would be to expand the second term in the integrated exponential in a taylor series. This then gives us an infinite sum for $$f$$ in terms of <b> Modified Bessel Functions </b>

$$ I_k (x) = \int_0^{\pi} \frac{d\theta}{\pi} \cos (k \theta) \exp( x \cos \theta) $$

for integer $$k$$. Our function then can written using the Bessels as a positional basis. Using the symmetry properties of the bessels, we write

$$ f = e^{- ( \gamma + \beta x^2)/2} \Big( I_0(\gamma/2)I_0(\alpha x) +  2\sum_{k=1}^{\infty} (-1)^k I_k(\gamma/2) I_{2k}(\alpha x) \Big) $$ 

From here we can truncate at some order to yield an approximation to the function. We might also be interested in the asympototic tails of this function - i.e its behaviour as $$x \rightarrow \pm \infty$$.  Let us focus on divergence in positive values first. One way to approximate its behaviour is by noting that Eq. $$\eqref{eqn:f-function}$$ would be peaked around $$\theta = 0$$ for sufficiently large, positive $$x$$. Using a saddle point approximation about this point we get that

$$ f \approx e^{- (\gamma + \beta x^2) /2} \int ^{\infty}_{-\infty} \frac{d\theta}{2 \pi} \exp \Big( \alpha x \Big[1 - \frac{1}{2} \theta^2 \Big] - \frac{1}{2} \gamma \Big[ 1 - \frac{1}{2} (2 \theta)^2 \Big] \Big) $$

$$ f \sim e^{- (2 \gamma + \beta x^2 - 2 \alpha x ) /2} \Bigg( \sqrt{\frac{1}{2 \pi \alpha x}} + \mathcal{O}(x^{3/2})  \Bigg) $$

Our function $$f$$ is also even in $$x$$, so the same asymptote holds as we diverge negatively (although in the interim calculation we must expand about the <i>minimum</i> of $$\cos$$). Where are the stationary points of this function in $$x$$? Since it is even around the origin, there will surely be one there, but are there any more? To help calculation we look for the staionary points of $$ \log f$$ instead.

$$0 = - \beta x + \alpha \frac{\int d\theta \cos\theta \exp(\alpha x \cos \theta - \gamma \cos^2 \theta) }{\int d\theta \exp( \alpha x \cos \theta - \gamma \cos^2 \theta )} := \Pi(x) \label{eqn:Pi} \tag{2} $$

There a couple of key observations to make here. For $$x \rightarrow \infty$$ the first term is negative and decreases indefinitely without bound, but the second term is always bounded between $$(-\alpha,\alpha)$$ (since $$ \vert \cos \theta \vert \leq 1$$), and tends to $$\alpha$$ as $$x \rightarrow \infty$$. Therefore there is either one solution only (at $$x = 0 $$), or three depending on the relative values of the parameters.

The second function is concave, so it is enough to consider the linear behaviour of both terms about $$x=0$$. If the gradient of the first term is initially larger or the same as the gradient of the second, then we have one solution to $$\Pi = 0$$, otherwise we'll have three. The first is already linear, but the second can be expanded about $$x=0$$.

$$ \Pi(x) \approx \Bigg[ - \beta  + \frac{\alpha }{2} \Big( 1 - \frac{I_1(\gamma /2)}{I_0(\gamma /2)} \Big) \Bigg] x + \mathcal{O}(x^3)  $$ 

Again, using the definition of the Bessel functions. And so we therefore need the following condition for a stationary point away from the origin.

$$ \beta <  \frac{\alpha }{2} \Big( 1 - \frac{I_1(\gamma /2)}{I_0(\gamma /2)} \Big) $$ 

This is the same behaviour seen in equilibrium second order phase transitions (such as mean field Ising model). Just from graphical arguments, we then see that $$f$$ goes from something which has a maximum at $$x=0$$ and decays at both sides, to something with a minimum at $$x=0$$ and maxima further out, before decaying away. The simplest way to approximate the location of the stationary points $$\pm x_p$$ is to just take the next order, which is fine if you expect the maxima to not be too far from the origin. The calculation for it is not too illuminating though. Some bounds may give a more intuitive picture instead.

We can easily say that $$0 \leq x_p <\alpha/ \beta $$ from examining Eq. $$\ref{eqn:Pi}$$, but maybe there is something nicer we can do. 

References:

[1] NIST Digital Library of Mathematical Functions
