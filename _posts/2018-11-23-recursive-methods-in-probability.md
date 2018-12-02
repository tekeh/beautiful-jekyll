---
layout: post
title: Recursive Methods in Probability
image: /img/hello_world.jpeg
tags: [probability, calculation methods]
math: true
---


<script src='https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/MathJax.js?config=TeX-MML-AM_CHTML' async></script>



Problems can of course be solved in mutliple ways. Sometimes the natural, methodical solution to a problem is very lengthy, so knowing some tricks is useful. One such trick is recursive reasoning, which can prove useful in certain types of probability problems and puzzles. I like these methods since the idea is sufficiently basic that anyone can use it without formal probabilistic training.

Consider the following problem:

<b> [Heads in a row]: </b> What is the expected number of coin flips to get n heads in a row?

So when n = 1 then the answer is obviously 2. One way to approach this problem in the general case is to define some family of expectations with a recursion relation connecting them. Define $$E_n$$ to be the expected number of coin flips needed to first get n heads in a row. The variables $$E_n$$ follow the recursion:

$$ E_{n+1} = \frac{1}{2} ( 1 + E_{n} ) + \frac{1}{2} ( 1 + E_{n+1} + E_{n} ) $$

This expression relies on the fact that to get $$n$$ heads in a row we must first have had $$n-1$$ heads in a row. Therefore from having $$n-1$$ heads 2 things can occur; either we get another head with a probability half (which would lead to just one more flip), or we get a tail and have to start from scratch. The solution to this is then $$E_n = 2 ( 2^{n} - 1)$$. If the coin is unfair and we have probability $$p$$ of getting a head, then the answer is $$(p^{-n} - 1 )/(1 - p)$$.

This is nice concept is an example of what is (apparently) called the "Law of iterated Expectations";

$$ E(X) = \sum_i E(X|A_i) P(A_i) $$

where X is some random variable and $$A_i$$ is a complete partition of the probability space. For the case above $$A_1 = n-1$$ heads just flipped and $$A_2$$ would be the complement. 

Consider this one other problem:

<b> [Filling Boxes]:</b> You have $$N$$ boxes lined up in a row, and you need to fill each of them with an item. If you can'te remember which boxes you have already filled what is the expected number of box openings needed?

If we could remember the positions we have tried, then the we would of course need $$N$$ boxes exactly. In the memoryless case the answer can be derived via a recursive expression. Define $$E_m$$ to be the expected number of trials left to fill the remaining boxes, given we have already filled $$m < N$$ boxes. WIth this definition $$E_N = 0$$ and in particular we want $$E_0$$.

$$ E_{m} = \frac{m}{N} ( 1 + E_{m} ) + (1 - \frac{m}{N} )( 1 + E_{m+1} ) $$

this can then be rearranged and solved exactly

$$ \sum_{m=0}^{N-1} ( E_m - E_{m+1}) = E_0 = N \sum_{k = 1} ^N \frac{1}{k} $$

Asymptotically this number goes as $$\sim N \log N + \gamma N $$, where $$\gamma = 0.57721...$$ is the Euler-Mascheroni constant. This is opposed to $$N$$ for the case with perfect memory. There is some tradeoff between memory (space) and average number of trials (time). It is also worth noting that in the momryless case our worst case run time is essentially infinite, so there is a long tail of (low probability) instances where we pick the wrong boxes for far longer than the average protocol time.

As a bonus it would be nice to smoothly interpolate between perfect recall and memoryless. Luckily, recursive reasoning also makes this possible!

Let us now say we can remember a finite distance $$r < N $$ into our past i.e we can remember the last $$r$$ boxes we tried in a sort of "one-in-one-out" fashion. What is the expected number of trials to fill now? Using the recursion we can generalise to

$$ E_{m} = \frac{m - r}{N - r} ( 1 + E_{m} ) + \Big(1 - \frac{m - r}{N - r} \Big)( 1 + E_{m+1} ) \qquad m \geq r$$

Under a similar calculation as before this then leads to 

$$ E_0 = r + (N - r ) \sum_{k = 1}^{N - r} \frac{1}{k} $$

Asymptotically we then have that $$E_0 \sim N(1-f) \log( N (1-f) ) + N f + N(1 - f) \gamma  $$ for the case with memory, where we've defined $$f = r/N$$. So we have a smooth interpolation between the memoryless and perfect recall situations. I don't know of any other ways to do this problem that are nicer than this - recursive techniques are nice and simple. 

TE

