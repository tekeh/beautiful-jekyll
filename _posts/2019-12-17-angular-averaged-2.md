---
layout: post
title: Integrals over Solid Angles (Part 2)
image: /img/hello_world.jpeg
tags: [statistics, linear algebra]
math: true
---


<script src='https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/MathJax.js?config=TeX-MML-AM_CHTML' async></script>

In a [previous post](angular-averaged) we considered averaging quantities built from tensors over all angles. We know wish to extend the ides in that post to integrals of the form

$$ 
\langle e^{\bf n^T H n} \rangle = \int e^{H_{ij} n_i n_j} \frac{d\Omega^d_{\bf n}}{S_d} = f_d({\bf H})
$$

where $$ H_{ij} $$ is a second rank tensor, symmetric without loss of generality. Ideally will would like to reason what the solution looks like in arbitrary dimension. Specific solutions can sometimes be worked out directly. For exmaple in $$d = 2$$ we can diagonalise the quadratic form in the exponent (it is a scalar and invariant to the choice of basis, and the integration measure doesn't change under a rotation of the axes)

$$
\begin{equation} \label{eq:f2} \tag{1}
f_2({\bf H}) = \int e^{\lambda_{1} \cos^2 \theta + \lambda_2 \sin^2 \theta} \frac{d\theta}{2\pi} = e^{(\lambda_{1} + \lambda_{2})/2} I_{0}\Big(\frac{\lambda_{1} - \lambda_{2}}{2}\Big)
\end{equation}
$$

where $$\lambda_{1, 2}$$ are the eigenvalues (i.e the invariants) of $$\bf H $$. As expected, the result is symmetric under the exchange of eigenvalues. How else might we derive Eq \ref{eq:f2}?

![Numerical tests](/img/ang_avg_expellipse.png)


#### $$d$$-dim

The first thing to notice is that we can decompose a symmetric rank two tensor into a isotropic part and a symmetric traceless part i.e $$ H_{ij} = \frac{H_{kk}}{d} \delta_{ij} + T_{ij} $$. Which simplifies our expression to 

$$
f_{d}({\bf H}) = e^{H_{kk}/d} \int e^{T_{ij} n_{i} n_{j}} \frac{d\Omega^d_{\bf n}}{S_{d}} = e^{H_{kk}/d} f_{2}({\bf T})
$$ 


The first thing we should do is diagonalise the quadratic form to yield

$$
 f_{d} = \int e^{ \sum_{i=1}^d \lambda_i n_i^2} \frac{d\Omega^d_{\bf n}}{S_{d}}
$$ 

Where again $$\lambda_i$$ denote the eigenvalues of $$\bf T$$ (and thus $$\bf H$$). Note that we can easily see that

$$
\sum_k \partial_{\lambda_k} f_{d} = f_{d} \label{eq:plane-pde} \tag{2}
$$ 

Due to $${\bf n}$$ being of unit magnitude. We can also see that

$$
 \frac{\partial}{\partial T_{km}} \frac{\partial f_{d}({\bf T})}{\partial T_{km}} \equiv \frac{\partial }{\partial {\bf T}} : \frac{\partial f_{d}({\bf T})}{\partial {\bf T}} = f_d({\bf T})
$$

And so we seem to get a $$d^2$$ version of the Laplacian (although this equation is actually a consequence of the Eq $$\ref{eq:plane-pde}$$ and contains no new information). This could in principle be reduced by considering the principal frame.

From here it seems hard to proceed. We can say some basic things, such as that $$f_d$$ is obviously bounded by the range of eigenvalues

$$
e^{\lambda_{\rm max}} \geq f_d \geq e^{\lambda_{\rm min}}
$$

And can be represented as a multivariable taylor series


$$
f_d = \sum_{k_1 k_2 ... k_d}^{\infty} \frac{\langle n_1^{2 k_1} n_2^{2k_2} ... n_d^{2k_d} \rangle}{k_1! k_2! ... k_d!} \lambda_1^{k_1} \lambda_2^{k_2}...\lambda_d^{k_d}
$$

Not much insight (yet).

