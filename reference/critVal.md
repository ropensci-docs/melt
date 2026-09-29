# Critical value

Extracts the critical value from a model.

## Usage

``` r
# S4 method for class 'ELMT'
critVal(object, ...)

# S4 method for class 'ELT'
critVal(object, ...)

# S4 method for class 'SummaryELMT'
critVal(object, ...)

# S4 method for class 'SummaryELT'
critVal(object, ...)
```

## Arguments

- object:

  An object that contains the critical value.

- ...:

  Further arguments passed to methods.

## Value

A single numeric.

## See also

[ELMT](https://docs.ropensci.org/melt/reference/ELMT-class.md),
[ELT](https://docs.ropensci.org/melt/reference/ELT-class.md)

## Examples

``` r
## F-calibrated critical value
data("precip")
fit <- el_mean(precip, 30)
elt <- elt(fit, rhs = 34, calibrate = "f")
critVal(elt)
#> [1] 3.979807
```
