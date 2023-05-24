---
title: "Black-Scholes-Merton Model"
date: 2023-03-15T15:54:07-08:00
draft: false
math: true
TocOpen: true
---

#### Black and Scholes assumed:
1. A continuously-compounded interest rate of $r$.
2. Geometric Brownian motion dynamics for the stock price, $S_{t}$, so that
$$S_{t} = S_{0} e^{(\mu - \sigma^{2}/2)t + \sigma W_{t}}$$
where $W_{t}$ is a standard Brownian motion.
3. The stock pays a dividend yield of $c$.
4. Continuous trading with no transactions costs and short-selling allowed.

#### Black-Scholes formula:
$$C_{0} = S_{0} e^{-cT}N(d_{1}) - K e^{-rT}N(d_{2})$$
where
$$d_{1} = \frac{\ln(S_{0}/K) + (r - c + \sigma^{2}/2)T}{\sigma \sqrt{T}}$$
$$d_{2} = d_{1} - \sigma \sqrt{T}$$

and $N(d) = P(N(0,1) \le d)$

##### Deriving $N(d_1)$

(N/A)

hint: Ross. S.M., Introduction to Probability Models, 12th ed., 655-658.

### The "Greeks"

The "Greeks" refer to the partial derivatives of a derivative security price with respect to model parameters.

#### Delta

The delta of a European call option satisfies
$$\text{delta} = \frac{dC}{dS} = e^{-cT} N(d_{1}) \in [0,1]$$

The delta of a European put option satisfies
$$\text{delta}= \frac{dP}{dS} = -e^{-cT} N(-d_{1}) = e^{-cT} (N(d_{1}) - 1) \in [-1,0]$$

#### Gamma

The gamma of a European option satisfies

$$\text{gamma} = \frac{d^{2}C}{dS^{2}} = e^{-cT}\frac{\phi(d_{1})}{\sigma S \sqrt{T}} \in [0,\infty]$$

where $\phi(\cdot)$ is the standard normal PDF.

#### Vega

The vega of a European option satisfies

$$\text{vega} = \frac{dC}{d\sigma} = e^{-cT} S \sqrt{T} \phi (d_{1})$$

where $\phi(\cdot)$ is the standard normal PDF.

#### Theta

The theta of a European call option satisfies

$$\text{theta} = -\frac{dC}{dT} = -e^{-cT} S \phi (d_{1}) \frac{\sigma}{2 \sqrt{T}} + ce^{-cT} S N(d_{1}) - rKe^{-rT}N(d_{2})$$

The theta of a European put option satisfies

$$\text{theta} = -\frac{dP}{dT} = -e^{-cT} S \phi (d_{1}) \frac{\sigma}{2 \sqrt{T}} - ce^{-cT} S N(-d_{1}) + rKe^{-rT}N(-d_{2})$$

where $\phi(\dot)$ is the standard normal PDF.

#### Rho

The rho of a European call option satisfies

$$KTe^{-rT}N(d_{2})$$

The rho of a European put option satisfies

$$-KTe^{-rT}N(-d_{2})$$

### The Black Model

$$c = e^{-rT}[FN(d_{1}) - K N(d_{2})]$$

$$p = e^{-rT}[FN(-d_{1}) - K N(-d_{2})]$$

which states the price for a European option of maturity $T$ on a futures contract with strike price $K$ and delivery date $T'$ (with $T' > T$)

{{<detail-tag "Why?">}}
#### Margrabe's formula
{{ <detail-tag>}}

