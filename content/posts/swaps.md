---
title: "Swaps"
date: 2023-03-17T15:54:07-08:00
draft: false
math: true
---

# Interest rate swaps

## "Vanilla" fixed for floating
To determine any interest rate swap, a number of parameters must be specified for each leg (series of payments)

- the notional principal amount
- start and end dates, value-date, trade-date,  settlement dates, date scheduling (rolling)
- fixed rate (i.e. swap rate), sometimes swap spread
- floated interest rate index tenor
- day count conventions for interest calculations

Receive floating

$$P_{IRS} = \frac{NA (\text{floating rate} - \text{fixed rate})(days / 360)}{1 + \text{floating rate}(days / 360)}$$

Receive fixed

$$P_{IRS} = \frac{NA (\text{fixed rate} - \text{floating rate})(days / 360)}{1 + \text{floating rate}(days / 360)}$$

Libor is annual rate, when calculated, we must include accrual period adjustment and convention changes.

$$r_{\text{fixed}} = \frac{1 - \text{DF}_{n}}{\sum \text{DF}}$$

Valuation

$$V_{swap} = (r_{\text{fixed}_0} - r_{\text{fixed_{t}}\sum\text{DF} \times NA$$

## Basis swap
# Currency swaps

$$V_{swap} = V_{D} - S_{t} V_{F} = NA(r_{fx_d} \sum DF + DF_{n}) - S_{t}NA(r_{fx_f} \sum DF + DF_{n})$$

where $S_{t} = d/f$

or 

$$V_{swap} = S_{t} V_{D} - V_{F} = S_{t}NA(r_{fx_d} \sum DF + DF_{n}) - NA(r_{fx_f} \sum DF + DF_{n})$$

where $S_{t} = f/d$

# Inflation swaps
# Commodity swaps
# Credit default swaps
# Equity swaps
# Swaption