---
layout: post
title: "Why researching fusion concepts in parallel makes sense"
author: "Samuel Ward"
categories: thoughts
tags: [draft]
image: python_packaging.png
---

## Some title

### A simple problem

Suppose you have a simple pass/fail test - for example, rolling a six on a die. With one chance, your probability of success is 1/6.

If you fail on the first attempt and are given a second try, then what is your probability of success now? Hint: it's not 2/6 (this would imply you always succeed by the 6th attempt).

It's the probability that you _either_ pass the first attempt _or_ fail the first attempt and pass the second. That equates to:

$$
P_{\mathrm{pass}} = \frac{1}{6} + \frac{5}{6}\times\frac{1}{6}  
$$

How about three dice rolls? 

$$
P_{\mathrm{pass}} = \frac{1}{6} + \frac{5}{6}\times\frac{1}{6} + \left( \frac{5}{6}\right)^{2}\times\frac{1}{6}  
$$

How about for $n$ attempts? We essentially have a summation, which can be expressed by this recursion relation:

$$
P_{\mathrm{pass},n} = P_{\mathrm{pass},n-1} + p_{\mathrm{fail}}^{n-1}p_{\mathrm{pass}} 
$$

Where little $p$ signifies the probabilities regarding a single event - i.e. the probability any die yields a 6.

So if you have an extra attempt at passing a test, your overall probability of success increases like:

$$
\Delta P_{\mathrm{pass}} = p_{\mathrm{fail}}^{n-1}p_{\mathrm{pass}}
$$

That applies _after_ the first roll. For a continuum, where $\Delta n\rightarrow0$:

$$
\frac{dP_{\mathrm{pass}}}{dn} \approx \frac{\Delta P_{\mathrm{pass}}}{\Delta n} = \frac{p_{\mathrm{fail}}^{n-1}p_{\mathrm{pass}}}{n-(n-1)} = p_{\mathrm{fail}}^{n-1}p_{\mathrm{pass}}
$$

If you integrate this, you find

$$
P_{\mathrm{pass}} \approx p_{\mathrm{pass}} + \frac{p_{\mathrm{pass}}}{\mathrm{ln}\left(p_{\mathrm{fail}}\right)}\left[ e^{\left(n-1\right)\mathrm{ln}\left(p_{\mathrm{fail}}\right)}-1\right]
$$

which gives the correct behaviour for $n=1$. Remember, $\mathrm{ln}\left(p_{\mathrm{fail}}\right)<0$ always, since the probability of failure is always between 0 and 1. For $n\rightarrow\infty$, we see

$$
P_{\mathrm{pass}}\rightarrow p_{\mathrm{pass}}-\frac{p_{\mathrm{pass}}}{\mathrm{ln}\left(1-p_{\mathrm{pass}}\right)}
$$

which essentially hovers between 1 and $\sim$ 1.3 (it should remain close to 1):

![error term](https://samuelhward.github.io/assets/img/parallel_fusion_error_term.png?raw=true "error term")

This error likely comes from the fact that we derived our equation for $P$; we assumed $P$ perfectly described the recursion relation via some nice and smooth function over $n$, but we only derived that in the range $1<n<\infty$. So we missed that small bit of probability between $0<n<1$. 

Can we quantify that error? Well, between $n=0$ and $n=1$, our probability of success, $P_{\mathrm{pass}}$, increases from 0 to $p_{\mathrm{pass}}$ ; we go from rolling no dice to rolling one die. To first order, the average value of $P_{\mathrm{pass}}$ is  therefore $p_{\mathrm{pass}}/2$, assuming that whatever the function $P_{\mathrm{pass}}$ looks like near $n\sim0$ resembles a straight line. So the bit missing in the original integration, which is what defines $P_{\mathrm{pass}}$, is roughly $p_{\mathrm{pass}}/2$: that's between 0 and 0.5, which is roughly the range covered by the graph above. In fact, most of that graph is a straight line, which reflects the fact that the error term increases with $p_{\mathrm{pass}}$.

Though I'm not sure what is happening as $p_{\mathrm{pass}}\rightarrow 1$...


