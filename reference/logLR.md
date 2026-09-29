# Empirical log-likelihood ratio

Extracts the empirical log-likelihood ratio from a model.

## Usage

``` r
# S4 method for class 'EL'
logLR(object, ...)

# S4 method for class 'ELT'
logLR(object, ...)

# S4 method for class 'SummaryEL'
logLR(object, ...)

# S4 method for class 'SummaryELT'
logLR(object, ...)

# S4 method for class 'SummaryLM'
logLR(object, ...)
```

## Arguments

- object:

  An object that contains the empirical log-likelihood ratio.

- ...:

  Further arguments passed to methods.

## Value

A single numeric.

## References

Baggerly KA (1998). “Empirical Likelihood as a Goodness-of-Fit Measure.”
*Biometrika*, **85**(3), 535–547.
[doi:10.1093/biomet/85.3.535](https://doi.org/10.1093/biomet/85.3.535) .

## See also

[EL](https://docs.ropensci.org/melt/reference/EL-class.md),
[ELT](https://docs.ropensci.org/melt/reference/ELT-class.md)

## Examples

``` r
data("precip")
fit <- el_mean(precip, par = 40)
logLR(fit)
#> [1] -4.978739
```
