---
layout: post
title: Thermal Beads
image: /img/hello_world.jpeg
tags: [stochastic processes, thermodynamics]
math: true
---


<script src='https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/MathJax.js?config=TeX-MML-AM_CHTML' async></script>

A simple calculation to help me understand something larger. Suppose there are two beads in between two parallel walls which can move in one dimension perpendicular to the plane of the walls. They are connected together by elastic spring with strength $$k_{12}$$, and each is further connected to the wall initially closest to them by springs of constant $$k_1 $$ and $$k_2$$ respectiviely. They are both held at different temperatures $$T_1$$ and $$T_2$$, again respectively. Withiin the framework of stochastic differential equations we can write 

$$
\begin{equation}
\begin{aligned}
\dot x_1 &= k_{12} \mu (x_2 - x_1) - k_1\mu x_1 + \sqrt{2 T_1} \eta_1 \\
\dot x_2 &= k_{12} \mu (x_1 - x_2) - k_2\mu x_2 + \sqrt{2 T_2} \eta_2
\end{aligned}
\end{equation}
$$

or in a vector form

$$
{\bf \dot x} = - {\bf \hat K} {\bf x} + {\bf \hat B} {\bf \eta}  \\
\text{with} \\
{\bf \hat K} = \mu  \pmatrix{ (k_1 + k_{12}) & -k_{12} \\ -k_{12} & (k_{12} + k_2) } \label{eqn:k-mat} \tag{1}\\
 {\bf \hat B} =  \pmatrix{ \sqrt{2T_1 } & 0 \\ 0 & \sqrt{2T_2 } }
$$

By rotating this equation we can decouple the problem into two independent normal modes subject to brownian motion

$$
{\bf \dot u} = - {\bf \hat \Lambda} {\bf u} + (2 {\bf \hat D})^{1/2} {\bf \eta}  \\

\text{with}\\
 {\bf \hat \Lambda} = \mu  \pmatrix{ \lambda_1 & 0 \\ 0 & \lambda_2 } \\
 (\bf{ \hat D})^{1/2} =   \pmatrix{ \sqrt{T_1 \cos^2 \phi + T_2 \sin^2 \phi } & 0 \\ 0  & \sqrt{T_1 \sin^2 \phi + T_2 \cos^2 \phi } }

$$

With $$\tan \phi = \frac{k_1 - k_2}{k_{12}} \Big[ \sqrt{1 + (\frac{k_{12}}{k_1 - k_2})^2 } - 1 \Big] $$. Each normal mode experiences some modified noise, but Tr( $${\bf D}$$ ), which can be related to the total power in the harmonic modes, is conserved. Since each mode is an independent brownian process, the steady state solutions can then be written explicitely as the product of two Boltzmann weights in the normal coordinates. Once roated back we get that the steady state distribution is a quadratic form in the original coordinates.

$$
\mathcal{P}_{ss}(x) = \frac{1}{\sqrt{  (2 \pi)^2 \text{det} {\bf \hat C} }}\exp \Big( - \frac{1}{2} {\bf  x}^T {\bf \hat C}^{-1} {\bf  x} \Big) \tag{2} \label{eqn:prob-ss}
$$

where $$\bf{ C} = \langle \bf{x} \otimes \bf{x} \rangle $$ is the covariance matrix which satisfies the <b> Lyaponov equation </b> 

$$ {\bf  K C + C K^{T}} = 2{\bf D} \tag{3} \label{eqn:lyaponuv} $$. 


Usually some algorithm is implemented to solve the equation in the general case such as the <b> Bartels-Stewart algorithm </b> (suitable for sparse $${\bf K}$$ and low-rank $${\bf D} $$ ), but for our 2x2 matrices we can just solve elementwise. It was shown that this steady state equation will produce a phase space flux unless the covariance matrix is a multiple of $$\bf K^{-1}$$.

 For reference, the associated Fokker-Plank equation can be written

