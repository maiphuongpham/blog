---
title: "Linear Regression: A Deep Dive into the Mathematical Framework"
date: 2023-05-27T15:54:07-08:00
draft: false
math: true
ShowToc: true
ShowRef: true
tags: [regression, statistics]
---

Linear Regression is a starting point for learning statistics. I have taken numerous classes that discusses this model, emphasizing its simplicity and ease of implementation. Despite the straightforward nature, Linear Regression is a fundamental technique that every graduate school and quant company would expect, or even assume the candidates have profoundly understood. In this brief overview, I aim to provide a concise explanation of the method, employing a more mathematical and computational approach.

### Simple Linear Regression
#### Introduction
A linear relationship between the mean response and the value of a single independent variable can be expressed as

$$Y = \beta_0 + \beta_1 x + \epsilon,$$
where $\epsilon$, representing the random error, is assumed to be independent and normally distributed  with mean $0$ and variance $\sigma^2$, i.e.
$$\epsilon \overset {iid}\sim N(0,\sigma^2)\tag{1}$$

Note that this assumption can be relaxed under certain conditions, such as when the number of observations $n$ is sufficiently large, in which case the estimator is approximately normally distributed, justified by the central limit theorem.

From the assumption in $(1)$ and given the value of the input $x$, using the linearity of the normal distribution, it follows that 

$$Y \sim N(\beta_0 + \beta_1 x, \sigma^2)$$

#### Least Squares Estimators

Now suppose that a random sample $Y_i$ corresponding to the input values $x_i$, $i=1,\ldots, n$ are to be observed and used to estimate $\beta_0$ and $\beta_1$ in a simple linear regression model. Let $B_0$ and $B_1$ be the estimators of $\beta_0$ and $\beta_1$, respectively, the sum of the squared differences between the estimated responses and the actual response values, call it $SS_R$ is given by

$$SS_R = \sum_{i=1}^n (Y_i - (B_0 + B_1 x_i))^2$$

The method that chooses estimators $B_0$ and $B_1$ that minimize $SS_R$ is called the method of least squares.

$$\frac{\partial SS_R}{\partial B_0} = -2 \sum_{i=1}^n (Y_i - (B_0 + B_1 x_i))$$

$$\frac{\partial SS_R}{\partial B_1} = -2 \sum_{i=1}^{n} x_i (Y_i - (B_0 + B_1 x_i))$$

Setting equal to 0 yields normal equations

$$\sum_{i=1}^n Y_i = \sum_{i=1}^n (B_0 + B_1 x_i)$$
$$\sum_{i=1}^n x_i Y_i = \sum_{i=1}^n x_i (B_0 + B_1 x_i)$$

Solving gives

$$B_1 = \frac{\sum_{i=1}^n (x_i - \bar{x})(Y_i - \bar{Y})}{\sum_{i=1}^n (x_i - \bar{x})^2} \overset {(2)}= \frac{\sum_{i=1}^n (x_i - \bar{x})Y_i}{\sum_{i=1}^n (x_i - \bar{x})^2}$$

$$B_0 = \bar{Y} - B_1 \bar{x}$$

Equation $(2)$: $\\sum_{i=1}^n (x_i - \bar{x})\bar{Y} = \bar{Y}\sum_{i=1}^n(x_i - \bar{x}) = 0$

These are our estimators for slope and intercept, respectively.

#### Distributions of the Estimators

$B_0$ and $B_1$ are linear combination of the independent normal random variables $Y_i$, $i = 1, \ldots, n$, so they are normally distributed. Their means and variances can be calculated as follows:

$$E[B_1] = E\left[ \frac{\sum_{i=1}^n (x_i - \bar{x})(Y_i - \bar{Y})}{\sum_{i=1}^n (x_i - \bar{x})^2} \right] = \frac{\sum_{i=1}^n (x_i - \bar{x}) E[Y_i - \bar{Y}]}{\sum_{i=1}^n (x_i - \bar{x})^2} \overset {(3)}= \frac{\sum_{i=1}^n (x_i - \bar{x}) \beta_1 [Y_i - \bar{Y}]}{\sum_{i=1}^n (x_i - \bar{x})^2}= \beta_1$$

