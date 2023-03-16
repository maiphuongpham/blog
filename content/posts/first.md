---
title: "Black-Scholes-Merton Model"
date: 2023-03-15T15:54:07-08:00
draft: false
math: true
---

### Black-Scholes call option formula

Consider a European call option with strike price $K$ and expiration time $T$. If the underlying stock pays no dividends during the time $[0,T]$ and if interest is constant and continuously compounded at a rate $r$, the Black-Scholes solution is $f(S,t) = C(S,t)$, defined by

$$C(S,t) = SN(d_{1}) - K e^{-r(T-t)}N(d_{2})$$

where

$$d_{1} = \frac{\ln(S/K) + (r + \sigma^{2}/2)(T-t)}{\sigma \sqrt(T-t)}$$

$$d_{2} = \frac{\ln(S/K) + (r - \sigma^{2}/2)(T-t)}{\sigma \sqrt(T-t)} = d_{1} - \sigma \sqrt(T-t)$$

and where $N(x)$ denotes the standard cummulative normal probability distribution.

Special cases: Suppose $t = T$ (the option is at expiration), then

$$d_{1} = d_{2} = 
\begin{cases}
+\infty \text{if} S > K\n
-\infty \text{if} S < K$$