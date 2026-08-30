# Empirical likelihood for the mean

Computes empirical likelihood for the mean.

## Usage

``` r
el_mean(x, par, weights = NULL, control = el_control())
```

## Arguments

- x:

  A numeric matrix, or an object that can be coerced to a numeric
  matrix. Each row corresponds to an observation. The number of rows
  must be greater than the number of columns.

- par:

  A numeric vector of parameter values to be tested. The length of the
  vector must be the same as the number of columns in `x`.

- weights:

  An optional numeric vector of weights to be used in the fitting
  process. The length of the vector must be the same as the number of
  rows in `x`. Defaults to `NULL`, corresponding to identical weights.
  If non-`NULL`, weighted empirical likelihood is computed.

- control:

  An object of class
  [ControlEL](https://docs.ropensci.org/melt/reference/ControlEL-class.md)
  constructed by
  [`el_control()`](https://docs.ropensci.org/melt/reference/el_control.md).

## Value

An object of class
[EL](https://docs.ropensci.org/melt/reference/EL-class.md).

## Details

Let \\X_i\\ be independent and identically distributed \\p\\-dimensional
random variable from an unknown distribution \\P\\ for \\i = 1, \dots,
n\\. We assume that \\{\textrm{E}\[X_i\]} = {\theta_0} \in
{\rm{I\\R}}^p\\ and that \\P\\ has a positive definite covariance
matrix. Given a value of \\\theta\\, the (profile) empirical likelihood
ratio is defined by \$\$R(\theta) = \max\_{p_i}\left\\\prod\_{i = 1}^n
np_i : \sum\_{i = 1}^n p_i X_i = \theta,\\ p_i \geq 0,\\ \sum\_{i = 1}^n
p_i = 1 \right\\.\$\$ `el_mean()` computes the empirical log-likelihood
ratio statistic \\-2\log R(\theta)\\, along with other values in
[EL](https://docs.ropensci.org/melt/reference/EL-class.md).

## References

Owen A (1990). “Empirical Likelihood Ratio Confidence Regions.” *The
Annals of Statistics*, **18**(1), 90–120.
[doi:10.1214/aos/1176347494](https://doi.org/10.1214/aos/1176347494) .

## See also

[EL](https://docs.ropensci.org/melt/reference/EL-class.md),
[`elt()`](https://docs.ropensci.org/melt/reference/elt.md),
[`el_eval()`](https://docs.ropensci.org/melt/reference/el_eval.md),
[`el_control()`](https://docs.ropensci.org/melt/reference/el_control.md)

## Examples

``` r
## Scalar mean
data("precip")
fit <- el_mean(precip, 30)
fit
#> 
#>  Empirical Likelihood
#> 
#> Model: mean 
#> 
#> Maximum EL estimates:
#> [1] 34.89
#> 
#> Chisq: 8.285, df: 1, Pr(>Chisq): 0.003998
#> EL evaluation: converged 
#> 
summary(fit)
#> 
#>  Empirical Likelihood
#> 
#> Model: mean 
#> 
#> Number of observations: 70 
#> Number of parameters: 1 
#> 
#> Parameter values under the null hypothesis:
#> [1] 30
#> 
#> Lagrange multipliers:
#> [1] 0.02319
#> 
#> Maximum EL estimates:
#> [1] 34.89
#> 
#> logL: -301.5, logLR: -4.142 
#> Chisq: 8.285, df: 1, Pr(>Chisq): 0.003998
#> EL evaluation: converged 
#> 

## Vector mean
data("faithful")
fit2 <- el_mean(faithful, par = c(3.5, 70))
summary(fit2)
#> 
#>  Empirical Likelihood
#> 
#> Model: mean 
#> 
#> Number of observations: 272 
#> Number of parameters: 2 
#> 
#> Parameter values under the null hypothesis:
#> eruptions   waiting 
#>       3.5      70.0 
#> 
#> Lagrange multipliers:
#> [1] -0.33537  0.03043
#> 
#> Maximum EL estimates:
#> eruptions   waiting 
#>     3.488    70.897 
#> 
#> logL: -1529, logLR: -4.241 
#> Chisq: 8.483, df: 2, Pr(>Chisq): 0.01439
#> EL evaluation: converged 
#> 

## Weighted data
w <- rep(c(1, 2), each = nrow(faithful) / 2)
fit3 <- el_mean(faithful, par = c(3.5, 70), weights = w)
summary(fit3)
#> 
#>  Weighted Empirical Likelihood
#> 
#> Model: mean 
#> 
#> Number of observations: 272 
#> Number of parameters: 2 
#> 
#> Parameter values under the null hypothesis:
#> eruptions   waiting 
#>       3.5      70.0 
#> 
#> Lagrange multipliers:
#> [1] -0.30891  0.02829
#> 
#> Maximum EL estimates:
#> eruptions   waiting 
#>     3.498    70.931 
#> 
#> logL: -1513, logLR: -3.641 
#> Chisq: 7.282, df: 2, Pr(>Chisq): 0.02622
#> EL evaluation: converged 
#> 
```
