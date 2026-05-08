---
title: 'Exponentials'
date: 2026-05-08
permalink: /posts/2026/05/Exponentials/
tags:
  - heuristics
---

Sometimes when someone wants to express that one thing is significantly larger than another, they'll say that it's "exponentially" larger. Or, if something is growing over time at an increasing rate, someone might say that its "exponential". These are usually not intended as precise uses of the word "exponential". But I'm not pointing that out to be pedantic, instead I want to talk about *why* it's not a precise use of the word "exponential". And why, when you think about it, it's not clear why you'd use the word "exponential" in the first place.

If I said that Beijing was exponentially larger than my hometown of 20,000 people, I might connect it to exponentials by saying that the size of my town has a population on the order of $$10^4$$, but that Beijing has a population on the order of $$10^7$$. Since Beijing was so much bigger than my hometown, the best way to compare their sizes is by using exponentials. Since the exponent for the population of Beijing is larger than for my hometown, that makes it exponentially larger. But "exponentially" isn't really the right word for that, "power" or "order of magnitude" make a lot more sense. So why would people say exponential? 

There's this old story about a peasant who does some remarkable feat - let's say he saves the princess. The king is extremely impressed and wants to reward him handsomly. The peasant refuses gold and jewels, instead telling the king that he wants him to place a single piece of grain on the corner square of a chess board and to give him the grain. The next day, he wants the king to place two grains on the second square and give him the grain. On the third day, four grains on the third square, doubling each day until all 64 squares of the chess board are full. In the story, the king thinks this sounds like nothing, so he laughs it off and agrees. The fact is, that even if he wanted to, the king couldn't pay out the amount of grain needed to satisfy the deal. If he tried to, by the time he got to the 40th square (if he were paying in corn) he'd be paying out the total annual corn production for the entire United States - presumably much more than his kingdom could produce. By the time they reached the end of the board he would need to pay out $$2^64$$ grains, or around $$10^19$$, which (if he were paying in rice) would be the entire current global rice production for three and a half centuries.

Most people will tell you that this story is about how fast the exponential function grows, because the amount of grain on each square follows the (base 2) exponential function,

$$y = 2^x$$

where y is the amount of rice on the square and x is the square on the chess board. The exponential function *definitely* grows fast, but I would argue that this story is really about something else. This story is about the fact that people don't understand how fast the exponential function grows. It just doesn't seem like the grain should grow to that scale. 

So maybe that's why we call big things "exponential" - after all, the exponential function grows *really* fast, so it kindof makes sense. The problem with that explanation is that the exponential function isn't the only function that grows way faster than we think it should. In fact, we tend to be caught flat footed by anything that isn't linear. For instance, if you wrapped a 1 cm diameter tube around the earth and filled it with water, it would require about the same amount of water to fill as an olympic sized swimming pool.

That seems *super* wrong, but that's just the cubic function. The cubic function grows *way* slower than the exponential function and it still breaks our intuition.

If we have poor intuition for all non-linear functions, why would we use the word exponential so much? Why not quadratic? Far more people get exposed to quadratics in their schooling than to exponentials. 

I think the reason is that, in the real world, most things change exponentially. Even if you only used exponential to describe things that actually behaved exponentially, you'd be using it... a lot - population change, the stock market, disease spread, radioactive decay etc. Its pretty easy to imagine that when so many things are exponential, people would say something behaved "exponentially" whenever it kindof felt right. So, if the exponential function is so common that we just started to refer to anything and everything as exponential, the next reasonable question is, why is it so common? 

That's what I'm going to address here.

The current state of a system tends to describe how it will change over time, and the amount of information needed to fully describe the state of the system is the number of degrees of freedom the system has. If I have a pendulum, I need to know the position and the velocity of the pendulum in order to predict its motion in the future, so that system has 2 degrees of freedom. The population of birds in an ecosystem might depend on thousands of different variables, like the population of predators, and available food. That system would have thousands of degrees of freedom. 

The simplest and most useful example to start with is the system with only 1 degree of freedom. Radioactive decay of one element into another would be an example of a 1-degree of freedom system. For this system, knowing a single variable 'y' can tell us the future state of the system. Since knowing 'y' now describes what it will be in the future, then the change in 'y' over time must be a function of 'y',

$$dy/dt = f(y)$$

where $$f(y)$$ is some arbitrary function of 'y' and $$dy/dt$$ is the rate of change in 'y'. This equation tells us that the rate of change of 'y' with time depends on 'y'. Consider the linear limit of 'f',

$$dy/dt = a+by$$

where a and b are constants. If we solve this equation, we get,

$$y = A e^(bt)-a/b$$

where A is an integration constant. This is an exponential curve! This short derivation shows that exponential behavior corresponds to linear 1-degree of freedom systems. 

When considering the exponential equation as a model for a given physical system, there are two heuristics at play. First, you make the heuristic assumption that the problem is in the linear limit - meaning that you understand exponential behavior is temporary. If 'y' gets big enough, it will probably level off. Second, for most systems, you make the assumption that it is approximately a 1 degree of freedom system. One single number describes all the most important aspects of the system. 

The exponential model is common enough that just this heuristic understanding of it is really useful. If I want to model time-series data, an exponential curve will always be my first guess at how it behaves. But more interesting to me is what the ubiquity of the exponential function in nature tells us. Strictly speaking, few systems are 1-degree of freedom systems. However, the prevalence of exponential behavior tells us that there are many systems which behave approximately like 1 degree of freedom systems. We already knew that the linear limit was a strong heuristic, but the prevalence of exponential behavior suggests that even complex and messy systems often behave like they have only 1 degree of freedom. Why does that occur? Is it possible to use the underlying principles that cause this reduction in complexity to understand less obvious behavior? 

One of the purposes of this blog will be to explore these questions more. Next post, I'm going to examine in more detail how higher degree of freedom systems work, and what oscillatory, or even more complex behavior can tell us.