Equation $(3)$: $E[Y_i] = \beta_0 + \beta_1 x_i$ and $E[\bar{Y}] = \beta_0 + \beta_1 \bar{x}$, thus $E[Y_i - \bar{Y}] = \beta_1 (x_i - \bar{x})$

So $B_1$ is an *unbiased* estimator of $\beta_1$

$$Var[B_1] = Var\left[ \frac{\sum_{i=1}^n (x_i - \bar{x})Y_i}{\sum_{i=1}^n (x_i - \bar{x})^2} \right] = \frac{\sum_{i=1}^n Var[(x_i - \bar{x})Y_i]}{(\sum_{i=1}^n (x_i - \bar{x})^2)^2} = \frac{\sum_{i=1}^n(x_i - \bar{x})^2 Var[Y_i]}{(\sum_{i=1}^n (x_i - \bar{x})^2)^2} = \frac{\sigma^2}{\sum_{i=1}^n(x_i - \bar{x})^2}$$

Similarly, $$E[B_0] = \beta_0 \text{ and } Var[B_0] = \frac{\sigma^2 \frac{1}{n}\sum_{i=1}^n x_i^2}{\sum_{i=1}^n (x_i - \bar{x})^2}$$

Note that $B_0$ and $B_1$ are **not** independent. The quantities $Y_i - B_0 - B_1 x_i$ are called the *residuals*. The sum of squares of the residuals $SS_R$ can be used to estimate the unknown $\sigma^2$ by

$$\frac{SS_R}{\sigma^2} \sim \chi_{n-2}^2$$

which implies that

$$E\left[\frac{SS_R}{\sigma^2}\right] = n - 2$$

Thus $\dfrac{SS_R}{n-2}$ is an unbiased estimator of $\sigma^2$ (analog of $S^2$).

**Remark:** if we let 
$$S_{xY} = \sum_{i=1}^n (x_i - \bar{x})(Y_i - \bar{Y}); S_{xx} = \sum_{i=1}^n (x_i - \bar{x})^2; S_{YY} = \sum_{i=1}^n (Y_i - \bar{Y})^2$$
the sum of squares of the residuals can be established
$$SS_R = S_{YY} - \frac{S_{xY}^2}{S_{xx}}$$
the least squares estimators of $\beta_1$ and $\beta_0$
$$B_1 = \frac{S_{xY}}{S_{xx}}, B_0 = \bar{Y} - B \bar{x}$$
are distributed as follows
$$B_1 \sim N\left(\beta_1, \frac{\sigma^2}{S_{xx}}\right), B_0 \sim N\left(\beta_0, \frac{\sigma^2 \sum_i x_i^2}{n S_{xx}}\right)$$


#### Hypothesis Testing
We first establish that $\frac{SS_R}{\sigma^2}$ (i) has a chi-squared distribution with $n-2$ degrees of freedom and (ii) be independent of $B_0$ and $B_1$

(i) is true since $\dfrac{Y_i - E[Y_i]}{\sqrt{Var(Y_i)}}, i = 1, \ldots, n$ are independent standard normal so their sum has chi-squared distribution.

(ii) is true following the fundamental result that in normal sampling $\bar{X}$ and $S^2$ are independent (though not obvious).

To test the hypotheses

$$H_0: \beta_1 = \beta_{1,0} \text{ vs } H_1: \beta_1 \not = \beta_{1,0}$$ 

note that,
$$\frac{B_1 - \beta_1}{\sigma / \sqrt{S_{xx}}} \sim N(0,1)$$

therefore, if $H_0$ is true, by independence, from the definition of a t-random variable it follows that:
$$\frac{B_1 - \beta_{1,0}}{\sqrt{\frac{SS_R}{n-2} / S_{xx}}} \sim t_{n-2}$$

To test

$$H_0: \beta_0 = \beta_{0,0} \text{ vs } H_1: \beta_0 \not = \beta_{0,0}$$

note that,

$$\frac{B_0 - \beta_0}{\sigma \sqrt{\frac{\frac{1}{n} \sum_{i=1}^n x_i^2}{S_{xx}}}} \sim N(0,1)$$

