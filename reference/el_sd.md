# Empirical likelihood for the standard deviation

Computes empirical likelihood for the standard deviation.

## Usage

``` r
el_sd(x, mean, sd, weights = NULL, control = el_control())
```

## Arguments

- x:

  A numeric vector, or an object that can be coerced to a numeric
  vector.

- mean:

  A single numeric for the (known) mean value.

- sd:

  A positive single numeric for the parameter value to be tested.

- weights:

  An optional numeric vector of weights to be used in the fitting
  process. The length of the vector must be the same as the length of
  `x`. Defaults to `NULL`, corresponding to identical weights. If
  non-`NULL`, weighted empirical likelihood is computed.

- control:

  An object of class
  [ControlEL](https://docs.ropensci.org/melt/reference/ControlEL-class.md)
  constructed by
  [`el_control()`](https://docs.ropensci.org/melt/reference/el_control.md).

## Value

An object of class
[SD](https://docs.ropensci.org/melt/reference/SD-class.md).

## Details

Let \\X_i\\ be independent and identically random variable from an
unknown distribution \\P\\ for \\i = 1, \dots, n\\. We assume that
\\{\textrm{E}\[X_i\]} = {\mu_0}\\ is known and that \\P\\ has a variance
\\\sigma_0^2\\. Given a value of \\\sigma\\, the (profile) empirical
likelihood ratio is defined by \$\$R(\sigma) =
\max\_{p_i}\left\\\prod\_{i = 1}^n np_i : \sum\_{i = 1}^n p_i (X_i -
\mu_0)^2 = \sigma^2,\\ p_i \geq 0,\\ \sum\_{i = 1}^n p_i = 1
\right\\.\$\$ `el_sd()` computes the empirical log-likelihood ratio
statistic \\-2\log R(\sigma)\\, along with other values in
[SD](https://docs.ropensci.org/melt/reference/SD-class.md).

## See also

[EL](https://docs.ropensci.org/melt/reference/EL-class.md),
[SD](https://docs.ropensci.org/melt/reference/SD-class.md),
[`el_mean()`](https://docs.ropensci.org/melt/reference/el_mean.md),
[`elt()`](https://docs.ropensci.org/melt/reference/elt.md),
[`el_control()`](https://docs.ropensci.org/melt/reference/el_control.md)

## Examples

``` r
data("women")
x <- women$height
w <- women$weight
fit <- el_sd(x, mean = 65, sd = 5, weights = w)
fit
#> 
#>  Weighted Empirical Likelihood
#> 
#> Model: sd 
#> 
#> Maximum EL estimates:
#> [1] 4.34
#> 
#> Chisq: 1.843, df: 1, Pr(>Chisq): 0.1746
#> EL evaluation: converged 
#> 
summary(fit)
#> 
#>  Weighted Empirical Likelihood
#> 
#> Model: sd 
#> 
#> Number of observations: 15 
#> Number of parameters: 1 
#> 
#> Parameter values under the null hypothesis:
#> [1] 5
#> 
#> Lagrange multipliers:
#> [1] -0.01913
#> 
#> Maximum EL estimates:
#> [1] 4.34
#> 
#> logL: -41.45, logLR: -0.9215 
#> Chisq: 1.843, df: 1, Pr(>Chisq): 0.1746
#> EL evaluation: converged 
#> 
```
