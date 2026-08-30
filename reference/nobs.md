# Number of observations in a model

Extracts the number of observations from a model.

## Usage

``` r
# S4 method for class 'EL'
nobs(object, ...)

# S4 method for class 'SummaryEL'
nobs(object, ...)

# S4 method for class 'SummaryLM'
nobs(object, ...)
```

## Arguments

- object:

  An object that contains the number of observations.

- ...:

  Further arguments passed to methods.

## Value

A single integer.

## See also

[EL](https://docs.ropensci.org/melt/reference/EL-class.md)

## Examples

``` r
data("precip")
fit <- el_mean(precip, par = 40)
nobs(fit)
#> [1] 70
```