therefore, if $H_0$ is true and by independence, then 
$$\frac{B_0 - \beta_{0,0}}{\sqrt{\frac{SS_R}{n-2}} \sqrt{{\frac{\frac{1}{n} \sum_{i=1}^n x_i^2}{S_{xx}}}}} \sim t_{n-2}$$

#### Confidence Intervals

- Confidence Interval for $\beta_0$ or $\beta_1$:

$$100(1-\alpha) \text{CI two-sized}$$

$$\beta_1 \in [\hat{\beta_1} \pm t_{\alpha/2}, n-2 \sqrt{\frac{SS_R / (n-2)}{S_{xx}}}]$$

$$\beta_0 \in [\hat{\beta_0} \pm t_{\alpha/2}, n-2 \sqrt{\frac{SS_R \frac{1}{n} \sum_{i=1}^{n}x_i^2}{(n-2)S_{xx}}}]$$

- Confidence Interval for new response

$$ E[Y|x^\ast] = \beta_0 + \beta_1 x^\ast $$

Point estimator: $\beta_0 + \beta_1 x^*$

$$E[B_0 + B_1 x^*] = \beta_0 + \beta_1 x^\ast$$

$$Var[B_0 + B_1 x^{\ast}] = \sigma^2 [\frac{1}{n} + \frac{(x^{\ast} - \bar{x})^2}{S_{xx}}]$$

$$\beta_0 + \beta_1 x^{\ast} \in \left[ \hat{\beta_0} + \hat{\beta_1} x^{\ast} \pm t_{\alpha/2, n-2} \sqrt{\frac{SS_R}{n-2} \left( \frac{1}{n} + \frac{(x^{\ast} - \bar{x})^2}{S_{xx}} \right)} \right]$$

**Notes:**

- We could have $Y_i = \beta_0 + \beta_1 x_i^2 + \epsilon_i$ and still use linear regression techniques.
- The $x_i$ can be "Dummy variables"
$\x_i = 1$ if $i$th person smokes, and 0 otherwise.
$H_0: \beta_0 = 0$ - Test whether smoking affects (say) life expectancy.

### Multiple Linear Regression

#### Introduction
The Multiple Linear Regression model takes the form

$$Y_i = \beta_0 + \beta_1 x_{i1} + \cdots + \beta_k x_{ik} + \epsilon_i$$

$$
\begin{align*}
   \begin{bmatrix}
      y_1 \\\
      y_2 \\\
      \vdots \\\
      y_n
   \end{bmatrix}
   &=
   \begin{bmatrix}
      1 & x_{11} & \cdots & x_{1k} \\\
      1 & x_{21} & \cdots & x_{2k} \\\
      \vdots & \vdots & \ddots & \vdots \\\
      1 & x_{n1} & \cdots & x_{nk} \\\
   \end{bmatrix} 
   \begin{bmatrix}
      \beta_0 \\\
      \beta_1 \\\
      \vdots \\\
      \beta_k
   \end{bmatrix}
   +
   \begin{bmatrix}
      \epsilon_1 \\\
      \epsilon_2 \\\
      \vdots \\\
      \epsilon_n
   \end{bmatrix}
\end{align*}
$$

$$
\begin{matrix}
    y & = & X & \beta & + & \epsilon \\\
    (n \times 1 ) & & (n \times (k + 1)) & ((k + 1) \times 1) & & (n \times 1)
\end{matrix}
$$

Multiple Linear Regression model

$$\min_\beta (y - X\beta)' (y - X\beta) \text{, note that }v'v = \sum_{i=1}^{n} v_i^2$$

$$\frac{\partial}{\partial \beta} (y - X\beta)'(y - X\beta) = -2 X'(y - X\beta)$$

Set equal to 0:

$$X'y = X'X\beta \text{ (Normal Equations)}$$ 

