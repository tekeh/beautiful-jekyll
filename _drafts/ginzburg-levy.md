---
layout: post
title: Ginzburg for Levy Flight Rheology
image: /img/hello_world.jpeg
tags: [rheology, statistical physics]
math: true
---


<script src='https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/MathJax.js?config=TeX-MML-AM_CHTML' async></script>

See <a href=""> this previous post </a> for a description of the physical set up and problem to be investigated.

<h2> Approaches </h2>

The mean field arguments and models siplify a calculation by ignoring the spatial structure present. To consider the effect of spatial information, we can introduce small, position dependent fluctuations and see how they affect behaviour predicted in the mean field picture.

In our case we start with the continuum picture but add some small amount of structure to the Eshelby kernel so that $$ \mathcal{G}_{ij} \approx -\delta_{ij} /(N-1) + g_{ij} $$. 

$$
x_j(\gamma) = x_i(0) - \mathcal{G}_{ij}v_j \gamma + \tilde \zeta_i(\gamma)
$$

 Here $$v_i$$ is a vector with $$v$$ in ever entry. One thing to bare in mind is that this equation is linear in the stress variables ($$\mathcal{G}_{ij}$$ has spatial information but is independent of the stresses). The only peculiarity is the non gaussian noise. However, in light of some [previous considerations]({2019-02-15-gaussian-mixture.md}), we might ask whether this Levy distribution could be approximated as a Gaussian mixture. WIthout the cutoffs this is asking whether we can find a $$ f_l(\beta)$$ such that


$$
\int^{\infty}_0 f_l(\beta) \frac{\exp( -\beta x^2/2)}{\sqrt{2 \pi \beta^{1/2}}} \equiv \int^{\infty}_0 F_l(\beta) \exp( -\beta x^2/2) = \vert x \vert ^{-\mu - 1}
$$

Note that a differential equation for $$y = \vert x \vert^{-\mu - 1} $$ is $$ y' = -(1 + \mu)y/x$$. Differentiation both sides by $$x$$ yields.

$$
\int^{\infty}_0 - \beta x F_l(\beta) \exp( -\beta x^2/2) = - \frac{1 + \mu}{x} \int^{\infty}_0 F_l(\beta) \exp( -\beta x^2/2) 
$$

Multiplying by $$x$$ and then integrating by parts allows us to then derive the following nice expression

$$ 
\int_0^{\infty} \Big( \partial_{\beta}( \beta F_l ) - \frac{1}{2}(1 + \mu)F_l \Big) \exp(- \beta x^2/2) d \beta
$$

Want it true for all $$x$$, and so we expect 

$$
\partial_{\beta}( \beta F_l ) = \frac{1}{2}(1 + \mu)F_l
$$

Which has a simple solution $$ F_l(\beta) \propto \beta^{(\mu - 1)/2}$$. Power law for a power law. The corresponding $$f_l$$ is not normalizable, however (as was obvious as the RHS wasn't).

With the cut off we want to follow a similar method; find a differential equation which it satisfies, and see if we can find the corresponding equation for $$F_l$$.

Suppose we can approximate the Levy noise fluctuations reasonably well by a Gaussian mixture.

$$
p_{\text{Levy}}(x) \approx \int^{\infty}_0 f_{\text{Levy}}(\beta) p_{\text{normal}}(x \vert \mu = 0, \sigma^2 = \beta^{-1}) d\beta
$$

Remembering that it was a convolution of levy kicks which made up the noise $$tilde \zeta$$

$$
\begin{equation}
\begin{aligned}
p_{\gamma} (\tilde \zeta = t) &= \int ... \int \delta( t - \sum_i y_i) p(\zeta = y_1) ... p(\zeta = y_{\gamma N}) \prod dy_i \\
	&= \Big( \idotsint \prod_j f_{\text{Levy}}(\beta_j) d\beta_j\Big) \idotsint \delta( t - \sum_i y_i) p_{\text{normal}}(y_1 \vert \sigma^2 = \beta_1^{-1}) ... p_{\text{normal}} (y_{\gamma N} \vert \sigma^2 = \beta_{\gamma N}^{-1} ) \prod_i dy_i\\
	& \equiv \int_{\mathcal{V}} F_{\text{Levy}}(\vec \beta)  \exp\Bigg( -\frac{t^2}{2 \sum_{i=1}^{\gamma N} \beta_i^{-1} } \Bigg) \frac{d \vec \beta}{\sqrt{ 2 \pi \sum^{\gamma N}_i \beta_i^{-1} }} 
\end{aligned}
\end{equation}
$$

We'll want to do our averages in the steady state, so this integral actually then becomes <i>infinite dimensional</i> (as $$\gamma N \rightarrow \infty$$). This may actually help us with the calculation quite a bit. 

Assuming the mixture form is valid this measn that we only need to solve the corresponding N-body brownian problem. After taking a derivative it is the following overdamped motion.

$$
\dot x_i(\gamma) =  \mathcal{G}_{ij}v_j + \sqrt{2 D(\vec \beta)} \eta_i(\gamma)
$$

With $$D(\vec \beta)  = (\gamma N)^{-1} \sum_i \beta_i^{-1} $$ where the $$\beta_i$$'s are a random sample of the positive sector in $$\beta$$-space (seemingly time dependent noise - problem?). The brownian problem obeys the following master equation

$$
\frac{\partial \mathcal{P} }{\partial \gamma} = \mathcal{G}_{ij} v_j \frac{\partial \mathcal{P}}{\partial x_i} + D(\vec \beta ) \frac{\partial^2 \mathcal{P} }{\partial x_i \partial x_i} + \prod_i \delta( x_i - 1)
$$

In the steady state $$\partial_{\gamma} \mathcal{P} = 0 $$ and we denote $$\beta $$ by $$\beta_{\infty}$$. The solution can be written in product form $$\mathcal{P}(\{x_i\}) = \prod_j \rho(x_j)$$ with

$$
	\rho(x_i) = \frac{e^{\mathcal{G}_{ij}v_j/D}}{2\mathcal{G}_{ij}v_j} 
\begin{cases}
1 - \exp(-\mathcal{G}_{ij}v_jx_i/D) \qquad 0 \leq x_i < 1\\
1 - \exp(\mathcal{G}_{ij}v_j(x_i-2)/D) \quad 1 < x_i \leq 2
\end{cases}
$$

With no sum on the $$i$$ index. Now we should be able to write the solution to the Levy flight process as a superposition of these gaussian solutions:

$$
\mathcal{P}_{\text{Levy}} = \idotsint \mathcal{P}^{(\vec \beta_{\infty})}( \{x_i\} ) F_{\text{Levy}}(\vec \beta_{\infty}) d \vec \beta_{\infty}
$$

To check the validity of the method, let's look at the single variable mean field case to show we reproduce behaviour

$$
\begin{equation}
\begin{aligned}
\mathcal{P}_{\text{Levy}}(x) &\propto  \idotsint (1 - \exp(-vx/D(\vec \beta)) ) \exp(v/D(\vec \beta)) F_{\text{Levy}}(\beta_i \} ) d \vec \beta \\
			& \equiv \idotsint e^{-S} d \vec \beta \\
