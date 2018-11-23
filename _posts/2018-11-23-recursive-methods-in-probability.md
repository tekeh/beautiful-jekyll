---
layout: post
title: Recursive Methods in Probability
image: /img/hello_world.jpeg
tags: [probability, calculation methods]
---

Problems can of course be solved in mutliple ways. Sometimes the natural, methodical solution to a problem is very lengthy, so knowing some tricks is useful. One such trick is recursive reasoning, which can prove useful in certain types of probability problems and puzzles. I like these methods since the idea is sufficiently basic that anyone can use it without formal probabilistic training (unlike other Markov system techniques).

Consider the following problem:

1) What is the expected number of coin flips to get n heads in a row?

So when n = 1 then the answer is obviously 2. One way to approach this problem in the general case is to define some family of expectations with a recursion relation connecting them. Define $E_n$ be the expected number of coin flips needed to first get n heads in a row. The variables $E_n$ follow the recursion:

$$ E_{n+1} = \frac{1}{2} ( 1 + E_{n} ) + \frac{1}{2} ( 1 + E_{n+1} + E_{n} ) $$

This expression relies on the fact that to get $n$ heads in a row we must first have had $n-1$ heads in a row. Therefore from having $n-1$ heads 2 things can occur; either we get another head with a probability half (which would lead to just one more flip), or we get a tail and have to start from scratch. The solution to this is then $E_n = 2 ( 2^{n} - 1)$. 

This is nice concept is an example of what is (apparently) called the "Law of iterated Expectations";

$$ E(X) = \sum_i E(X|A_i) P(A_i) $$

where X is some random variable and A_i is a complete partition of the probability space. For the case above A_1 = n-1 heads just flipped and A_2 would be the complement. 

Another property that makes this technique possible is the fact that the coin flipping process is memoryless. After a reset (getting a tail) the expected number of flips to get n heads stays the same. The process does not remember the entire history of the process.

