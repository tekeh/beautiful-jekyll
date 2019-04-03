---
layout: post
title: Title
image: /img/hello_world.jpeg
tags: [tag2, tag2]
math: true
---


<script src='https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/MathJax.js?config=TeX-MML-AM_CHTML' async></script>

Suppose we have a Brownian Motion on a ring. The stochastic differential equation can be written in the angular coordinate as

$$ d\phi_t =   \sqrt{\frac{2}{\tau}} dW_t$$

Where $$\tau$$ is a non-random constant and $$dW_t$$ is a Weiner process (White gaussian noise). What is the probability that $$\cos(\phi_t)$$ takes some certain value when evolving under this dynamics? We can consider the Fokker plank equation.

$$ \partial_t \mathcal{P} = \frac{1}{\tau} \partial_{\phi}^2 \mathcal{P} $$

We need periodic boundary conditions in $$\phi$$ and we suppose that the initial distribution is delta-peaked at some $$\phi_0$$.

This can be solved explicitely in terms of a fourier sum

$$ \mathcal{P}(\phi_t = \phi) = \frac{1}{2 \pi} \Big( 1 + \sum_{n=0}^{\infty} 2 \cos\big( n (\phi - \phi_0)  e^{-n^2 t/ \tau} \Big) $$

We can then transform the probability distribution

$$\mathcal{P}(\phi) d\phi = \mathcal{P}(\phi) \vert \frac{d\phi}{d\cos\phi} \vert d( \cos\phi ) := \tilde{\mathcal{P}}(\cos \phi) d( \cos \phi ) $$


which give us, upon taking $$\phi_0 = 0$$ (or equivalently $$ \phi_t \rightarrow \phi_t - \phi_0 e^{t/\tau} )$$ .

$$\tilde{ \mathcal{P}} (\cos \phi_t = f) = \frac{1}{2 \pi \sqrt{ 1 - f^2} } \Big( 1 + 2 \sum_{n=0}^{\infty} T_n (f)  e^{-n^2 t/\tau} \Big) $$

Where $$T_n$$ is the $$n$$th order Chebyshev polynomial. But now let's say we wish to work out the pdf of a sum of two random variable $$ X_t = \alpha \cos \phi_t +  \eta^{1/2} d\Lambda_t$$. $$d \Lambda_t$$ is also a white gaussian noise, but one uncorrelated with the noise controlling the angular coordinate. The joint pdf of the sum of two random variables is just the convolution of both their pdfs, so we can write

$$ P(X_t = x) = \int^{\alpha}_{-\alpha} \tilde{\mathcal{P}}( \cos \phi_t = s/\alpha ) \mathcal{P}( \Lambda_t = (x - s)/\eta) ds \\

= \frac{1}{\sqrt{ 2 \pi \eta}} \int^{1}_{-1} \frac{du}{2 \pi \sqrt{ 1 - u^2} } \Bigg( 1 + 2 \sum_{n=0}^{\infty} T_n (u)  e^{-n^2 t/\tau} \Bigg)  \exp\big( - (x - u \alpha)^2/2 \eta \big)   $$

The mean of this new variable $$X_t$$ is $$0$$ by symmetry. Let us focus on the steady state so that

$$ P(X_t = x) = \frac{1}{\sqrt{ 2 \pi \eta}} \int^{1}_{-1} \frac{ \exp\Big[ - (x - u \alpha)^2/2 \eta \Big]}{\pi \sqrt{ 1 - u^2} }  du  $$


We formally want this to be equal to a superposition of gaussians with fixed mean, but a range of variances. In other words, we want


$$ \int_\eta^{\infty} f(\beta) e^{- \beta x^2 /2} \frac{1}{\sqrt{2 \pi \beta^{-1}}} d\beta = \frac{1}{\sqrt{ 2 \pi \eta ^{-1}}} \int^{1}_{-1} \frac{ \exp\Big[ - \eta (x - u \alpha)^2 /2 \Big]}{\pi \sqrt{ 1 - u^2} }  du  $$

This defines $$f(\beta)$$, the normalised superstatistical ensemble which we wish to derive, or at least approximate well. It depends on the parameters of the original stochastic process $$ \alpha, \eta $$ but certainly should not depend on $$x$$ at all for this construction to be valid. Presumably we need $$ \alpha < 2\eta^{1/2}$$ for this representation to work, as in this limit the gaussian sums is sure to sure to have only one peak at the origin (think about the turning points of two separated gaussians).

![Superstatistical Ensemble](/img/superstat_integral.png)


May need to perform a reverse Laplace transform here unless i can find a nicer route to the deduction of $$f$$. When $$\alpha \rightarrow 0$$ then we expect $$f(\beta) \approx \delta( \beta - \eta^{-1})$$. The expression above should ideally hold for all $$x$$, so we can fourier transform the integrals in that variable to give something like 


$$ \int_{0}^{\infty} f(\beta) e^{- k^2 /2\beta} d\beta =  \int^{1}_{-1} \frac{ \exp\Big[ - k^2 /2\eta \Big] \cos(k u \alpha) }{\pi \sqrt{ 1 - u^2} }  du  $$

$$ \int_0^{\infty} f(\beta) e^{- k^2 /2\beta} d\beta = \exp\Big[ - k^2 /2\eta  \Big] J_0( \vert k \alpha \vert )  $$

This is enough to kill the idea of $$f$$ being some sort of probability distribution in general. The RHS can take positive and negative values as $$k$$ varies but the LHS can only be positive by assumption. What if we drop the conceptual hangup of it being a distribution and instead see it as a summation function i.e let $$f$$ take positive and negative values?


Lets rearrange slightly


$$ \int_{\eta}^{\infty} f(\beta) e^{- (\beta^{-1} - \eta^{-1}) k^2 /2} d\beta = J_0( \vert k \alpha \vert)  $$

$$ \int_0^{\infty} F(T) e^{- T s} dT = - J_0( \vert \sqrt{s} \alpha \vert )  $$

$$T = (\beta^{-1} - \eta^{-1}) $$. Also set $$k^2 = s$$. $$F(T) = (T+ \eta^{-1})^2f( \frac{1}{T + \eta^{-1}}) $$ 

We know that the Bessel function obeys the PDE

$$
x^2 J_0'' + x J_0' + x^2 J_0 = 0
$$

And therefore through use of the chain rule we can verify that

$$ \int_0^{\infty} \big( \alpha^2 \partial_{\alpha}^2  + \alpha \partial_{\alpha} \big)F(T) e^{- T s} dT = -s \alpha^2 J_0''( \vert \sqrt{s} \alpha \vert ) - \alpha \sqrt{s} J_0'(\alpha \sqrt{s}) =  s\alpha^2 J_0 = -\alpha^2 s \mathcal{L} [F]$$

But we also know that the Laplace transform has the property that $$ \mathcal{L}[dF / dT] = s\mathcal{L}[F] - F(0)$$. So we can further rearrange to yield

$$ \int_0^{\infty} \big( \alpha^2 \partial_{\alpha}^2  + \alpha \partial_{\alpha} + \alpha^2 \partial_{T} \big)F(T) e^{-T  s} dT = -\alpha^2 F(0) $$

For all $$s$$. It is then easy to see we can pass from this integral equation to a differential one.

$$
\big( \alpha^2 \partial_{\alpha}^2  + \alpha \partial_{\alpha} + \alpha^2 \partial_{T} \big)F(T) = -\alpha^2 F(0) \delta(T)
$$

$$
 \alpha^{-1} \partial_{\alpha}( \alpha \partial_{\alpha}F)  + \partial_{T}F = - F(T = 0) \delta(T)
$$

A Greens fucntion of sorts, to a cylindrical diffusion process (albeit with negative constant). Beware the boundary conditions. We need that $$F(T, \alpha=0) = \delta (T)$$ and $$F(T \rightarrow \infty) = 0$$. The advantage to passing to this equation is we can at least make use of standard techniques that can be used to solve such parabolic equations. Also, i suspect that $$F(T = 0) = -\delta(\alpha)$$ from looking at it's definition and considering the limiitng behaviour in $$\alpha$$, but don't hold me to it.

So we should solve this and then look at the function $$F$$ when $$\alpha = \alpha_0$$, where $$\alpha_0$$ is the value specific to the system. We can write a series solution to this equation away from $$T=0$$ in terms of 


