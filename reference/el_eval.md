# Empirical likelihood for general estimating functions

Computes empirical likelihood with general estimating functions.

## Usage

``` r
el_eval(g, weights = NULL, control = el_control())
```

## Arguments

- g:

  A numeric matrix, or an object that can be coerced to a numeric
  matrix. Each row corresponds to an observation of an estimating
  function. The number of rows must be greater than the number of
  columns.

- weights:

  An optional numeric vector of weights to be used in the fitting
  process. The length of the vector must be the same as the number of
  rows in `g`. Defaults to `NULL`, corresponding to identical weights.
  If non-`NULL`, weighted empirical likelihood is computed.

- control:

  An object of class
  [ControlEL](https://docs.ropensci.org/melt/reference/ControlEL-class.md)
  constructed by
  [`el_control()`](https://docs.ropensci.org/melt/reference/el_control.md).

## Value

A list of the following optimization results:

- `optim` A list with the following optimization results:

  - `lambda` A numeric vector of the Lagrange multipliers of the dual
    problem.

  - `iterations` A single integer for the number of iterations
    performed.

  - `convergence` A single logical for the convergence status.

- `logp` A numeric vector of the log probabilities of the empirical
  likelihood.

- `logl` A single numeric of the empirical log-likelihood.

- `loglr` A single numeric of the empirical log-likelihood ratio.

- `statistic` A single numeric of minus twice the empirical
  log-likelihood ratio with an asymptotic chi-square distribution.

- `df` A single integer for the degrees of freedom of the statistic.

- `pval` A single numeric for the \\p\\-value of the statistic.

- `nobs` A single integer for the number of observations.

- `npar` A single integer for the number of parameters.

- `weights` A numeric vector of the re-scaled weights used for the model
  fitting.

## Details

Let \\X_i\\ be independent and identically distributed \\p\\-dimensional
random variable from an unknown distribution \\P\\ for \\i = 1, \dots,
n\\. We assume that \\P\\ has a positive definite covariance matrix. For
a parameter of interest \\\theta(F) \in {\rm{I\\R}}^p\\, consider a
\\p\\-dimensional smooth estimating function \\g(X_i, \theta)\\ with a
moment condition \$\$\textrm{E}\[g(X_i, \theta)\] = 0.\$\$ We assume
that there exists an unique \\\theta_0\\ that solves the above equation.
Given a value of \\\theta\\, the (profile) empirical likelihood ratio is
defined by \$\$R(\theta) = \max\_{p_i}\left\\\prod\_{i = 1}^n np_i :
\sum\_{i = 1}^n p_i g(X_i, \theta) = 0, p_i \geq 0, \sum\_{i = 1}^n p_i
= 1 \right\\.\$\$
[`el_mean()`](https://docs.ropensci.org/melt/reference/el_mean.md)
computes the empirical log-likelihood ratio statistic \\-2\log
R(\theta)\\ with the \\n\\ by \\p\\ numeric matrix `g`, whose \\i\\th
row is \\g(X_i, \theta)\\. Since the estimating function can be
arbitrary, `el_eval()` does not return an object of class
[EL](https://docs.ropensci.org/melt/reference/EL-class.md), and the
associated generics and methods are not applicable.

## References

Qin J, Lawless J (1994). “Empirical Likelihood and General Estimating
Equations.” *The Annals of Statistics*, **22**(1), 300–325.
[doi:10.1214/aos/1176325370](https://doi.org/10.1214/aos/1176325370) .

## See also

[EL](https://docs.ropensci.org/melt/reference/EL-class.md),
[`el_control()`](https://docs.ropensci.org/melt/reference/el_control.md)

## Examples

``` r
set.seed(123526)
mu <- 0
sigma <- 1
x <- rnorm(100)
g <- matrix(c(x - mu, (x - mu)^2 - sigma^2), ncol = 2)
el_eval(g, weights = rep(c(1, 2), each = 50))
#> $optim
#> $optim$lambda
#> [1]  0.07496852 -0.13181246
#> 
#> $optim$iterations
#> [1] 5
#> 
#> $optim$convergence
#> [1] TRUE
#> 
#> 
#> $logp
#>   [1] -4.769471 -4.990644 -4.870218 -5.091557 -5.100253 -4.930272 -5.062251
#>   [8] -4.776230 -4.686532 -5.140843 -5.128973 -5.142095 -5.113834 -4.725774
#>  [15] -5.036367 -5.067660 -5.067015 -5.119565 -5.093684 -5.098870 -4.875005
#>  [22] -5.078325 -5.023702 -5.131392 -5.090640 -5.123581 -5.084509 -5.124924
#>  [29] -5.126164 -5.116142 -4.858517 -4.609268 -4.397857 -5.128368 -5.085189
#>  [36] -5.028656 -4.858664 -5.096852 -5.133205 -4.281854 -5.140959 -4.618976
#>  [43] -5.024714 -5.101541 -4.946874 -5.143709 -5.063363 -5.131133 -5.118396
#>  [50] -5.114350 -4.450663 -4.389785 -3.925409 -4.416857 -4.447601 -4.371702
#>  [57] -4.442178 -4.450460 -4.438083 -4.379111 -4.449239 -4.105659 -4.330148
#>  [64] -4.447834 -4.438277 -4.235448 -4.383028 -4.312055 -4.180299 -4.417466
#>  [71] -4.432212 -4.396910 -4.081117 -4.330231 -4.394711 -4.127873 -4.432886
#>  [78] -4.433487 -4.258212 -4.363482 -4.236043 -4.426048 -4.434566 -4.422859
#>  [85] -4.415198 -4.302786 -3.988760 -4.300249 -4.429157 -4.320378 -4.330964
#>  [92] -4.447207 -4.435400 -4.448065 -4.450586 -4.450673 -4.437071 -4.429319
#>  [99] -4.423978 -3.975990
#> 
#> $logl
#> [1] -456.2696
#> 
#> $loglr
#> [1] -1.415871
#> 
#> $statistic
#> [1] 2.831742
#> 
#> $df
#> [1] 2
#> 
#> $pval
#> [1] 0.2427141
#> 
#> $nobs
#> [1] 100
#> 
#> $npar
#> [1] 2
#> 
#> $weights
#>   [1] 0.6666667 0.6666667 0.6666667 0.6666667 0.6666667 0.6666667 0.6666667
#>   [8] 0.6666667 0.6666667 0.6666667 0.6666667 0.6666667 0.6666667 0.6666667
#>  [15] 0.6666667 0.6666667 0.6666667 0.6666667 0.6666667 0.6666667 0.6666667
#>  [22] 0.6666667 0.6666667 0.6666667 0.6666667 0.6666667 0.6666667 0.6666667
#>  [29] 0.6666667 0.6666667 0.6666667 0.6666667 0.6666667 0.6666667 0.6666667
#>  [36] 0.6666667 0.6666667 0.6666667 0.6666667 0.6666667 0.6666667 0.6666667
#>  [43] 0.6666667 0.6666667 0.6666667 0.6666667 0.6666667 0.6666667 0.6666667
#>  [50] 0.6666667 1.3333333 1.3333333 1.3333333 1.3333333 1.3333333 1.3333333
#>  [57] 1.3333333 1.3333333 1.3333333 1.3333333 1.3333333 1.3333333 1.3333333
#>  [64] 1.3333333 1.3333333 1.3333333 1.3333333 1.3333333 1.3333333 1.3333333
#>  [71] 1.3333333 1.3333333 1.3333333 1.3333333 1.3333333 1.3333333 1.3333333
#>  [78] 1.3333333 1.3333333 1.3333333 1.3333333 1.3333333 1.3333333 1.3333333
#>  [85] 1.3333333 1.3333333 1.3333333 1.3333333 1.3333333 1.3333333 1.3333333
#>  [92] 1.3333333 1.3333333 1.3333333 1.3333333 1.3333333 1.3333333 1.3333333
#>  [99] 1.3333333 1.3333333
#> 
```
