# Empirical likelihood for linear models

Fits a linear model with empirical likelihood.

## Usage

``` r
el_lm(
  formula,
  data,
  weights = NULL,
  na.action,
  offset,
  control = el_control(),
  ...
)
```

## Arguments

- formula:

  An object of class [`formula`](https://rdrr.io/r/stats/formula.html)
  (or one that can be coerced to that class) for a symbolic description
  of the model to be fitted.

- data:

  An optional data frame, list or environment (or object coercible by
  [`as.data.frame()`](https://rdrr.io/r/base/as.data.frame.html) to a
  data frame) containing the variables in `formula`. If not found in
  data, the variables are taken from `environment(formula)`.

- weights:

  An optional numeric vector of weights to be used in the fitting
  process. Defaults to `NULL`, corresponding to identical weights. If
  non-`NULL`, weighted empirical likelihood is computed.

- na.action:

  A function which indicates what should happen when the data contain
  `NA`s. The default is set by the `na.action` setting of
  [`options`](https://rdrr.io/r/base/options.html), and is `na.fail` if
  that is unset.

- offset:

  An optional expression for specifying an *a priori* known component to
  be included in the linear predictor during fitting. This should be
  `NULL` or a numeric vector or matrix of extents matching those of the
  response. One or more [`offset`](https://rdrr.io/r/stats/offset.html)
  terms can be included in the formula instead or as well, and if more
  than one are specified their sum is used.

- control:

  An object of class
  [ControlEL](https://docs.ropensci.org/melt/reference/ControlEL-class.md)
  constructed by
  [`el_control()`](https://docs.ropensci.org/melt/reference/el_control.md).

- ...:

  Additional arguments to be passed to the low level regression fitting
  functions. See ‘Details’.

## Value

An object of class of
[LM](https://docs.ropensci.org/melt/reference/LM-class.md).

## Details

Suppose that we observe \\n\\ independent random variables \\{Z_i}
\equiv {(X_i, Y_i)}\\ from a common distribution, where \\X_i\\ is the
\\p\\-dimensional covariate (including the intercept if any) and \\Y_i\\
is the response. We consider the following linear model: \$\$Y_i =
X_i^\top \theta + \epsilon_i,\$\$ where \\\theta = (\theta_0, \dots,
\theta\_{p-1})\\ is an unknown \\p\\-dimensional parameter and the
errors \\\epsilon_i\\ are independent random variables that satisfy
\\\textrm{E}(\epsilon_i \| X_i)\\ = 0. We assume that the errors have
finite conditional variances. Then the least square estimator of
\\\theta\\ solves the following estimating equations: \$\$\sum\_{i =
1}^n(Y_i - X_i^\top \theta)X_i = 0.\$\$ Given a value of \\\theta\\, let
\\{g(Z_i, \theta)} = {(Y_i - X_i^\top \theta)X_i}\\ and the (profile)
empirical likelihood ratio is defined by \$\$R(\theta) =
\max\_{p_i}\left\\\prod\_{i = 1}^n np_i : \sum\_{i = 1}^n p_i g(Z_i,
\theta) = \theta,\\ p_i \geq 0,\\ \sum\_{i = 1}^n p_i = 1 \right\\.\$\$
`el_lm()` first computes the parameter estimates by calling
[`lm.fit()`](https://rdrr.io/r/stats/lmfit.html) (with `...` if any)
with the `model.frame` and `model.matrix` obtained from the `formula`.
Note that the maximum empirical likelihood estimator is the same as the
the quasi-maximum likelihood estimator in our model. Next, it tests
hypotheses based on asymptotic chi-square distributions of the empirical
likelihood ratio statistics. Included in the tests are overall test with
\$\$H_0: \theta_1 = \theta_2 = \cdots = \theta\_{p-1} = 0,\$\$ and
significance tests for each parameter with \$\$H\_{0j}: \theta_j = 0,\\
j = 0, \dots, p-1.\$\$

## References

Owen A (1991). “Empirical Likelihood for Linear Models.” *The Annals of
Statistics*, **19**(4), 1725–1747.
[doi:10.1214/aos/1176348368](https://doi.org/10.1214/aos/1176348368) .

## See also

[EL](https://docs.ropensci.org/melt/reference/EL-class.md),
[LM](https://docs.ropensci.org/melt/reference/LM-class.md),
[`el_glm()`](https://docs.ropensci.org/melt/reference/el_glm.md),
[`elt()`](https://docs.ropensci.org/melt/reference/elt.md),
[`el_control()`](https://docs.ropensci.org/melt/reference/el_control.md)

## Examples

``` r
## Linear model
data("thiamethoxam")
fit <- el_lm(fruit ~ trt, data = thiamethoxam)
summary(fit)
#> 
#>  Empirical Likelihood
#> 
#> Model: lm 
#> 
#> Call:
#> el_lm(formula = fruit ~ trt, data = thiamethoxam)
#> 
#> Number of observations: 165 
#> Number of parameters: 4 
#> 
#> Parameter values under the null hypothesis:
#> (Intercept)    trtSpray   trtFurrow     trtSeed 
#>       6.016       0.000       0.000       0.000 
#> 
#> Lagrange multipliers:
#> [1] -0.03994 -0.29622  0.59777 -0.15872
#> 
#> Maximum EL estimates:
#> (Intercept)    trtSpray   trtFurrow     trtSeed 
#>      5.6667     -0.7167      2.7798     -0.3452 
#> 
#> logL: -875.9 , logLR: -33.38 
#> Chisq: 66.76, df: 3, Pr(>Chisq): 2.113e-14
#> Constrained EL: converged 
#> 
#> Coefficients:
#>             Estimate   Chisq Pr(>Chisq)    
#> (Intercept)   5.6667 413.766    < 2e-16 ***
#> trtSpray     -0.7167   1.978      0.160    
#> trtFurrow     2.7798  19.259   1.14e-05 ***
#> trtSeed      -0.3452   0.416      0.519    
#> ---
#> Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1
#> 

## Weighted data
wfit <- el_lm(fruit ~ trt, data = thiamethoxam, weights = visit)
summary(wfit)
#> 
#>  Weighted Empirical Likelihood
#> 
#> Model: lm 
#> 
#> Call:
#> el_lm(formula = fruit ~ trt, data = thiamethoxam, weights = visit)
#> 
#> Number of observations: 165 
#> Number of parameters: 4 
#> 
#> Parameter values under the null hypothesis:
#> (Intercept)    trtSpray   trtFurrow     trtSeed 
#>       6.358       0.000       0.000       0.000 
#> 
#> Lagrange multipliers:
#> [1] -0.06482 -0.21994  0.51894 -0.19381
#> 
#> Maximum EL estimates:
#> (Intercept)    trtSpray   trtFurrow     trtSeed 
#>     5.71940    -0.10153     2.94806    -0.07815 
#> 
#> logL: -847.5 , logLR: -31.59 
#> Chisq: 63.18, df: 3, Pr(>Chisq): 1.229e-13
#> Constrained EL: converged 
#> 
#> Coefficients:
#>             Estimate   Chisq Pr(>Chisq)    
#> (Intercept)  5.71940 415.486    < 2e-16 ***
#> trtSpray    -0.10153   0.028      0.867    
#> trtFurrow    2.94806  19.830   8.46e-06 ***
#> trtSeed     -0.07815   0.020      0.887    
#> ---
#> Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1
#> 

## Missing data
fit2 <- el_lm(fruit ~ trt + scb, data = thiamethoxam,
  na.action = na.omit, offset = NULL
)
summary(fit2)
#> 
#>  Empirical Likelihood
#> 
#> Model: lm 
#> 
#> Call:
#> el_lm(formula = fruit ~ trt + scb, data = thiamethoxam, na.action = na.omit, 
#>     offset = NULL)
#> 
#> Number of observations: 162 
#> Number of parameters: 5 
#> 
#> Parameter values under the null hypothesis:
#> (Intercept)    trtSpray   trtFurrow     trtSeed         scb 
#>       6.043       0.000       0.000       0.000       0.000 
#> 
#> Lagrange multipliers:
#> [1] -0.017410 -0.301618  0.595467 -0.153307 -0.008558
#> 
#> Maximum EL estimates:
#> (Intercept)    trtSpray   trtFurrow     trtSeed         scb 
#>     5.62981    -0.74024     2.82886    -0.24460     0.01551 
#> 
#> logL: -857 , logLR: -32.79 
#> Chisq: 65.58, df: 4, Pr(>Chisq): 1.939e-13
#> Constrained EL: converged 
#> 
#> Coefficients:
#>             Estimate   Chisq Pr(>Chisq)    
#> (Intercept)  5.62981 405.317    < 2e-16 ***
#> trtSpray    -0.74024   2.160      0.142    
#> trtFurrow    2.82886  23.410   1.31e-06 ***
#> trtSeed     -0.24460   0.235      0.628    
#> scb          0.01551   0.141      0.707    
#> ---
#> Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1
#>   (3 observations deleted due to missingness)
#> 
```
