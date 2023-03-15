---
title: "Duration"
date: 2023-02-21T15:54:07-08:00
draft: false
math: true
---

## Duration
Duration the measure of a bond's interest rate risk or sensitivity of a bond's full price to a change in its yield.
### Macaulay Duration
Introduced by Frederick Macaulay, is the weighted average number of years until each of the bond's promised cash flow is to be paid, where the weights are the present values of each cash flow as a percentage of the bond's full value.

In particular, Macaulay Duration $D$ is defined as

$$ D = \frac{\sum_{k=1}^{n} (k/m)c_{k} / [1 + (\lambda/m)]^{k}}{\text{PV}} $$

where the bond makes payment $m$ times per year, with the payment in period $k$ being $c_{k}$, and there are $n$ periods remaining, $\lambda$ is the yield to maturity and

$$PV = \sum_{k=1}^{n} \ frac{c_{k}}{[1 + (\lambda/m)]^{k}}$$

Note that the factor $k/m$ in the numerator of the formula for $D$ is time, measured in years.

#### Proof as $n \to \infty$, D is finite:

$$D = \frac{R}{R-1} - \frac{QR + n(1 + Q - QR)}{R^{n} - 1 - Q + QR}$$

### Modified Duration
### Effective Duration
### Key Rate Duration
### Convexity
