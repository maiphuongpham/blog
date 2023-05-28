---
title: "CFA Level II Cheatsheet: Quantitative Methods"
date: 2023-05-23T15:54:07-08:00
draft: false
math: true
ShowToc: true
ShowRef: true
tags: [cfa]
---
### Multiple Regression
#### Coefficient of Determination, $R^2$
$$R^2 = 1 - \frac{SSE}{SST} = \frac{RSS}{SST}$$
$$MSE = \frac{SSE}{n-k-1}, MSR = \frac{RSS}{k}$$
#### Adjusted $R^2$
$$R^2_a = 1 - \left[ \frac{n-1}{n-k-1}(1-R^2) \right]$$
#### Akaike's information criterion (AIC):
$$AIC = n\ln\left(\frac{SSE}{n}\right) + 2(k+1)$$
#### Schwarz's Bayesian information criteria (BIC):
$$BIC = n\ln\left(\frac{SSE}{n}\right) + \ln(n)(k+1)$$
#### F-statistic to evaluate nested models:
$$F = \frac{(SSE_R - SSE_U)/q}{SSE_U/(n-k-1)}$$
*with $q$ and $(n-k-1)$ degrees of freedom.*
#### F-test statistic to evaluate overal model fit:
$$F = \frac{RSS_U/k}{SSE_U/(n-k-1)}$$
#### Variance inflation factor (VIF)
to quantify multicollinearity:
$$VIF_j = \frac{1}{1-R_j^2}$$
#### Cook's distance (D_i)
detects influential data points:
$$D_i = \frac{e_i^2}{k\times MSE}\left[\frac{h_{ii}}{(1-h_{ii})^2}\right]$$
#### Logistic regression (logit) models:
$$\ln\left(\frac{p}{1-p}\right) = b_0 + b_1X_1 + b_2X_2 + \ldots + \epsilon$$
$$odds = e^{\hat{y}}$$
$$P = odds/(1+odds) = 1/(1+e^{-\hat{y}})$$
#### Likelihood ratio (LR) test
for logistic regressions:
$$LR = -2(\ln(L_R) - \ln(L_U)$$

### Time-Series Analysis
#### Linear trend model
$$y_t = b_0 + b_1t + \epsilon_t$$
#### Log-linear trend model
$$\ln(y_t) = b_0 + b_1t + \epsilon_t$$
#### Mean-reverting level for AR(1)
$$\frac{b_0}{1-b_1}$$
#### Random Walk Time Series
$$x_t = x_{t-1} + \epsilon_t$$
#### ARCH
Detected by estimating:
$$\hat{\epsilon}_t^2 = a_0 + a_1\hat{\epsilon}_{t-1}^2 + \mu_t$$
#### Variance of ARCH series
$$\hat{\sigma}^2_{t+1} = \hat{a}_0 + \hat{a}_1 \hat{\epsilon}^2_t$$

### Big Data Projects
#### Preparing data
$$normalized X_i = \frac{X_i - X_{min}}{X_{max} - X_{min}}$$
$$standardized X_i = \frac{X_i - \mu}{\sigma}$$
#### Fit of a Machine Learning Algorithm
$$precision(P) = \frac{TP}{FP+TP}$$
$$recall(R) = \frac{TP}{TP + FN}$$
$$accuracy = \frac{TP + TN}{TP+TN+FP+FN}$$
$$F1 = \frac{2PR}{P+R}$$
$$RMSE = \sqrt\frac{\sum_{i=1}^n (\hat{y}_i - y_i)^2}{n}$$
