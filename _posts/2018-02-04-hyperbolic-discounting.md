---
layout: post
title: Hyperbolic discounting — The irrational behavior that might be rational after all
description: 
---

<p></p>
When I was in grad school I occasionally overheard people talk about how humans do something called "hyperbolic discounting". Apparently, hyperbolic discounting was considered irrational under standard economic theory. 

I recently decided to learn what hyperbolic discounting was all about, so I set out to write this blog post. I have to admit that hyperbolic discounting has been pretty hard for me to understand, but I think I now finally have a good enough handle on it to write about it. Along the way, I learned something interesting: Hyperbolic discounting might be rational after all.

## Rational and irrational discounting
If I offered you <span class="tex2jax_ignore">$</span>50 now or <span class="tex2jax_ignore">$</span>100 in 6 months, which would you pick? It’s not crazy to choose the <span class="tex2jax_ignore">$</span>50 now. One reason is that it's a safer bet. If you had chosen the delayed <span class="tex2jax_ignore">$</span>100, there’s a risk that I might forget about the deal when the time came to pay _[personal note: I wouldn't]_, and you would never get your money. Another reason is that if you invest the $50 now, you might be able to make up some of the remainder in interest.

Valuing immediate money more than future money is a rational behavior known as discounting. Everybody has their own discount factor. Some people might value money in 6 months at, say, 75% of what they’d value it today. Others might value it at 90%. 

