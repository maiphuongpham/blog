---
title: "Term Structure"
date: 2023-03-17T15:54:07-08:00
draft: true
math: true
---
# One-factor short-rate models

Short-rate model, describes the future evolution of interest rates by describing the future evolution of the short rate, usually written $r_{t}$

The short rate is the (continuously compounded, annualized) interest rate at which an entity can borrow money for an infinitesimally short period of time from time $t$

Following are the one-factor models, where a single stochastic factor - the short rate - determines the future evolution of all interest rates.

$z$ represents a standard Brownian motion.

## Equilibrium Models

### Vasicek Model (1977)

$$d r_{t} = k (\theta - r_{t}) dt + \sigma dz$$

### Cox-Ingersoll-Ross (CIR) Model (1985)

$$d r_{t} = k(\theta - r_{t}) dt + \sqrt{r_{t}} \sigma dz$$

The $\sigma \sqrt{r_{t}}$ precludes the possibility of negative interest rates.

## Arbitrage-Free Models

### Ho-Lee Model (1986)

$$dr_{t} = \theta_{t} dt + \sigma dz$$

### Kalotay-Williams-Fabozzi Model (1993)

A Lognormal variant on Ho-Lee model.

$$d\ln(r) = \theta_{t} dt + \sigma dz$$
