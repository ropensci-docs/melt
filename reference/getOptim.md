# Optimization results

Extracts the optimization results from a model.

## Usage

``` r
# S4 method for class 'EL'
getOptim(object, ...)

# S4 method for class 'ELT'
getOptim(object, ...)

# S4 method for class 'SummaryEL'
getOptim(object, ...)

# S4 method for class 'SummaryELT'
getOptim(object, ...)

# S4 method for class 'SummaryLM'
getOptim(object, ...)
```

## Arguments

- object:

  An object that contains the optimization results.

- ...:

  Further arguments passed to methods.

## Value

A list with the following optimization results:

- `par` A numeric vector of the parameter value. See the documentation
  of [EL](https://docs.ropensci.org/melt/reference/EL-class.md) and
  [CEL](https://docs.ropensci.org/melt/reference/CEL-class.md).

- `lambda` A numeric vector of the Lagrange multipliers.

- `iterations` A single integer for the number of iterations performed.

- `convergence` A single logical for the convergence status.

## See also

[EL](https://docs.ropensci.org/melt/reference/EL-class.md),
[ELT](https://docs.ropensci.org/melt/reference/ELT-class.md),
[`sigTests()`](https://docs.ropensci.org/melt/reference/sigTests.md)

## Examples

``` r
data("precip")
fit <- el_mean(precip, par = 40)
getOptim(fit)
#> $par
#> [1] 40
#> 
#> $lambda
#> [1] -0.0267627
#> 
#> $iterations
#> [1] 5
#> 
#> $convergence
#> [1] TRUE
#> 
#> $cstr
#> [1] FALSE
#> 
```
