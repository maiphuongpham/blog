---
title: "Linear Regression"
date: 2023-03-17T15:54:07-08:00
draft: false
math: true
---

### Assumptions
1. Linearity
2. Homoskedasticity
3. Independence of errors
4. Normality
5. Independence of IVs

### Evaluating Model Fit

#### $R^{2}$

$$R^{2} = \frac{SSR}{SST} = \frac{\sum (\hat{Y}_{i} - \bar{Y})^{2}}{\frac{\sum (Y_{i} - \bar{Y})^{2}}$$

#### Adjusted $R^{2}$

Proposed by Mordecai Ezekiel, the adjusted $R^{2}$ is defined as

$$\bar{R}^{2} = 1 - \frac{SSE/ (n-k-1)}{SST/(n-1)} = 1 - \left[ \left( \frac{n-1}{n-k-1} \right) (1 - R^{2}) right]$$

For $k \ge 1, \bar{R}^{2} < R^{2}$
if coefficient's $|t - \text{stat}| > 1, \bar{R}^{2} \uparrow, \text{else} \bar{R}^{2} \downarrow$

#### AIC and BIC

AIC - Akaike's Information Criterion

$$AIC = n\ln(SSE/n) + 2(k+1)$$

Better for prediction purposes

$$BIC = n\ln(SSE/n) + \ln(n)(k+1)$$

Better when "goodness of fit" is preferred

#### Hypothesis Testing
Testing single coeffient

t-stat vs critical value

Testing joint coefficients

$$F-stat = \frac{(SSE_{\text{restricted}} - SSE_{\text{unrestricted}})/q}{SE_{\text{unrestricted}} / (n-k-1)}$$

with $q$ being the number of restrictions

Testing unrestricted model
$$F-stat = \frac{\text{Explained variance}}{\text{Unexplained variance}} = \frac{MSR}{SSR} = \frac{SSR/k}{SSE/(n-k-1)}$$

### Model Mispecification

#### Failures in regression functional form
1. Omitted variables
2. Inappropriate form of variables
3. Inappropriate scaling
4. Inappropriate pooling of data

#### Heteroskedastic
Non-constant $Var(\epsilon)$ across observations

1. Unconditional heteroskedasticity: no issues for inference
2. Conditional heteroskedasticity: SE underestimated, t-stats inflated, F-test unreliable.

Test: BP (Breusch Pagan) $\chi_{k}^{2} = n R_{e}^{2}$ with $R_{e}^{2}$ from the regression ($e, VIs$)

Correct: Compute robust SEs (White-corrected SEs)

#### Serial Correlation (autocorrelation)
