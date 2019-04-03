---
layout: post
title: Some 1A NatSci Extension Problems
tags: [ ]
math: true
---


<script src='https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/MathJax.js?config=TeX-MML-AM_CHTML' async></script>

Here are a collection of some problems to try if you find yourself with spare time

Magnetic Monopole

A particle with electric charge $$q$$ moving through an elctromagnetic field experiences a Lorentz force

$$ \boldsymbol{F} q ( \boldsymbol{E} + \boldsymbol{v} \times \boldsymbol{B} )$$

Magnetic monopoles are hypothetical particles that produce magnetic fields that are not divergencelss (). The magnetic field from a magnetic monoople of strength $$g$$ can be written as

$$ \boldvymol{B} = \frac{g}{\vert \boldsymbol{r} \vert^3} \boldsymbol{r} $$

We fix a magnetic monopole off this strength at the prigin in a space where $$E = 0$$ everywhere. Using Newton's law, write doen the vector equation of motion for a particle of electric charge $$q$$ in this space.

By considering $$\boldsymbol{v} \cdot \boldsymbol{v}$$, show that the speed of the particle is a constant of motion. Show further that the quantity 

$$ \boldsymbol{J}  \Bigg( m \boldsymbol{r} \times \dot{\boldsymbol{r}} - q g \frac{\boldsymbol{r}}{\vert \boldsymbol{r} \vert} $$

is constant.

Show that $$\boldsymbol{J} \cdot \hat{\boldsymbol{r}}$$ is a constant. Describe the motion of the charged particle in the monopole's field.

Iterative Vector Operations

Consider a vector $$\boldsymbol{v}$$ and an arbitrary unit vector $$\boldsymbol{n}$$ in the same space. Describe the action of the operation 

$$ \boldsymbol{v} \rightarrow \boldsymbol{v} + \delta \theta \boldsymbol{n} \times \boldsymbol{v} = (1 + \delta\theta \boldsymbol{A} ) \boldsymbol{v}$$

where $$\delta \theta$$ is a small real number, and $$\boldsymbol{A}$$ is a matrix depending on the components of $$\boldsymbol{n}$$, which you should find. Show that $$ \boldsymbol{A}^T = -\boldsymbol{A}, Tr(\boldsymbol{A}) = 0$, and det($$\boldsymbol{A}$$) = $$0$$.

What is the action of the operator $$ \big( 1 + \alpha\boldsymbol{A}/N \big)^N$$ on a vector $$\boldsymbol{v}$$ as $$N \rightarrow \infty$$? Write this operator in a closed form after the limit taking process.

<i> You may need the following identity </i>

$$ \lim_{N \rightarrow \infty} \Bigg( 1 + \frac{x}{N} \Bigg)^N = e^x $$ 

In the problem sheet you were given the Cauchy- Schwartz inequaltity for two geometric vctors $$ \vert \boldsymbol{a} \cdot \boldsymbol{b} \vert \leq \vert \boldsymbol{a} \vert \vert \boldsymbol{b} \vert$$. This inequality actually takes many forms when considered on more abstract vector spaces with an appropriately defined inner product.
Suppose $$f$$ and $$g$$ are real functions that are elements of the vector space of <i> square integrable functions </i> ($$ \int f(x)^2 dx < \infty$$ and same for $$g$$). ON this space we can define an inner product $$ \langle f, g \rangle = \int fg dx $$. This vector space is used to describe wavefunctions in quantum mechanics.

By considering $$ \int (f + \lambda g)^2 dx $$ as a polynomial in $$\lambda$$, show that Cauchy-Schwarz inequality holds on this vector space.


Summation Tricks

In the examples sheets you calculate $$ \sum^N_{n=0} \cos n \theta $$ and $$ \sum_{n=0}^N \sin n\theta $$. We will extend the idea of that question to calculate a few more sums.

Evaluate the following sums for $$ m = \pm 1$$.

$$ \sum_{r=1}^{N} \frac{\cos r \theta }{r^m} $$

Show that

$$ \sum_{r=0}^{N} \pmatrix{ N // r} \cos r \theta = \cos (N\theta) \Big( 2 \cos \frac{\theta}{2} \Big)^N $$

Where $$\vert \delta \vert < 1$$, work out the value of the infinite sum

$$ \sum_{n=0}^{\infty} \delta^n \cos n \theta $$

Evaluate the sum

$$\sum_{r=0}^N \cos( r \theta_1) \cos(r \theta_2) \cos(r \theta_3) $$

(Harder) Consider the more general sum of cosines products. Show that


$$\sum_{r=0}^N \cos( r \theta_1) \cos(r \theta_2) \cos(r \theta_3)... \cos(\theta_{2k})  = \frac{1}{2^{2k}} \sum_{s = \pm 1}  \frac{1 - \delta( \boldsymbol{s} \cdot \boldsymbol{\theta}) }{1 + \delta^2 - 2 \delta \cos( \boldsymbol{s} \cdot \boldsymbol{\theta}) }$$

Where blah blah

In the case where the angles are actually the same $$\theta_m = \phi$$ show by a counting argument that we can rewrite the sum further as

$$ \frac{1}{2^{2k}} \sum_{l=0}^{2k} \pmatrix{ 2k // l} \frac{1 - \delta \cos(2(k-l) \phi)}{1 + \delta^2 - 2\delta \cos(2(k-l)\phi)} $$

Check this formula for the values of $$\phi = \pi/2, \pi$$.

Representations of the Dirac Delta

The Dirac Delta $$\delta(x)$$ is a mathematical object which is zero everywhere (except the origin, where it is undefined) and satisfies

$$ \int^a_b \delta(x) f(x) dx = f(0)$$

For an positive $$a,b$$, and an arbitrary function $$f$$. Deduce the value of $$\int^a_{-b} \delta(x) dx $$.
The delta function is a strange object, but can be expressed as the limit of certain functions. Below  we will take a brief look at some of these representations.

a) One representation can be written in the form

$$ \delta(x) \lim{a \rightarrow 0} \frac{1}{\sqrt{2 \pi a^2}} e^{-x^2/2a^2} $$

Sjetch the RHS for various values of $$a$$. INtegrate this expression over all $$x$$ and verify that both sides agree <i> (For this question you may assume that integrating then taking the liit will agree with taking the limit and then integrating) </i>.

b) Another representation is the expression

$$ \delta(x) = \lim_{c \rightarrow \infty} \frac{e^{- c\vert x \vert}}{\mathcal{N}} $$

What must $$\mathcal{N}$$ be to make this a valid expression?

Consider the integral

$$ \int^{\infty}_{-\infty} \Bigg( \lim_{c \rightarrow \infty 0} \frac{e^{-c \vert x \vert}{\mathcal{N}} \Bigg) \cos(ax + \phi) dx $$

Find the value of the integral and compare your result with Eq \ref{}.

Phase Portraits

Population dynamics provide many examples of very complex, highly non-linear systems. A simple model is the predator prey model. Let $$x(t)$$ be the population of the prey species at a time $$t$$, and $$y(t)$$ the population of the predator species. Their populations can be modelled by the coupled equations

$$\frac{dx}{dt} = Ax - B x y $$
$$\frac{dy}{dt} = - Cx + BDx y $$

Where $$a, B, C, D$$ are constants. Briefly justify the terms in each equation (i.e speculate on their origin froma  population dynamics point of view).

Eliminate t to show that

$$ \frac{dy}{dx} = \frac{-Cy + Dxy}{Ax - Bxy} $$

By seperation of variables , show that we can define an explicity solution to this equation

$$A \ln y - C \ln x - By - Dx = \Gamma$$

Where $$\Gamma$$ is an integration constant depending on the inital conditions, such as the number of each species present at $$t=0$$. The above equation implicitely defines a curve in the $$x-y$$ plane. Below it is plotted for various values of $$\Gamma$$. With your favourtie plotting program, draw the contours for various values of $$\Gamma$$ when $$A = 2/3 , B = 4/3, C = D = 1$$. 



