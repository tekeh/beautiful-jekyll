---
layout: post
title: Active Energetics (in progress)
image: /img/hello_world.jpeg
tags: [thermodynamics, stochastic processes]
math: true
---


<script src='https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/MathJax.js?config=TeX-MML-AM_CHTML' async></script>

Let us call $$ \phi(x, \theta)$$ the ABP potential function. This can take various forms depending on the model. Let's impose that $$ \phi$$ and its derivative is zero at the wall for all $$\theta$$ The steady state Fokker Plank equation for this system is then

$$
0 = \partial_x \big( ( \mu \partial_x \phi - v \cos \theta ) \mathcal{P} + D \partial_x \mathcal{P} \big) + \partial_{\theta} \big( \tau^{-1} \partial_{\theta} \mathcal{P} + \mu_r \partial_{\theta} \phi \mathcal{P} \big) \tag{1} \label{eqn:fokker-plank}
$$

Even without the active propulsion, there is still some peculiarity in the system in the general case. From the stochastic ODEs the spatial and angular degree of freedom both fluctuate, but at at <i>different temperatures</i>. When these degrees of freedom do not interact (i.e $$\phi = \phi_1(x) + \phi_2(\theta)$$) and $$ v = 0$$ then the system is a standard equilibrium one since from independence of the DOFs we expect $$ \mathcal{P} (x, \theta) = \mathcal{P}_1(x) \mathcal{P}_2(\theta)$$ with each . But if we have a general $$\phi$$ then $$x$$ and $$\theta$$ are coupled, which can lead to non equilibrium currents even in the absence of a self propulsion velocity. This is in line with [previous considerations]( https://tekeh.github.io/2019-03-22-thermal-beads/ ).

As coupling can introduce phase space currents, it is not obvious that we will be guaranteed zero work processes, even without self propulsion, in a physical system of this type. Indeed the [previous post](https://) linked to above shows that for a simple 2 node elastic chain we can extract work from out stochastic thermodynamic framework. Because of this trying to get zero work results simply by changing the potential seem like they would not work. The original potential function from before is in some ways more convenient as the coupling is "weak" in some sense with only the heaviside term multiplying the angular energy. 

We can integrate this equation over all angles  $$\theta $$, and then assume no spatial flux to yield the condition

$$
0 =  \mu \int^{2 \pi}_0 \partial_x \phi \mathcal{P} d\theta - v m_1 + D \partial_x \rho \label{eqn:zero-flux} \tag{2} 
$$

where $$m_n(x) = \int^{2 \pi}_0 \mathcal{P} \cos n\theta \quad d\theta $$. If we multiply by $$\cos n\theta$$ first beforewe integrate we instead get the moment equation

$$
 \partial_x \big( ( \mu \int^{2\pi} \cos n\theta \partial_x \phi \mathcal{P} d\theta - \frac{v}{2} (m_{n+1} + m_{n-1} ) + D \partial_x m_n \big) = n^2 \tau^{-1} m_n - n \mu_r \int^{2\pi}_0 \cos n\theta \partial_{\theta} \phi \mathcal{P} d\theta
$$

The definition of the mechanical pressure on the right hand side wall in the system is

$$
\begin{equation}
\begin{aligned}
P 	&= \int_{x_w}^{\infty} \int^{2\pi}_0  \mathcal{P} \partial_x \phi dx d\theta \\
	&= \mu^{-1} \int_{x_w}^{\infty} \big( v m_1 - D \partial_x \rho \big) dx \\
	&= \frac{v}{\mu} \int_{x_w}^{\infty} m_1 dx + \frac{D}{\mu} \rho_0
\end{aligned}
\end{equation}
$$ 

With $$\rho_0 = \rho(x_w)$$. Integrating Eq \ref{eqn:fokker-plank} over all positions yields a similar zero flux condition.

$$
0 = \tau^{-1} \partial_{\theta} f(\theta) + \mu_r \int^{\infty}_{-\infty} \partial_{\theta} \phi \mathcal{P} dx  
$$

The work output for a 2 parameter harmonic wall is, following the framework of stochastic thermodynamics

$$
\begin{equation}
\begin{aligned}
d \mathcal{W} &= \langle \partial_{x_w} \phi  \rangle  d x_w + \langle \partial_{\lambda} \phi \rangle d \lambda \\
		&= - P d x_w + \langle \partial_{\lambda} \phi \rangle d \lambda
\end{aligned}
\end{equation}
$$

We will now look specifically at some potential functions

<h3> Product Form $$  \phi =  \phi_1(x) \phi_2(\theta) $$  </h3> 

In this specific case let us use

$$
\phi_1 = \lambda\Big[ x^2 H(-x) + (x - x_w)^2 H(x - x_w) \Big] \quad \phi_2 =\kappa \cos 2 \theta + 1
$$

For this potential $$ \langle \partial_{\lambda} \phi \rangle = \lambda^{-1} \langle \phi \rangle $$. We can calculate it in the following way, within the right hand wall

$$
\begin{equation}
\begin{aligned}
\langle \phi \rangle &= \lambda \int_{x_w}^{\infty} \int_0^{2\pi}  (x - x_w)^2 (\kappa \cos(2\theta) + 1 ) \mathcal{P} dx d\theta \\ 
				&= \frac{1}{2} \int_{x_w}^{\infty} \int_0^{2\pi}  (x - x_w) \partial_x \phi \mathcal{P} dx d\theta \\ 
				&= \frac{1}{2} \int_{x_w}^{\infty} (x - x_w) (v m_1 - D \partial_x \rho) dx \\
				&= \frac{1}{2}  D \int^{\infty}_{x_w} \rho(x) dx + \frac{v}{2} \int_{x_w}^{\infty} (x - x_w) m_1 dx 
\end{aligned}
\end{equation} 
$$

when $$ v = 0 $$ we have the simple expression

$$
d \mathcal{W} = - \frac{D}{\mu} \rho(x_w) d x_w + \frac{D}{2 \lambda \mu} \Big( 2 \int_{x_w}^{\infty} \rho(x) dx \Big) d \lambda
$$

When $$v = 0$$ the [solution for the density profile in the bulk must be flat](link), therefore we write $$ \rho(x_w) = (\mathcal{N} - \mathcal{N}_w)/x_w $$.

$$
d \mathcal{W} \propto -\mathcal{N} d(\ln x_w ) + \mathcal{N}_w d ( \ln x_w \lambda^{1/2} )
$$

As $$\mathcal{N}$$ is a constant the first term will disappear under a loop integral. Thus only the second term is worth investigating. The term will vanish only if $$\mathcal{N}_w$$ depends on the potential parameters only through the form implied by the differential i.e $$ \mathcal{N}_w = \mathcal{N}_w( x_w \lambda^{1/2}) $$. This is manifestly true if we assume a spatial boltzmann distribution everywhere. We need to calculate $$\mathcal{N}_w$$ within this model. Using Eq \ref{eqn:zero-flux} we have that $$ D \partial_x \rho = - \mu \partial_x \phi_1 ( \kappa m_2 + \rho) $$, Integrating up gives 

$$
\rho = \rho(x_w) e^{ - \frac{\mu}{D} \phi_1} - \frac{\kappa \mu}{D} e^{- \frac{\mu}{D} \phi_1} \int_{x_w}^{x} \partial_t \phi_1 m_2 e^{ \frac{\mu}{D} \phi_1} dt 
$$

After some more calculation, and a couple of changes of variable we can show that

$$
\mathcal{N}_w/ \mathcal{N} = \frac{\sqrt{2 \pi D/ \lambda \mu }}{x_w + \sqrt{2 \pi D/ \lambda \mu} } \Bigg[ 1 - \frac{\kappa x_w}{\mathcal{N}} \int_0^{\infty} \frac{d \bar u}{\sqrt{\pi}/2} e^{-\bar u^2 /2} \int_0^{\bar u} d \bar z \partial_{\bar z} \Big( e^{\bar z ^2/2} \Big) m_2 ( \sqrt{\frac{D}{\lambda \mu}} \bar z + x_w ) \Bigg] 
$$

The first term is the first, uncorrected term, and scales in the appropriate way as to derive zero work output. The second term (related to the [Dawson function?]( https://en.wikipedia.org/wiki/Dawson_function )) is the correction due to the imbalance of temperatures in this model (remember here $$v = 0$$). This term would need to produce the specific funcitonal dependence necessary for zero work, which we should not expect a priori.

When the thermal bath flucuations match this is definitely satisfied. By noting the full distribution will be given by a Boltzmann (verifiable by substituting answer into Fokker Plank equation) we get that

$$
m_2(  \bar z\sqrt{  D/\lambda \mu}  + x_w )  = \mathcal{N} \frac{e^{-\bar z^2 /2} I_1(\kappa \bar z^2/2)}{x_w + I_0(\kappa \bar z ^2 /2)  \sqrt{2 \pi D / \lambda \mu }} \quad \text{ (inside wall) }
$$

Which clearly satisfies the necessary functional form for the number of particles in the wall, and thus will give zero work output under all cyclic protocols.

For the general temperature imbalance we can calculate the work output to first order in the difference. Let us wrtie Eq \ref{eqn:} $$ \mathcal{L} \mathcal{P} = 0$$. We wish to peturb away from an exactly soluble limit. Take $$ (\tau \mu_r)^{-1} = D/\mu $$ - in this limiit Eq \ref{eqn:} will be written $$ \mathcal{L}_0 \mathcal{P}_0 = 0$$. $$ \mathcal{P}_0$$ is then the Boltzmann solution. Now suppose that the temperatures are nearly the same, with $$ \tau \mu_r = \frac{\mu}{D} (1 + \epsilon) + \mathcal{O}(\epsilon^2)$$. We can also expand our solution to first order so that $$ \mathcal{P} = \mathcal{P}_0 + \epsilon \mathcal{P}_1 + \mathcal{O}(\epsilon^2)$$ and collect terms to first order to yield

$$
(\mathcal{L}_0 + \epsilon \mathcal{L}_1 ) ( \mathcal{P}_0 + \epsilon \mathcal{P}_1 + ...) \\
\rightarrow \mathcal{L}_1 \mathcal{P}_0 = - \mathcal{L}_0 \mathcal{P}_1
$$

The LHS can be quickly computed

$$
\mathcal{L}_1 \mathcal{P}_0 = \frac{\phi_1 \mu}{\tau D^2} \Big( \frac{\mu \kappa}{D} ( 1 - \cos 4 \theta ) \phi_1 - 4 \kappa \cos 2 \theta \Big) \mathcal{P}_0\\
\text{where} \\
\mathcal{L}_1 f = \frac{\mu}{\tau D^2}  \partial_{\theta} \Big( \partial_{\theta} \phi f \Big)
$$

We can then expand the first order correction to the distribution as a fourier series $$ \mathcal{P}_1 = a_0/(2 \pi) + \pi^{-1} \sum a_n \cos (n \theta )$$. We can then compare the coefficients 

$$
\partial_x \Big( \partial_x m_n + \frac{1}{T} \partial_x \phi_1 m_n + \frac{\kappa}{2} ( m_{n+2} + m_{n-2} ) \Big) - \frac{n^2}{\tau D} + \frac{2 n \kappa}{\tau D T} \phi_1 (m_{n+2} - m_{n-2}) \Big) \\

= \begin{cases}
 \\
 \\ 
 \\

\end{cases}

$$

We wish to calculate the particle number

$$
\begin{equation}
\begin{aligned}
\mathcal{N}_w &= 2 \int_{x_w}^{\infty} ( \rho_0(x) + \epsilon \rho_1(x) ) dx \\
		&= \mathcal{N}_w^{(0)} + 2 \epsilon \int^{\infty}_{x_w} \rho_1 dx  \\

\end{aligned}
\end{equation}
$$

Integrating Eq \ref{eqn:pertubative-pde} over angles gives the following relation

$$
2 \pi \frac{\phi_1^2 \mu^2 \kappa }{\tau D^3} = \partial_x \Big( \frac{\mu}{D} \partial_x \phi_1 ( \kappa a_2 + \rho_1 ) + \partial_x \rho_1 \Big)
$$

<h3> Weak Addtitive Form $$ \phi = \phi_1(x) + \phi_2(\theta) [ H(-x) + H(x - x_w) ] $$ </h3>

Called "weak addtive" because, in a sense, this is one of the weakest couplings as there is no functional dependenc on the $$x$$ for the $$\phi_2$$ apart from ht Heaviside. This is essentially the form initially investigated, ave for the boundary impulse term. For specificity, take 

$$
\phi_1 = \lambda\Big[ x^2 H(-x) + (x - x_w)^2 H(x - x_w) \Big] \quad \phi_2 = \lambda \kappa \cos 2 \theta                
$$



<h3> General Mixed Form $$ \phi = \phi(x, \theta)$$ </h3> 


I'm not sure much can be said about this case  which hasn't been said already. In general will be the hardest to solve for. In this specific case let us use

$$
\phi = \lambda \Bigg( \Big[ (x - x_w)^2 + (x - x_w) (\kappa \cos 2 \theta + 1) \Big] H(x - x_w) + \Big[ x^2 + x (\kappa \cos 2 \theta + 1) \Big] H(-x)
$$

I'm not sure much can be done with this case directly.
