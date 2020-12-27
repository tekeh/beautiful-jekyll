---
layout: post
title: Circumventing Bias
image: /img/hello_world.jpeg
tags: [probability, stub]
math: true
---


<script src='https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/MathJax.js?config=TeX-MML-AM_CHTML' async></script>

Suppose you have a coin which has probability $$p$$ of giving heads when it is flipped. If $$p \neq 1/2$$ then the coin is called _biased_. Despite the biased nature of the coin, it is still possible to use it to generate fair "flips". 

Consider flipping the coin twice, independently. The sample space $$\mathcal{S} = \{ HH, HT, TH, TT\}$$ with probabilities, $$p^2, p(1-p), p(1-p), (1-p)^2$$. The two mixed results have equal probability, so to simulate an even RV, we merely flip twice and treat $$HT$$ as "tails" and $$TH$$ as "heads". If we get any other outcome we retry. This is called the _Von Neumann method_. Note that unlike in the case of a truly fair coin, this method has a running time which is not deterministic, and could (technically) go on forever. The expected running time, $$T$$, which is the number of flips, is ($$P=2p(1-p)$$)

$$
E(T) =  \frac{1}{p(1-p)}
$$

with a variance given by

$$
{\rm VAR} (T) = \frac{1 - 2p(1-p)}{p^2(1-p)^2}
$$

This demonstrates that we can implement strategies which circumvent bias (at least in this case), but not necessarily efficiently.