\end{aligned}
\end{equation}
\\
\text{with} \\

S(\vec \beta) = - \frac{v}{D(\vec \beta)} - \ln \big( 1 - \exp(-vx/D(\vec \beta)) \big) - \ln F_{\text{Levy}} 
$$ 

From here we might try  a saddle point like method. If it is valid then we would expect $$\mathcal{P}_{\text{Levy}} \sim e^{-S_0} \sigma(x) $$, where $$\sigma$$ is the standard deviation. The mean of $$S$$, assuming a single unique stationary point at $$\vec \beta = \beta_m (1,1,1,...,1)$$. obeys the following equation

$$
	0 = v \Big( 1 + xn_{B}(v x \beta_m) \Big)  + \partial_u \ln f_{\text{Levy}}(u) \vert_{\beta_m}
$$

Here we've defined $$n_{B}(u) = (e^u - 1)^{-1}$$ (This is the form for the Bose-Einstein distribution in quantum physics). The variance is determined by the following expression

$$
\sigma^{-2} = v^2 x^2 \Big( n_{B}(v x \beta_m) + n_{B}(v x \beta_m)^2 \Big) - \partial^2_u \ln f_{\text{Levy}}(u) \vert_{\beta_m} \\

\sigma^{-2} = \frac{v^2 x^2}{4 \sinh^2(v x \beta_m/2)} - \partial^2_u \ln f_{\text{Levy}}(u) \vert_{\beta_m} \\

$$

 Clearly the distribution $$f_{\text{Levy}}$$ plays an important role. In particular its log-convexity properties are important - if $$f$$ is log-concave , then there is no chance of a negative variance (which would be fallacious).

$$
\mathcal{P}_{\text{Levy}} = \prod_i^{\gamma N} x_i \idotsint \mathcal{P}^{(\vec z )}( 1 \vert \mathcal{G}_{ij} ) F_{\text{Levy}}(\{ z_i/x_i \} ) d \vec z
$$


Make the ansatx that asymptotically $$F_{\text{Levy}}(t) \sim t^{-\alpha \gamma N} $$ for $$ \alpha > 0 $$. Then  

$$
\mathcal{P}_{\text{Levy}}(x) \sim x^{\gamma N(1 + \alpha)} \idotsint (1 - \exp(-v/D(\vec z)) ) \exp(v/xD(\vec z)) z^{-\alpha}  d \vec z
$$ 

Assuming $$A \approx 1$$ then we could reasonably model the noise by a <b>scaled t-distribution</b> (where be pick the DOF such that we have the same asympotote). The downside is that it does not accurately exhibit the cut off behaviour, but as $$ N \rightarrow \infty$$ this cut off tends toward zero anyway. By using the t-distribution we are implicitely saying that all the interesting physics (in an RG/fluctuation sense) is in the broad tail and none of the other details, and not in what happens near the origin. On the other hand surely we should be trying to match up the most probable events, which are nearer to the mean of distribution? More on this.
