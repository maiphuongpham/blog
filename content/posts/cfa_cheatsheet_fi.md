---
title: "CFA Level II Cheatsheet: Fixed Income"
date: 2023-05-25T15:54:07-08:00
draft: false
math: true
ShowToc: true
ShowRef: true
tags: [cfa]
---
### Term Structure of Interest Rates
#### Forward pricing model
$$F_{(a,b)} = DF_{a+b} / DF_{a}$$
#### Forward rate model
$$(1+f(a,b))^k = \frac{(1+S_b)^b}{(1+S_a)^a}$$
#### Swap spread
$$\text{swap spread}_t = \text{swap rate}+t - \text{treasury yield}_t$$
#### TED spread
$$\text{TED spread} = \text{3-month MRR rate} - \text{3-month T-bill rate}$$
#### MRR-OIS spread
$$\text{MSS-OIS spread} = \text{MRR rate} - \text{overnight indexed swap rate}$$
#### Managing yield curve shape risk
$$\Delta P/P \approx -D_L\Delta x_L - D_S\Delta x_S - D_C\Delta x_C$$

### Bonds with Embedded Options
#### Effective Duration
$$EffDur = \frac{P_{-} - P_{+}}{2\Delta y P_0}$$
#### Effective Convexity
$$EffCon = \frac{P_{-} + P_{+} - 2P_0}{P_0\Delta y^2}$$