# Model fitting

## Fitting an `EL` object

The melt package provides several functions to construct an `EL` object
or an object that inherits from `EL`:

- [`el_mean()`](https://docs.ropensci.org/melt/reference/el_mean.md) for
  the mean.
- [`el_sd()`](https://docs.ropensci.org/melt/reference/el_sd.md) for the
  standard deviation.
- [`el_lm()`](https://docs.ropensci.org/melt/reference/el_lm.md) for
  linear models.
- [`el_glm()`](https://docs.ropensci.org/melt/reference/el_glm.md) for
  generalized linear models.

We illustrate the usage of
[`el_mean()`](https://docs.ropensci.org/melt/reference/el_mean.md) with
the `faithful` data set.

``` r

data("faithful")
str(faithful)
#> 'data.frame':    272 obs. of  2 variables:
#>  $ eruptions: num  3.6 1.8 3.33 2.28 4.53 ...
#>  $ waiting  : num  79 54 74 62 85 55 88 85 51 85 ...
summary(faithful)
#>    eruptions        waiting    
#>  Min.   :1.600   Min.   :43.0  
#>  1st Qu.:2.163   1st Qu.:58.0  
#>  Median :4.000   Median :76.0  
#>  Mean   :3.488   Mean   :70.9  
#>  3rd Qu.:4.454   3rd Qu.:82.0  
#>  Max.   :5.100   Max.   :96.0
```

Suppose we are interested in evaluating empirical likelihood at
`c(3.5, 70)`.

``` r

fit <- el_mean(faithful, par = c(3.5, 70))
class(fit)
#> [1] "EL"
#> attr(,"package")
#> [1] "melt"
showClass("EL")
#> Class "EL" [package "melt"]
#> 
#> Slots:
#>                                                                        
#> Name:         optim         logp         logl        loglr    statistic
#> Class:         list      numeric      numeric      numeric      numeric
#>                                                                        
#> Name:            df         pval         nobs         npar      weights
#> Class:      integer      numeric      integer      integer      numeric
#>                                                           
#> Name:  coefficients       method         data      control
#> Class:      numeric    character          ANY    ControlEL
#> 
#> Known Subclasses: 
#> Class "CEL", directly
#> Class "SD", directly
#> Class "LM", by class "CEL", distance 2
#> Class "GLM", by class "CEL", distance 3
#> Class "QGLM", by class "CEL", distance 4
```

The `faithful` data frame is coerced to a numeric matrix. Simple print
method shows essential information on `fit`.

``` r

fit
#> 
#>  Empirical Likelihood
#> 
#> Model: mean 
#> 
#> Maximum EL estimates:
#> eruptions   waiting 
#>     3.488    70.897 
#> 
#> Chisq: 8.483, df: 2, Pr(>Chisq): 0.01439
#> EL evaluation: converged
```

Note that the maximum empirical likelihood estimates are the same as the
sample average. The chi-square value shown corresponds to the minus
twice the empirical log-likelihood ratio. It has an asymptotic
chi-square distribution of 2 degrees of freedom under the null
hypothesis. Hence the $`p`$-value here is not exact. The convergence
status at the bottom can be used to check the convex hull constraint.

Weighted data can be handled by supplying the `weights` argument. For
non-`NULL` `weights`, weighted empirical likelihood is computed. Any
valid `weights` is re-scaled for internal computation to add up to the
total number of observations. For simplicity, we use `faithful$waiting`
as our weight vector.

``` r

w <- faithful$waiting
(wfit <- el_mean(faithful, par = c(3.5, 70), weights = w))
#> 
#>  Weighted Empirical Likelihood
#> 
#> Model: mean 
#> 
#> Maximum EL estimates:
#> eruptions   waiting 
#>     3.684    73.494 
#> 
#> Chisq: 25.41, df: 2, Pr(>Chisq): 3.039e-06
#> EL evaluation: converged
```

We get different results, where the estimates are now the weighted
sample average. The chi-square value and the associated $`p`$-value are
based on the same limit theorem, but care must be taken when
interpreting the results since they are largely affected by the limiting
behavior of the weights.
