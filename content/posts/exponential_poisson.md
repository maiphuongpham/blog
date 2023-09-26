---
title: "The Exponential Distribution and the Poisson Process"
date: 2023-04-19T15:54:07-08:00
draft: true
math: true
---
# The Exponential Distribution and the Poisson Process
1. The time $T$ required to repair a machine is an exponentially distributed random variable with mean $\frac{1}{2}$ (hours).
(a) What is the probability that a repair time exceeds $\frac{1}{2}$ hour?
(b) What is the probability that a repair takes at least $12\frac{1}{2} hours given that its duration exceeds 12 hours?

{{< detail-tag "See answer" >}}
(a) Since $T \sim \text{Exp} (2)$, we have $P(T > \frac{1}{2}) = e^{-2{1}{2}} = e^{-1}$

(b) Using the memoryless property of the exponential distribution yields:
$P(T > 12\frac{1}{2} | T > 12) = P(T > \frac{1}{2}) = e^{-1}$
{{< /detail-tag >}}

2. Suppose that you arrive at a single-teller bank to find five other customers in the bank, one being served and the other four waiting in line. You join the end of the line. If the service times are all exponential with rate $\mu$, what is the expected amount of time you will spend in the bank?

