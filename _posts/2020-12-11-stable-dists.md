---
layout: post
title: Stable Distributions
image: /img/hello_world.jpeg
tags: probability, statistics
math: true
---


<script src='https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/MathJax.js?config=TeX-MML-AM_CHTML' async></script>

From Wikipedia:


"Let $$X_1$$ and $$X_2$$ be independent copies of a random variable $$X$$. Then $$X$$ is said to be stable if for any constants $$a > 0$$ and $$b > 0$$ the random variable $$aX_1 + bX_2$$ has the same distribution as $$cX + d$$ for some constants $$c > 0$$ and $$d$$."

And the distribution of X is called a _stable distribution_.

Under convolution, these distributions are fixed points. Some examples come to mind immediately, such as the much loved Normal Distribution $$P_{\mathcal{N}}(x \vert \mu, \sigma^2)$$, which obeys the following relationship:

$$\begin{equation}
	P_{\mathcal{N}}(x/a | \mu, \sigma^2) * P_{\mathcal{N}}(x/b | \mu, \sigma^2) = P_{\mathcal{N}}(x | (a+b) \mu, (a^2 + b^2) \sigma^2) 
\end{equation}
$$

But other stable distributions exits, such as the Cauchy Distributions $$P_{\mathcal{C}}(x\vert \mu, \gamma)$$. We show this explicitely by Fourier Transforming and using the convolution theorem:

$$
\begin{equation}
\begin{aligned}
	FT \Big[ P_{\mathcal{C}}(ax | \mu, \gamma^2) &* P_{\mathcal{C}}(bx | \mu, \gamma^2)\Big] (k) \qquad (a,b>0)\\
	&= \phi_{\mathcal{C}}(k/a | \mu, \gamma^2 ) \cdot  \phi_{\mathcal{C}}(k/b| \mu, \gamma^2 ) \\
	&= e^{-i k \mu(a^{-1} + b^{-1}) - \gamma |k|(a^{-1} + b^{-1}) } \\
	& = \phi_{\mathcal{C}} (k | \mu', \gamma'^2)  \qquad (\mu', \gamma'^2) =  (\mu(a^{-1}+b^{-1})^{-1}, \gamma'^2 = \gamma^2 (a^{-1} + b^{-1})^{-1} ) \\
\rightarrow  P_{\mathcal{C}}(ax | \mu, \gamma^2) &* P_{\mathcal{C}}(bx | \mu, \gamma^2) = P_{\mathcal{C}}(x \vert \mu', \gamma' )
\end{aligned}
\end{equation}
$$

So again, the functional form is preserved - the normal distribution is not alone in this. 

What make the enormal distribution even more powerful is the **Central Limit Theorem** (CLT) which says that the sum of $$N$$ IIDs with a finite mean and variance will converge in probability to a Gaussian as $$N \rightarrow \infty$$. This is a stronger statement, because it implies that no matter the distribution you start with, if the CLT holds then you will eventually get to the Gaussian as you do more convolutions. And once you "arrive" at the Gaussian, in the asymptotic sense, you will remain there, so it is an attractor in probability space, not just an unstable fixed point. So where does this leave all our other non-gaussian stable distributions? Are they ever reached when carrying out an asymptotic sum? The answer is yes, the CLT does not cover all cases - sums of iids without a defined variance (or mean) can converge to distributions other than the Gaussian.

## Stable distribution families

As said, the stable distributions are invariant, up to shifts and rescalings, under a convolution. It convenient to work in fourier space, where the relation reads

$$
\begin{equation}
\begin{aligned}
	\tilde\rho(k a) \cdot \tilde\rho(k b) &= e^{i k \delta} \tilde\rho(k c) \\
\end{aligned}
\end{equation}
$$

First consider the case of no shift. Defining $$\hat f(x) = \ln(\tilde\rho(x)) $$. Then we wish to solve

$$
\begin{equation}
\hat f(ak) + \hat f(bk) = ik\delta + \hat f(ck) 
\end{equation}
$$

where $$c = c(a,b)$$ is a constant depending on the scaling. Further define $$\hat f(x) = f(x) + ix\delta$$, which reduces the functional equation to a homogeneous form:

$$
\begin{equation}
f(ak) + f(bk) = f(ck) 
\end{equation}
$$

Which holds for all real $$a, b, k$$, with an an adjoining $$c(a, b)$$. We can deduce properties by taking special points:

- 1) $$c(a,b) = c(b,a) \qquad (a \leftrightarrow b)$$
- 2) $$f(0) = 0 \qquad (k=0) $$
- 3) $$c(a, 0) = a \qquad (b=0)$$
- 4) $$f(a/b) - f(b/a) = f(c/b) - f(c/a) \qquad (k=1/a) - (k= 1/b) $$
- 5) $$ c( c(x, y), z) {\rm \ permutation\ invariant} \qquad (f(ak) +f(bk) + f(ck) ) $$

