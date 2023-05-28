---
title: "CFA Level II Cheatsheet: Equity Valuations"
date: 2023-05-25T15:54:07-08:00
draft: false
math: true
ShowToc: true
ShowRef: true
tags: [cfa]
---
### Discounted Dividend Valuation
#### Gordon Growth Model (GGM)
$$V_0 = \frac{D_0(1+g)}{r-g} = \frac{D_1}{r-g}$$
#### Present Value of Growth Opportunities
$$V_0 = \frac{E_1}{r} + PVGO$$
#### H-Model
$$V = \frac{D_0(1+g_L)}{r-g_L} + \frac{D_0H(g_s - g_L)}{r - g_L}$$
**Sustainable Growth Rate:** $b \times ROE$
#### Required return from Gordon Growth Model
$$r = \frac{D_1}{P_0} + g$$

### Free Cash Flow Valuation
#### Free Cash Flow to Firm (FCFF)
$$\text{FCFF = NI + Dep + Int(1-t) - FCInv - WCInv}$$
$$\text{FCFF = EBIT(1-t) + Dep - FCInv - WCInv}$$
$$\text{FCFF = EBITDA(1-t) + tDep - FCInv - WCInv}$$
$$FCFF = CFO + Int(1-t) - FCInv$$
#### Free Cash Flow to Equity (FCFE)
$$\text{FCFE = FCFF - Int(1-t) + Ney borrowing}$$
#### Single-Stage FCFF/FCFE Models
$$V_0 = \frac{FCFF_1}{WACC - g}$$
$$V_0 = \frac{FCFE_1}{r - g}$$

### Price and EV Multiples
#### Justified P/E
$$\text{justified leading P/E} = \frac{P_0}{E_1} = \frac{1-b}{r-g}$$
$$\text{justified trailing P/E} = \frac{P_0}{E_0} = \frac{(1-b)(1+g)}{r-g}$$
#### Justified Dividend Yield
$$\frac{D_0}{P_0} = \frac{r-g}{1+g}$$
#### PEG ratio
$$PEG ratio = \frac{P/E}{g}$$
#### Justified P/B
$$\text{justified P/B} = \frac{ROE-g}{r-g}$$
#### Justified P/S
$$\text{justified P/S} = \frac{PM_0(1-b)(1+g)}{r-g}$$

### Residual Income Valuation
#### Residual Income Models
$$RI = E_t - rB_{t-1} = (ROE - r)B_{t-1}$$
#### Single-stage RI model
$$V_0 = B_0 + \frac{(ROE-r)B_0}{r-g}$$
#### Multistage RI valuation
$$V_0 = B_0 + \sum_{t=1}^{T-1} \frac{E_t - rB_{t-1}}{(1+r)^t} + \frac{E_T - rB_{T-1}}{(1+r-\omega)(1+r)^{T-1}}$$

#### Economic Value Added®
$$EVA = NOPAT - $WACC = EBIT(1-t) - WACC\times TC$$

### Private Company Valuation
#### Discount for Lack of Control
$$DLOC = 1 - \frac{1}{1+CP}$$
$$\text{Total discount} = 1 - (1-DLOC)(1-DLOM)$$