In the early 1980s, psychologist George Ainslie discovered something peculiar. He [found](https://en.wikipedia.org/wiki/Hyperbolic_discounting#Observations) that while a lot of people would prefer <span class="tex2jax_ignore">$</span>50 immediately rather than <span class="tex2jax_ignore">$</span>100 in 6 months, they would _not_ prefer <span class="tex2jax_ignore">$</span>50 in 3 months rather than <span class="tex2jax_ignore">$</span>100 in 9 months. These two different scenarios are shown in the diagram below, where the green checks indicate the options that people tended to choose.

<div class="wrapper">
  <img src='/assets/2018_hyperbolic_discounting/timeline_diagram.png' class="inner" style="position:relative border: #222 2px solid; max-width:100%;" >
</div> 

If you think about it, there’s something inconsistent about this behavior. The two scenarios are actually identical, just shifted by 3 months, and yet the same people behave differently depending on when the scenario would be presented. If we waited 3 months and then asked them again if they would prefer <span class="tex2jax_ignore">$</span>50 immediately or <span class="tex2jax_ignore">$</span>100 in 6 months, their original response to Scenario 1 implies they would prefer the fast money (i.e. they would have a high discount rate), but their original response to Scenario 2 implies they would prefer the delayed money (i.e. they would have a low discount rate). In other words, their present self today would make a decision in Scenario 2 that three months from now they will have regretted making. This behavior is _time-inconsistent_ and is therefore considered irrational according to standard economic theory.

The usual way to achieve rational time-consistent discounting is with an exponential discount curve, where the value of receiving something at future time $$ t $$ is a fixed fraction $$ s(t) $$ of its present value, and where $$ \lambda $$ is the constant discount rate.

$$ s(t) = e^{-\lambda t} $$

With an exponential curve, a dollar delayed by six months is always worth the same fixed fraction of a dollar at the baseline date, no matter what the baseline date it is. If you are indifferent between <span class="tex2jax_ignore">$</span>100 now and <span class="tex2jax_ignore">$</span>50 in 6 months, you should also be indifferent between <span class="tex2jax_ignore">$</span>100 in 3 months and <span class="tex2jax_ignore">$</span>50 in 9 months. The discount rate is constant.

<div class="wrapper">
  <img src='/assets/2018_hyperbolic_discounting/fig_exp_fracs.png' class="inner" style="position:relative border: #222 2px solid; max-width:100%;" >
</div> 


In contrast to an exponential curve, humans tend to show a [hyperbolic discount curve](https://en.wikipedia.org/wiki/Hyperbolic_discounting), which is considered irrational according to standard economic theory. Confusingly, the hyperbolic discount curve is not defined by one of the [hyperbolic functions](https://en.wikipedia.org/wiki/Hyperbolic_function) you may remember from high school. Instead, it is defined as follows, where $ \tau $ is the relative time from now:

$$ s(\tau) = \frac{1}{1+k \tau} $$


Whereas an exponential curve has a constant discount rate, a hyperbolic discount curve has a higher discount rate in the near future and lower discount rate in the distant future. That's why the participants in Ainslie's experiment cared more about the delay from 0 to 6 months than about the same delay from 3 to 9 months.

<div class="wrapper">
  <img src='/assets/2018_hyperbolic_discounting/fig_exp_and_hyp.png' class="inner" style="position:relative border: #222 2px solid; max-width:100%;" >
</div> 

The apparent rationality of an exponential function is often presented either with a hazard rate interpretation or an interest rate interpretation. It turns out, however, that both of these interpretations make implausible assumptions about the world. The rest of this blog post describes how if we make some more plausible assumptions, hyperbolic discount function becomes rational.


## Hazard Rate interpretation

According to the hazard-based interpretation of discounting, you should prefer immediate money to future money because there is a risk that the future money will never be delivered. This interpretation is more common in the animal behavior literature. ([Pigeons](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC2648524/), [rats](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC2648524/), and [monkeys](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3107575/) all show hyperbolic discounting.)

##### Apparent rationality of exponential discounting

Imagine that there could be an event at some time that could cause you to no longer receive your reward. Perhaps the person who owes you the money could die or lose their assets. Assuming a constant hazard rate (i.e. assuming the event is equally likely to happen at any time), the probability that the event has not happened by time $ \tau $ is:

$$ s(\tau) = e^{-\lambda \tau} $$

The $$ s(\tau) $$ function is called a "survival" function because it describes the probability that the deal is still "alive" by time $$ \tau $$. The $$ \lambda $$ parameter is the constant hazard rate.

<div class="wrapper">
  <img src='/assets/2018_hyperbolic_discounting/fig_exp_survival.png' class="inner" style="position:relative border: #222 2px solid; max-width:100%;" >
</div> 

A key insight here is that the survival function can also be interpreted as a discount function. If someone says you can receive your reward at time $ \tau $ if you're willing to wait for it, and if there's only a 60% chance you'll actually receive it, you should value that offer at 60% of the current value of the reward. Since the survival function is exponential, and since the survival function _is_ the discount function, your discount function is also exponential, at least according to standard economic theory.

##### Rationality of hyperbolic discounting

The problem with assuming an exponential survival function is that it assumes you know the hazard rate $ \lambda $. In most situations, you don't know exactly what the hazard rate is. Instead you have uncertainty around the parameter. [Souza (2015)](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC1689473/pdf/T9KA20YDP8PB1QP4_265_2015.pdf) proposes an exponential prior distribution over the hazard rate.

$$ p(\lambda) = \frac{1}{k} e^{-\frac{\lambda}{k}} $$

The exponential prior is shown in the graph below. Although this curve looks like a discount function, it is not. It is a distribution over a parameter.

<div class="wrapper">
  <img src='/assets/2018_hyperbolic_discounting/fig_hazard_prior.png' class="inner" style="position:relative border: #222 2px solid; max-width:100%;" >
</div> 

According to Souza, if you average over all the possible exponential survival functions generated by this prior, you get a hyperbolic survival function, or equivalently, a hyperbolic discount function. I'll try my best to explain:

##### Explanation
In the plot below, I've drawn 30 exponential survival functions in blue, each with a $$ \lambda $$ sampled from the $$ p(\lambda) $$ prior distribution defined above. The pink curve is the mean of all of them. Notice that whereas the individual survival curves are all exponential, their mean is hyperbolic, with a distant future characterized by a flat slope and relatively high survival values. 

<div class="wrapper">
  <img src='/assets/2018_hyperbolic_discounting/fig_mean_of_exponentials.png' class="inner" style="position:relative border: #222 2px solid; max-width:100%;" >
</div> 

Why do we get a hyperbolic function when we average many exponential functions? To understand why, you first need to know that the instantaneous discount rate of a discount function is the negative of its instantaneous slope divided by its height. This sounds like a mouthful but it actually makes sense if you think about it. At any point in time, the discount rate is the drop in value over one time unit (i.e. the slope), divided by the principal (i.e. the height). 

With that in mind, let's think about time points in the distant future, when almost all of the exponential curves have gone to zero except for the curve with the lowest discount rate. When averaging across these curves in the distant future, the many curves at zero effectively scale down the one remaining curve by the same factor across a broad range of dates. In the figure below, the averaging operation scales down the curve by 86% at two different dates separated by 15 months. When you scale down a curve by a constant factor across a broad range, you scale its height and its slope by the same factor, thus preserving the slope to height ratio (i.e. the discount rate). Therefore, when you average over possible discount functions in the distant future, your resulting discount function is [dominated](https://eml.berkeley.edu//~saez/course131/weitzman98.pdf) by the discount rate of the curve with the lowest discount rate.

<div class="wrapper">
  <img src='/assets/2018_hyperbolic_discounting/fig_mean_of_exponentials_arrows.png' class="inner" style="position:relative border: #222 2px solid; max-width:100%;" >
</div> 

As a consequence, the further you look into the future, the lower your discount rate. This is exactly what hyperbolic discounting is and exactly what humans do. For the choice between <span class="tex2jax_ignore">$</span>50 now and <span class="tex2jax_ignore">$</span>100 in 6 months, we apply a heavy discount rate. For the choice between <span class="tex2jax_ignore">$</span>50 in 3 months and <span class="tex2jax_ignore">$</span>100 in 9 months, we apply a lighter discount rate.

For a more qualitative intuition, you can think of it this way: When you make a deal with someone, you don't know what the hazard rate is going to be. But if the deal is still alive after 80 months, then your hazard rate is probably favorable and thus the deal is likely to still be alive after 100 months. You can therefore have a light discount rate between 80 months and 100 months.


## Interest Rate interpretation

A common justification for discounting is the fact that interest rates exist. A dollar now is worth more than a dollar in a year, because if you take the dollar now and invest it, it will worth more in a year.

##### Apparent rationality of exponential discounting
If the interest rate is 5%, you should be indifferent between <span class="tex2jax_ignore">$</span>100 today and <span class="tex2jax_ignore">$</span>105 in a year, since you could just invest the <span class="tex2jax_ignore">$</span>100 today and get the same amount in a year. If the interest rate is constant, the value of the dollar will rise exponentially, according to $ v(\tau) = e^{0.05\tau} $, where $ v $ is the value. To rationally maintain indifference between a dollar and its equivalent value in the future after investment, your discount function should decay exponentially, according to $ s(\tau) = e^{-0.05\tau} $.

##### Rationality of hyperbolic discounting
The problem with this story is that it only works if you assume that the interest rate is constant. In the real world, the interest rate fluctuates. 

Before taking on the fluctuating interest rate scenario, let's first take on a different assumption that is still somewhat simplified. Let's assume that the interest rate is constant but we don't know what it is, just as we didn't know what the hazard rate was in the previous interpretation. With this assumption, the justification for hyperbolic discounting becomes similar to the explanation in the blue and pink plots above. When you do a probability-weighted average over these decaying exponential curves, you get a hyperbolic function.

The previous paragraph assumed that the interest rate was constant but unknown. In the real world, the interest rate is known but fluctuates over time. [Farmer and Geanakoplos (2009)](https://campuspress.yale.edu/johngeanakoplos/files/2017/07/Hyperbolic-Discounting-is-Rational-Valuing-the-Far-Future-with-Uncertain-Discount-Rates-1uc47ft.pdf) showed that if you assume that interest rate fluctuations follow a [geometric random walk](http://sfb649.wiwi.hu-berlin.de/fedc_homepage/xplore/tutorials/sfehtmlnode21.html), hyperbolic discounting becomes optimal, at least asymptotically as $$ \tau \rightarrow \infty $$. In the near future, you know the interest rate with reasonable certainty and should therefore discount with an exponential curve. But as you look further into the future, your uncertainty about the interest rate increases and you should therefore discount with a hyperbolic curve.

Is the geometric random walk a process that was cherry picked by the authors to produce this outcome? Not really. [Newell and Pizer (2003)](https://dukespace.lib.duke.edu/dspace/bitstream/handle/10161/7542/NewellPizerDiscountingPew.pdf?sequence=1) studied US bond rates in the 19th and 20th century and found that the geometric random walk provided a better fit than any of the other interest rate models tested.

## Summary
When interpreting discounting as a survival function, a hyperbolic discounting function is rational if you introduce uncertainty into the hazard parameter via an exponential prior ([Souza, 2015](https://campuspress.yale.edu/johngeanakoplos/files/2017/07/Hyperbolic-Discounting-is-Rational-Valuing-the-Far-Future-with-Uncertain-Discount-Rates-1uc47ft.pdf)). When interpreting the discount rate as an interest rate, a hyperbolic discounting function is asymptotically rational if you introduce uncertainty in the interest rate via a geometric random walk ([Farmer and Geanakoplos, 2009](https://campuspress.yale.edu/johngeanakoplos/files/2017/07/Hyperbolic-Discounting-is-Rational-Valuing-the-Far-Future-with-Uncertain-Discount-Rates-1uc47ft.pdf)). 
