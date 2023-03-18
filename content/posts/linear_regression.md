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
4. Normality (of regression residuals)
5. Independence of IVs

### Evaluating Model Fit

#### $R^{2}$

$$R^{2} = \frac{SSR}{SST} = \frac{ \sum(\hat{Y}_{i} - \bar{Y})^{2} }{ \sum(Y_{i} - \bar{Y})^{2} }$$

#### Adjusted $R^{2}$

Proposed by Mordecai Ezekiel, the adjusted $R^{2}$ is defined as

$$\bar{R}^{2} = 1 - \frac{SSE/ (n-k-1)}{SST/(n-1)} = 1 - \left[ \left( \frac{n-1}{n-k-1} \right) (1 - R^{2}) \right]$$

For $k \ge 1, \bar{R}^{2} < R^{2}$
if coefficient's $|t - \text{stat}| > 1, \bar{R}^{2} \uparrow, \text{else } \bar{R}^{2} \downarrow$

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

$$F = \frac{(SSE_{\text{restricted}} - SSE_{\text{unrestricted}})/q}{SE_{\text{unrestricted}} / (n-k-1)}$$

with $q$ being the number of restrictions

Testing unrestricted model
$$F = \frac{\text{Explained variance}}{\text{Unexplained variance}} = \frac{MSR}{SSR} = \frac{SSR/k}{SSE/(n-k-1)}$$

### Model Mispecification

#### Failures in regression functional form
1. Omitted variables
2. Inappropriate form of variables
3. Inappropriate scaling
4. Inappropriate pooling of data

#### Heteroskedastic
Non-constant $Var(\epsilon)$ across observations

1. Unconditional heteroskedasticity: no issues for inference
2. Conditional heteroskedasticity: SE underestimated or overestimated, t-stats inflated or deflated, F-test unreliable.

Test: BP (Breusch Pagan) $\chi_{k}^{2} = n R_{e}^{2}$ with $R_{e}^{2}$ from the regression ($e, VIs$)

Correct: Compute robust SEs (White-corrected SEs)

#### Serial Correlation (autocorrelation)

Underestimate SE, inflate $t-stat = \frac{X - \bar{X}}{SE}$ and $F-stat = \frac{MSR}{MSE}$

Test: DW (Durbin-Watson - tests first-order SC only), BG (Breusch-Godfrey - tests for SC at any lag)

Correct: SC-consistent SEs, Newey-West SEs (will also correct for CH)

#### Multicollinearity

Inflates SEs and insignificant t-stats but possible significant F-stat

Test: VIF (Variance Inflation Factor) $VIF_{X_{1}} = \frac{1}{1 - R_{X_{1}}}^{2}$

min = 1 when $R_{X_{1}}^{2} = 0$

$>5$ becoming concerning

$>10$ indicates MC

Correct: 
Exclude one or more IVs (preferred)
Use a different proxy for one of the variables
Increase sample size

If the goal is prediction, the a significant model is more important than a significant coefficient (MS less of an issue)

### Extensions of Multiple Regression

#### Influential Data Points

##### High leverage points
$$h_{ii} = \frac{1}{n} + \frac{(X_{i} - \bar{X})^{2}}{\sum (X_{i} - \bar{X})^{2}} \in [1/n, 1]$$

For small samples: If $h_{ii} > 3\left( \frac{k+1}{n} \right)$, $i$ is a potential influencer

For large samples: $3\left( \frac{k+1}{n} \right)$ (Belsey, Kuh, Welsch, 1980)

##### Outliers

1. Delete i
2. Calculate a new regression on $n-1$ cases
3. Calculate residual $e_{i}* = Y_{i} - \hat{Y}$ for all n
4. Calculate studentized residual
$$t_{i}* = \frac{e_{i}*}{S_{e}} = \frac{e_{i}}{\hat{\sigma \sqrt{1-h_{ii}}}}$$

Where $\sigma$ is an appropriate estimate of $\sigma$ (e.g., $MSE = \frac{SSE}{n-k-1}$)

$$t_{i}* = e_{i}\sqrt{\frac{(n-k-1)}{SSE(1-h_{ii})}}$$

$|t_{i}*| > $ critical $t$ for small samples

$|t_{i}*| > 3$ for large samples

##### Influential data points

Cook's Distance
$$D_{i} = \frac{e_{i}^{2}}{k\times MSE} \frac{h_{ii}}{(1 - h_{ii})^{2}}$$ (Discrepancy $\times$ Leverage)

Large $D_{i}$ indicates influencer

$D_{i} > 0.5$ may be influencial
$D_{i} > 1$ likely to be (common)
$D_{i} > 2\sqrt{k/n}$ - large samples

#### Dummy variables and Logit Model

##### Goodness of Fit:

Likelihood ratio (LR) test:

$$LR = -2(\text{log likelihood restricted model} - \text{log likelihood unrestricted model})$$

no $R^{2}$, just pseudo-$R^{2}$

### Time-Series Analysis

#### Trend Models

Linear: DV changes at a constant rate with time (time is the IV)

$$y_{t} = b_{0} + b_{1} t + \epsilon_{t}$$

Log-Linear: DV changes at a constant growth rate. Let $y_{t} = e^{b_{0} + b_{1} t + \epsilon_{t}}$

$$\ln(y_{t}) = b_{0} + b_{1} t + \epsilon_{t}$$

Note: $\epsilon_{t}$ must be uncorrelated accoress time periods (use Durbin-Watson test on residual $H_{0}: DW = 2$)

#### Autoregressive Time-Series Model

$$AR(1) x_{t} = b_{0} + b_{1} x_{t-1} + \epsilon_{t}$$

$$AR(p) x_{t} = b_{0} + b_{1} x_{t-1} + b_{2} x_{t-2} + \ldots + b_{p} x_{t-p} + \epsilon_{t}$$ 

Covariance Stationary Series: mean, var, cov($y_{t}, y_{t-s}$) constant and finite in all periods, otherwise estimate of $b_{1}$ will be biased.

Cannot use DW statistics to test Serial Correlation, instead

1. Estimate an AR model (e.g. AR(1))
2. Compute $\rho_{\epsilon \epsilon_{t-k}}$ (e.g. AR(2))
3. Test $H_{0}: \rho_{\epsilon \epsilon_{t-k}} = 0$ (reject $H_{0}$ implies a misspecified model)

##### Mean Reversion

Let $x_{t} = b_{0} + b_{1} x_{t}$ to find the reverting level.

#### Comparing Models

RMSE

Instability of Regression Coefficients (using experience and judgement to decide the correct time period)

#### Random Walk & Unit Roots

AR(1) with $b_{0} = 0, b_{1} = 0$ - can only conclude that we have a random walk

If not RW on AR(1): transforms into a covariance-stationary time-series by first differencing

##### Unit root test of non-stationarity

Dickey-Fuller test for a unit root

$|b_{1}| < 1$ from AR(1): series is covariance stationary
$b_{1} = 1$, unit root, not covariance stationary

#### Seasonality

Use a seasonal lag

#### ARCH Models

Autoregressive Conditional Heleroskedasticity

#### Regression with more than 1 Time-Series

Test each time-series for unit root using DF test

If both have a unit root, see if they're cointegrated (i.e. share a common trend), if yes, can only evaluate long term relation.

Use Engle-Granger DF to test cointegration (reject to have cointegration)