$$
\partial_t \mathcal{P}(\bf{x}, t) = \nabla \cdot \Big[ \bf{ D} \nabla \mathcal{P} - \bf{ \hat K} \bf{ x}  \mathcal{P} \Big] \equiv \nabla \cdot {\bf J}
$$

To work out the thermodynamics we need to first calculate the quasistatic energy in terms of the parameters of the system (in this case the spring constants $$k_1, k_2, k_{12}$$). 

$$
\begin{equation}
\begin{aligned}
\langle V \rangle &= \frac{1}{2} \langle \bf{x}^T \bf{ \hat K} \bf{ x} \rangle = \frac{1}{2} K_{ij} \langle x_i x_j \rangle = \frac{1}{2} \text{Tr} \big( K C \big) = \frac{1}{2} \text{Tr}\big( D \big) \\
\langle V \rangle &= \frac{1}{2} (T_1 + T_2)
\end{aligned}
\end{equation}
$$

As we should expect from equipartition with respect to the normal modes.

$$ \langle \mathcal{W} \rangle = \langle \partial_{\alpha_i} V \rangle d \alpha_i$$ where $$\alpha_i$$ are the controllable parameters of the system. In this case they would be the strength of the springs attached to the masses. We can see that $$ \langle \partial_{\alpha} V \rangle = \frac{1}{2} \partial_{\alpha} K_{ij} \langle x_i x_j \rangle = \frac{1}{2} C_{ij} \partial_{\alpha} K_{ij} $$. The term would be a total derivative under the condition stated before for zero phase space flux  (i.e $$ C \propto K^{-1}$$) but in general it will not be, and we will thus get work out when undergoing cyclic protocols. Let us take the simplest case where we change $$k_1$$ and $$k_2$$ in tandem, keeping the spring connecting the two masses unchanged. The relevant part of the infintesimal work is 

$$
\langle d \mathcal{W} \rangle = \frac{1}{2} C_{11} dk_1 + \frac{1}{2} C_{22} dk_2
$$ 

Is this an exact differential? If it is then all loop integrals vanish. We can check to see whether there is a consistent potential function geneerating this one-form (i.e look for $$f$$ s.t $$ df = \langle d \mathcal{W} \rangle $$). Integrating the first term using the expression for $$ \bf{\hat C}$$ appearing in [Eq S4 in Federico Gnesotto, Benedikt Remlein, and Chase Broedersz's paper]( https://arxiv.org/pdf/1809.04639.pdf ) 

$$
\frac{1}{2} \int C_{11} dk_1 = T_1 \ln \big[ (k_1 + k_{12}) (k_2 + k_{12}) - k^2_{12}  \big] + \\ 
\frac{( T_2 - T_1) k^2_{12} }{ (k_2 + k_{12})^2 + k_{12}^2 } \Big( \ln \bigg[ \frac{k_1 + k_2 + 2 k_{12}}{ (k_1 + k_{12})(k_2 + k_{12}) - k_{12}^2 } \bigg] + \ln \big[ k_2 + k_{12} \big]  \Big) + A(k_2, k_{12}) \tag{4} \label{eqn:potential}
$$

$$\frac{1}{2}\int C_{22} d k_2 $$ should be the same expression as Eq \ref{eqn:potential} under swapping $$ T_1 \rightarrow T_2, k_1 \rightarrow k_2 $$ and $$ k_2 \rightarrow k_1$$ by symmetry (of course with a new arbitrary function $$A'(k_1, k_{12})$$). This shows there is no potential function which can generate this one-form, and so we can have non-zero work flux when $$T_1 \neq T_2$$. We can form a heat engine when there is something like a temperature gradient (surprise surprise /s).

Another way to see this condition is in terms of the stady state profile being only a function of the Potential and no other details i.e $$\rho = \rho(V)$$ alone. Clearly, unless $$\bf{ \hat C} \propto \bf{ \hat K}^{-1} $$ this is not the case for the quadratic form in Eq \ref{eqn:prob-ss}. 

References:

{1} [ Non-equilibrium dynamics of isostatic spring networks ](https://journals.aps.org/prl/abstract/10.1103/PhysRevLett.121.038002)
