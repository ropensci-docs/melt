# Summary methods

Provides summary methods for objects.

## Usage

``` r
# S4 method for class 'EL'
summary(object, ...)

# S4 method for class 'ELMT'
summary(object, ...)

# S4 method for class 'ELT'
summary(object, ...)

# S4 method for class 'GLM'
summary(object, ...)

# S4 method for class 'LM'
summary(object, ...)

# S4 method for class 'QGLM'
summary(object, ...)
```

## Arguments

- object:

  An object for which a summary is desired.

- ...:

  Further arguments passed to methods.

## Value

The form of the value returned by `summary()` depends on the class of
its argument.

## Methods (by class)

- `summary(EL)`: Summarizes the test results of the specified
  parameters.

- `summary(ELMT)`: Summarizes the multiple testing results.

- `summary(ELT)`: Summarizes the hypothesis test results.

- `summary(GLM)`: Summarizes the results of the overall model test and
  the significance tests for coefficients. The dispersion parameter is
  extracted for display.

- `summary(LM)`: Summarizes the results of the overall model test and
  the significance tests for coefficients.

- `summary(QGLM)`: Summarizes the results of the overall model test and
  the significance tests for coefficients. The estimated dispersion
  parameter is extracted for display.

## See also

[EL](https://docs.ropensci.org/melt/reference/EL-class.md),
[ELMT](https://docs.ropensci.org/melt/reference/ELMT-class.md),
[ELT](https://docs.ropensci.org/melt/reference/ELT-class.md),
[GLM](https://docs.ropensci.org/melt/reference/GLM-class.md),
[LM](https://docs.ropensci.org/melt/reference/LM-class.md),
[QGLM](https://docs.ropensci.org/melt/reference/QGLM-class.md),

## Examples

``` r
data("faithful")
fit <- el_mean(faithful, par = c(3.5, 70))
summary(fit)
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

data("mtcars")
fit2 <- el_lm(mpg ~ wt, data = mtcars)
summary(fit2)
#> 
#>  Empirical Likelihood
#> 
#> Model: lm 
#> 
#> Call:
#> el_lm(formula = mpg ~ wt, data = mtcars)
#> 
#> Number of observations: 32 
#> Number of parameters: 2 
#> 
#> Parameter values under the null hypothesis:
#> (Intercept)          wt 
#>       37.29        0.00 
#> 
#> Lagrange multipliers:
#> [1] -109.51   14.62
#> 
#> Maximum EL estimates:
#> (Intercept)          wt 
#>      37.285      -5.344 
#> 
#> logL: -330.4 , logLR: -219.5 
#> Chisq: 439.1, df: 1, Pr(>Chisq): < 2.2e-16
#> Constrained EL: initialization failed 
#> 
#> Coefficients:
#>             Estimate Chisq Pr(>Chisq)    
#> (Intercept)   37.285 443.3     <2e-16 ***
#> wt            -5.344 439.1     <2e-16 ***
#> ---
#> Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1
#> 
```