This seems tough to solve directly.

The issue was solved via other methods by those Kolmogorov and friends - the general solution is known, and is of the form

$$
\begin{equation}
f(k; \alpha, \beta, \gamma) = -\vert \gamma k \vert^{\alpha} ( 1 - i \beta {\rm sgn}(k) \Phi)
\end{equation}
$$

 where

$$ \Phi = \begin{cases} \big( \vert \gamma k \vert^{1-\alpha} - 1 \big) \tan(\frac{\pi \alpha}{2}) \qquad \alpha \neq 1 \\
-\frac{2}{\pi} \log \vert \gamma k\vert \qquad \alpha=1\end{cases}
$$

$$\alpha, \beta, \gamma, \delta$$ are parameters of the distribution. $$\alpha \in (0,2]$$ is called the stability parameter, $$\beta \in [-1,1]$$ is a measure of the skewness and $$\gamma \in \mathbb{R}^{+} $$ is the scale parameter. Furthermore the parameter $$\delta$$ in $$\hat f$$ is called the _location parameter_. The normal distribution corresponds to $$\alpha =2$$, the only value of alpha which yields a distribution with a defined variance. 

Although the characterstic function can be parametrised exactly, there is no general analytic form for the probability distribution - only special cases are known. The document [here](https://cds.cern.ch/record/1566201/files/978-3-319-00327-6_BookBackMatter.pdf) lists several closed forms for specific parameter values.

For a distribution $$P(x)$$ to belong to the basin of attraction for the stable distribution with parameter $$\alpha$$, it is necessary and sufficient for

- 1) $$\frac{P(-x)}{1 - P(x)} \rightarrow \frac{c_{-}}{c_{+}}, \qquad x\rightarrow \infty $$
- 2) $$\frac{1 - P(x) + P(-x)}{1 - P(kx) + P(kx)} \rightarrow k^{\alpha}, \qquad x\rightarrow \infty \qquad$$ for every $$k>0$$

where $$c_{-},c_{+}$$ are constants which are proportional to the amplitudes of the asymptotic behaviours of $$P(x)$$ for large $$\pm x$$ (defined with great specificity in Ref 4.). There are also independent conditions that rely on knowledge of the characteristic function.

Let $$p(k)$$ be the characteristic function of $$P(x)$$. To belong to the basin of attraction for the stable distribution with parameter $$\alpha$$, it is necessary and sufficient for

#### $$0<\alpha<2, \alpha \neq 1$$

$$
\begin{equation}
 \lim_{r\rightarrow 0} \frac{\rm{Re}[\ln p(rk)]}{\rm{Re}[\ln p(r)]} = k \qquad 
\end{equation}
$$

and 

$$
\begin{equation}
\lim_{r\rightarrow 0} \frac{\rm{Im}[\ln p(rk)]}{\rm{Re}[\ln p(r)]} = \beta r^{\alpha} \tan\Big( \pi \alpha/2\Big) \qquad 
\end{equation}
$$
 
#### $$\alpha = 1$$

$$
\begin{equation}
 \lim_{r\rightarrow 0} \frac{\rm{Re}[\ln p(rk)]}{\rm{Re}[\ln p(r)]} = k \qquad 
\end{equation}
$$

and

$$
\begin{equation}
\lim_{r\rightarrow 0} \frac{\rm{Im}[\ln e^{-i\langle x \rangle rk} p(rk) -  r\ln e^{-i\langle x \rangle k} p(k)]}{\rm{Re}[  \ln e^{-i\langle x \rangle r} p(r)]} = \frac{2 \beta}{\pi} k\ln k
\end{equation}
$$

**[References]**

[1] [Wiki](https://en.wikipedia.org/wiki/Stable_distribution) (Last accessed: 21 Nov 2020)

[2] [Random Services](http://www.randomservices.org/random/special/Stable.html) (Last accessed: 21Nov2020)

[3] [https://cds.cern.ch/record/1566201/files/978-3-319-00327-6_BookBackMatter.pdf](https://cds.cern.ch/record/1566201/files/978-3-319-00327-6_BookBackMatter.pdf)

[4] B.W. Gnedenko, A.N. Kolmogorov,\textit{Limit Distributions for Sums of Independent Random Variables}, (Addison-Wesley, Reading, 1954) 
