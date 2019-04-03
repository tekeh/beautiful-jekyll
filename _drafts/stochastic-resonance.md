---
layout: post
title: Stochastic Search 
image: /img/hello_world.jpeg
tags: [probability]
math: true
---


<script src='https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/MathJax.js?config=TeX-MML-AM_CHTML' async></script>

A basic sort of computatinla problem is that of searching for a specific elemnt within a larger list of elements Many algorithms exist to complete this task, but here we will investigate the usefulness of a certain type of <b> Stochastic Search Algorithm </b> which are algorithms which make use of randomness. In partiular we'll look at the effect of stochastic resets on the ability to find a certain elemnt in a $$d-dim$$ array. Let's state the problem more exactly.

Imagine our data elements living on a $$d$$-dim lattice with a total of $$L^d$$ sites, and our desired datum lives on one of these sites at position $$ \bf x_0$$ (where we start at the origin). Does a resettign practice yield any advantages?

If we were to try each site sequentially, then we'd have an algorithm which needed $$\mathcal{O}(L^d)$$ and about as much memory. 
