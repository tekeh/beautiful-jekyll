---
layout: post
title: Partition Function Level Sets
image: /img/hello_world.jpeg
tags: []
math: true
---


<script src='https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/MathJax.js?config=TeX-MML-AM_CHTML' async></script>

Suppose I want to find a $$\beta$$ which satisfies the following sort of equation:

$$
k = \int e^{\beta h(\boldsymbol{\alpha})} d \boldsymbol{\alpha} 
$$

where $$k >0$$ is a constant and $$h$$ is a known real function of the parameters $$\boldsymbol{\alpha} \in \mathbb{R}^n$$. How might I do so? Here we present one possible approximate route, and briefly analyse the resulting equation. If the exponent has a suitably steep minima which we can expand around, then we might try a saddle point approximation

$$
\begin{equation}
\begin{aligned}
k &= e^{\beta h({\boldsymbol{\alpha}*)}} \int e^{(\alpha - \alpha*)_i(\alpha - \alpha*)_j \frac{\partial^2 \beta h}{\partial \alpha_i \partial \alpha_j} } d \boldsymbol{\alpha} \\
 &\approx e^{\beta h({\boldsymbol{\alpha}*)}} \Big(\frac{(2\pi)^n}{det \frac{\partial^2 \beta h}{\partial\alpha_i \partial\alpha_j} } \Big)^{1/2} \\
\end{aligned}
\end{equation}
$$

Upon rearranging

$$
\begin{equation} \label{eq:monge-ampere} \tag{1}
\implies det \frac{\partial^2 \beta h}{\partial\alpha_i \partial\alpha_j} \vert_{\boldsymbol{\alpha = \alpha*}} = \frac{1}{k^2} e^{2 \beta h({\boldsymbol{\alpha}*)}} (2 \pi)^n
\end{equation}
$$

This is similar to a nonlinear PDE called the **Monge-Ampere Equation**, which has uses in diffeential geometry and optimal transport (apparently). The similarity is superficial - remember $$h$$ is known, and the expressions hold at a minima. 

$$\beta$$ is the solution to the non-linear algebraic equation which now involves no integrals. It still involves a determinant of the hessian, so it would be interesting to see if we could simplify this expression. This _could_ be simplified exactly in a number of special cases. Some of the resulting equations for $$\beta$$ are nonsensical, and thus betray the crassness of the saddle point approximation. We list some cases below.

#### $$h = h(\boldsymbol{c \cdot \alpha})$$ (const $$\boldsymbol{c}$$)

In this case the LHS becomes

\begin{equation}
\begin{aligned}
	det \frac{\partial^2 h}{\partial\alpha_i \partial\alpha_j} &= det(c_i c_j h'') = 0 \\
\end{aligned}
\end{equation}

where the last equality comes from the fact that the tensor is of rank 1. Clearly Eq \eqref{eq:monge-ampere} makes little sense and therefore [another approach is needed]().

#### $$h =h(\vert \boldsymbol{\alpha}\vert)$$  (rotational symmetry)

Denote $$ \vert \boldsymbol{\alpha}\vert = \alpha$$. In this case the LHS becomes

$$
\begin{equation}
\begin{aligned}
	det \frac{\partial^2 h}{\partial\alpha_i \partial\alpha_j} &= det\Big[ \delta_{ij} \frac{h'}{\alpha} + \alpha_i \alpha_j \big( \frac{h''}{\alpha^2} - \frac{h'}{\alpha^3} \big) \Big] \\
		&= \Big( \frac{h'}{\alpha} \Big)^{n-1} h'' = \frac{1}{n\alpha} \big((h')^n \big)'
\end{aligned}
\end{equation}
$$

The last line comes from considering the product of eigenvalues of the derived second rank tensor.

**[References]**