$$\hat{\beta} = (X'X)^{-1} X'y$$

$$\hat{y} = X\hat{\beta}$$

$$e = y - \hat{y} = y - X\hat{\beta}$$

#### Distribution of $\hat{\beta}$

$$\hat{\beta} \sim N(\mu, \Sigma)$$

$$
\Sigma = \begin{bmatrix}
   \operatorname{cov}(\hat{\beta}_0, \hat{\beta}_0) & \operatorname{cov}(\hat{\beta}_0, \hat{\beta}_1) & \cdots & \operatorname{cov}(\hat{\beta}_0, \hat{\beta}_k) \\\\
   \operatorname{cov}(\hat{\beta}_1, \hat{\beta}_0) & \operatorname{cov}(\hat{\beta}_1, \hat{\beta}_1) & \cdots & \operatorname{cov}(\hat{\beta}_1, \hat{\beta}_k) \\\\
   \vdots & \vdots & \ddots & \vdots \\\\
   \operatorname{cov}(\hat{\beta}_k, \hat{\beta}_0) & \operatorname{cov}(\hat{\beta}_k, \hat{\beta}_1) & \cdots & \operatorname{cov}(\hat{\beta}_k, \hat{\beta}_k) \\\\
\end{bmatrix}
$$

$$E(\hat{\beta}) = E\left[ (X'X)^{-1}X'y \right] = (X'X)^{-1}X' E(y)$$

$$= (X'X)^{-1}X'X\beta = \beta \rightarrow \hat{\beta} \text{ is unbiased}$$

$$E(y) = E(X\beta + \epsilon) = X\beta + E(\epsilon) = X\beta$$

$$Cov(\hat{\beta}) = Cov((X'X)^{-1}X'y) = (X'X)^{-1} X' Cov(y) ((X'X)^{-1}X')'$$

$$Var(aZ) = aVar(z)a$$

$$= \sigma^2 (X'X)^{-1} X'I.X[(X'X)^{-1}]'$$

$$= \sigma^2 (X'X)^{-1} X'X (X'X)^{-1}$$

$$= \sigma^2 (X'X)^{-1}$$

#### Point estimation

$$\hat{\beta} = (X'X)^{-1}X'y \text{ ,    } \mu = \bar{x}$$

$$\hat{\sigma^2} = \frac{(y-X\hat\beta{})(y - X - \hat{\beta})}{n - 1 - k} \text{ ,   } \sigma^2 = s^2$$

#### Interval estimation / Hypothesis testing ingredients

$$\hat{\beta} \sim N(\beta, \sigma^2(X'X)^{-1}) \text{ ,    } \bar{x} \sim N(\mu, \sigma^2 / n)$$
$$\frac{(n - 1 - k)\hat{\sigma}^2}{\sigma^2} \sim \chi^2_{n - 1 - k} \text{ ,    } \frac{(n - 1)s^2}{\sigma^2} \sim \chi^2_{n_1}$$

- Interval estimation

$$\beta_j \in [\hat{\beta_j} \pm t_{\alpha/2, n - 1 - k} \hat{\sigma^2} [(X'X)^{-1}_{jj}]]$$

$$\mu \in [\bar{x} \pm t_{\alpha/2, n - 1} \frac{s}{\sqrt{n}}]$$


- Hypothesis test
$$H_0: \beta_j = \beta_{j,0} \text{ vs } H_1: \beta_j \not = \beta_{j,0}$$

$$\text{If } T = \frac{\hat{\beta_j} - \beta_{j,0}}{\hat{\sigma} [(X'X)^{-1}]_{jj}} \text{ realization}$$

$$\text{in } [ \pm t_{\alpha/2, n - 1 - k}] \rightarrow \text{not reject}$$

$$H_0: \mu = \mu_0 \text{ ,  } H_1: \mu \not = \mu_0$$

$$\text{If } T = \frac{\bar{x} - \mu_0}{s / \sqrt{n}} \text{ realization}$$

$$\text{in }[ \pm t_{\alpha/2, n - 1}] \rightarrow \text{not reject}$$

### ANOVA (Analysis of Variance)



#### Coefficient of Determination $R^{2}$

$$R^{2} = \frac{SSR}{SST} = \frac{\sum(\hat{Y_{i}} - \bar{Y})^{2}}{\sum(Y_{i} - \bar{Y})^{2}}$$

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

$$F = \frac{(SSE_{\text{restricted}} - SSE_{\text{unrestricted}})/q}{SSE_{\text{unrestricted}} / (n-k-1)}$$

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