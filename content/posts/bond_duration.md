---
title: "Bond Duration"
date: 2023-02-21T15:54:07-08:00
draft: true
math: true
ShowToc: true
---

Duration the measure of a bond's interest rate risk or sensitivity of a bond's full price to a change in its yield.
### Macaulay Duration
Introduced by Frederick Macaulay (1938), is the weighted average number of years until each of the bond's promised cash flow is to be paid, where the weights are the present values of each cash flow as a percentage of the bond's full value.

Macaulay Duration $D$ is defined as

$$ D = \frac{\sum_{k=1}^{n} (k/m)c_{k} / [1 + (\lambda/m)]^{k}}{\text{PV}} $$

where the bond makes payment $m$ times per year, with the payment in period $k$ being $c_{k}$, and there are $n$ periods remaining, $\lambda$ is the yield to maturity and

$$PV = \sum_{k=1}^{n} \frac{c_{k}}{[1 + (\lambda/m)]^{k}}$$

Note that the factor $k/m$ in the numerator of the formula for $D$ is time, measured in years.

#### Theorem 1
" A bond's duration is equal to its maturity if and only if it is a zero-coupon bond (pure discount issue) or a one-period coupon bearing bond."

#### Theorem 2
" The duration of a coupon-bearing bond with a finite maturity of more than one period $(1 < n < \infty)$ has a duration which is shorter than its term to maturity."

#### Theorem 3
"The duration of a perpetual bond $(n = \infty)$ is equal to $(1+ \lambda/m) / \lambda$ irrespective of its coupon rate."

Corollary: "The duration of a coupon-bearing bond approaches the limit $(1+ \lambda/m) / \lambda$ as the bond's maturity is lengthened to infinity."

#### Theorem 4
"The duration of a coupon-bearing bond selling at par or above par increases monotonically with its term to maturity and approaches $(1+ \lambda/m) / \lambda$ as the term to maturity goes to infinity."

#### Theorem 5
"The duration of a coupon-bearing bond selling below par reaches a maximum before maturity reaches infinity and then recedes toward the limit $(1+ \lambda/m) / \lambda$

#### Theorem 6
"The duration of a coupon-bearing bond selling below par reaches its maximum at a maturity directly related to the bond's coupon rate and inversely related to the market yield."

#### Theorem 7
"The longer a bond's term to maturity, the greater the difference between its term and its duration."

#### Theorem 8
"A bond's duration varies inversely with its coupon rate (except for one period and perpetual bonds)."

#### Theorem 9
"The duration of a coupon-bearing bond is inversely related to its yield to maturity."

#### Theorem 10
"The duration of a "zero-yield" bond is equal to $(1/2(n^2+n)i_{0} + 1)/(ni_{0} + 1)$ with $i_{0}$ being bond's coupon-rate."

#### Theorem 11
"A bond's duration approaches unity as the bond's yield approaches infinity."

### Modified Duration
Modified Duration is found by taking the first derivative of $P$ with respect to $\lambda$:

$$\frac{dP}{d\lambda} = \sum_{k=1}^{n}\frac{dPV_{k}}{d\lambda} = -\sum_{k=1}^{n} \frac{(k/m)PV_{k}}{1 + (\lambda/m)} = - \frac{1}{1 + \lambda/m}DP = -D_{M}P$$

Note:

Price sensitivity formula: The derivative of price $P$ with respect to yield $\lambda$ of a fixed-income security is 

$$\frac{dP}{d\lambda} = -D_{M}P$$

where $D_{M} = D/[1 + (\lambda/m)]$$ is the modified duration.

Duration of a portfolio: Suppose there are m fixed-income securities with prices and durations of $P_{i}$ and $D_{i}$, respectively, $i = 1,2,\ldots,m$, all computed at a common yield. The portfolio consisting of the agregate of these securities has price $P$ and duration $D$, given by

$$P = P_{1} + P_{2} + \ldots + P_{m}$$

$$D = w_{1}D_{1} + w_{2}D_{2} + \ldots + w_{m}D_{m}$$

where $w_{i} = P_{i} / P, i = 1,2,\ldots,m$.

### Approximate Modified Duration

Taylor series expansion of the price as a function of interest rate:

$$P(i+\Delta i) = P(i) + \frac{dP}{di}\Delta i + \frac{1}{2}\frac{d^{2}P}{di^{2}}(\Delta i)^{2} + \ldots$$

Ignoring terms involving $(\Delta i)^{2}$ and higher yields

$$-\frac{dP}{di}\frac{1}{P} \approx \frac{P(i) - P(i + \Delta i)}{(\Delta i)P(i)}$$

and

$$-\frac{dP}{di}\frac{1}{P} \approx \frac{P(i - \Delta i) - P(i)}{(\Delta i)P(i)}$$

Averaging the right side of the last two equations yields

$$D_{M}(P) \approx \frac{P(i - \Delta i) - P(i + \Delta i)}{2P(i)(\Delta i)}$$

### Effective Duration

$$D_{E} \approx \frac{V_{-} - V_{+}}{2\times V_{0} \times \Delta \text{curve}}$$

### Key Rate Duration

Introduced by Thomas Ho (1992), key rate duration (partial duration) is the sensitivity of the value of a bond or portfolio to changes in the spot rate for a specific maturity, holding other spot rates constant.

A bond or portfolio will have a key rate duration for each maturity range on the spot rate curve.

The sum of a bond's key rate durations equals its effective duration.

Key rate duration is useful for measuring the effect of a nonparallel shift in the yield curve on a bond portfolio.

### Money Duration

$$\text{money duration} = D_{M} P$$

### Convexity
Using the Taylor series expansion and ignoring terms in powers of $(\Delta i)^{3}$ and higher yields

$$P(i+\Delta i) - P(i) \approx \frac{dP}{di}\Delta i + \frac{1}{2}\frac{d^{2}P}{di^{2}}(\Delta i)^{2}$$

$$P(i-\Delta i) - P(i) \approx \frac{dP}{di}(-\Delta i) + \frac{1}{2}\frac{d^{2}P}{di^{2}}(-\Delta i)^{2}$$

which are summed to give the following approximation to

$$\frac{d^{2}P}{di^{2}}(\Delta i)^{2} \approx P(i-\Delta i) - 2P(i) + P(i+\Delta i)$$.

It follows that

$$C = \frac{d^{2}}{di^{2}}\frac{1}{P} \approx \frac{P(i-\Delta i) - 2P(i) + P(i+\Delta i)}{P(i)(\Delta i)^2}$$

### Effective Convexity

$$C_{E} \approx = \frac{V_{-} + V_{+} - 2V_{0}}{(\Delta \text{curve})^{2}V_{0}}$$

### Change in full bond price

$$\Delta P = -D_{M}(\Delta \lambda) + 1/2 C(\Delta \lambda)^{2}$$

### Reference
Hawawini, G. (2017). Bond Duration and Immunization. Routledge.

Ho, T. S. Y. (1992). Key Rate Durations. The Journal of Fixed Income, 2(2), 29–44. https://doi.org/10.3905/jfi.1992.408049
‌
Luenberger, D. G. (2014). Investment science. New York, Ny [U.A.] Oxford Univ. Press C.


‌
‌