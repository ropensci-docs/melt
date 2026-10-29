# Significance tests

Extracts the results of significance tests from a model.

## Usage

``` r
# S4 method for class 'LM'
sigTests(object, ...)
```

## Arguments

- object:

  An object that inherits from
  [LM](https://docs.ropensci.org/melt/reference/LM-class.md).

- ...:

  Further arguments passed to methods.

## Value

The form of the value returned by `sigTests()` depends on the class of
its argument.

## Methods (by class)

- `sigTests(LM)`: Extracts a list with the optimization results of
  significance tests.

## See also

[LM](https://docs.ropensci.org/melt/reference/LM-class.md),
[`getOptim()`](https://docs.ropensci.org/melt/reference/getOptim.md)

## Examples

``` r
data("mtcars")
fit <- el_lm(mpg ~ ., data = mtcars)
sigTests(fit)
#> $statistic
#> (Intercept)         cyl        disp          hp        drat          wt 
#> 442.0394887   0.2334334 409.8798759 420.7490737 405.1301030 439.0974196 
#>        qsec          vs          am        gear        carb 
#> 442.4803698   0.4249416  26.6281283 401.7291427   0.5095781 
#> 
#> $iterations
#> (Intercept)         cyl        disp          hp        drat          wt 
#>           0          36           0           0           0           0 
#>        qsec          vs          am        gear        carb 
#>           0          36         200           0         115 
#> 
#> $convergence
#> (Intercept)         cyl        disp          hp        drat          wt 
#>       FALSE        TRUE       FALSE       FALSE       FALSE       FALSE 
#>        qsec          vs          am        gear        carb 
#>       FALSE        TRUE       FALSE       FALSE        TRUE 
#> 
```
