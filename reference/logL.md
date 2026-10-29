# Empirical log-likelihood

Extracts the empirical log-likelihood from a model.

## Usage

``` r
# S4 method for class 'EL'
logL(object, ...)

# S4 method for class 'ELT'
logL(object, ...)

# S4 method for class 'SummaryEL'
logL(object, ...)

# S4 method for class 'SummaryELT'
logL(object, ...)

# S4 method for class 'SummaryLM'
logL(object, ...)
```

## Arguments

- object:

  An object that contains the empirical log-likelihood.

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
logL(fit)
#> [1] -302.3734
```
