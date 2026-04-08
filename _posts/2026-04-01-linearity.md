---
title: 'Linearity'
date: 2026-04-01
permalink: /posts/2026/04/Linearity/
tags:
  - heuristics
---

This is my first blog post! I want to use it to talk a little bit about modeling things with straight lines. This post is about the most powerful model. I hope it's useful!

If given some data, the first relationship a scientist or engineer will propose is a linear relationship. If it works even passibly well, no one will question them. This is because of something called the "linear limit". Consider the relationship we're interested in,

$$y=f(x)$$

where $y$ is the dependent variable, $x$ is the independent variable and $f(x)$ is a continuous *non-linear* function. Maybe it looks like this:

![Image not available](https://sgshindler.github.io/images/blog_posts.png)

If you shrink the range of x-values, $f(x)$ will always get closer and closer to a straight line.

![Alt text](image_path_or_url) 

more...

![Alt text](image_path_or_url)

a little bit more...

![Alt text](image_path_or_url)

Calculus is largely based on the idea that if you consider an infinitesimally narrow domain of x-values, then over that domain, the function actually *is* a straight line. Math people make a big stink about things being *equal*. The limit of infinitesimal domain is the "linear limit". The linearity principle applies to any continuous function, not just functions of two variables. Additionally, while it's not the topic of this post, the idea of a linear limit is fundamental to the concept of the "tangent space" which underpins some of the most important and advanced mathematical physics that exists. A huge amount of advanced math is simply understanding linearity in different dimensions and contexts.

But the main point is: The straight line is the default relationship between two variables, because all continuous relationships have a linear limit.  

The linear limit is powerful in modeling because it gives you a very good excuse to draw a straight line through a bunch of data and call it a day. But just as the linear limit gives, it also taketh away, because most linear relationships are only linear *becuase* of the linear limit. Which means that if you want to extrapolate beyond the normal range, you will probably have to consider nonlinearity. 

While it seems so basic that its hardly worth paying any attention to, the linear assumption is so fundamental and universal in physical systems, it's hard to underestimate its importance. I'm amazed by how often the linear relationship has been the correct relationship to apply in my own work. 

