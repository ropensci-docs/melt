# \\p\\-value

Extracts the \\p\\-value from a model.

## Usage

``` r
# S4 method for class 'EL'
pVal(object, ...)

# S4 method for class 'ELMT'
pVal(object, ...)

# S4 method for class 'ELT'
pVal(object, ...)

# S4 method for class 'SummaryEL'
pVal(object, ...)

# S4 method for class 'SummaryELT'
pVal(object, ...)

# S4 method for class 'SummaryELMT'
pVal(object, ...)

# S4 method for class 'SummaryLM'
pVal(object, ...)
```

## Arguments

- object:

  An object that contains the \\p\\-value.

- ...:

  Further arguments passed to methods.

## Value

The form of the value returned by `pVal()` depends on the class of its
argument.

## Methods (by class)

- `pVal(EL)`: Extracts the \\p\\-value.

- `pVal(ELMT)`: Extracts the multiplicity adjusted \\p\\-values.

- `pVal(ELT)`: Extracts the \\p\\-value.

- `pVal(SummaryEL)`: Extracts the \\p\\-value.

- `pVal(SummaryELT)`: Extracts the \\p\\-value.

- `pVal(SummaryELMT)`: Extracts the multiplicity adjusted \\p\\-values.

- `pVal(SummaryLM)`: Extracts the \\p\\-value.

## See also

[EL](https://docs.ropensci.org/melt/reference/EL-class.md),
[ELMT](https://docs.ropensci.org/melt/reference/ELMT-class.md),
[ELT](https://docs.ropensci.org/melt/reference/ELT-class.md),
[`chisq()`](https://docs.ropensci.org/melt/reference/chisq.md)

## Examples

``` r
data("precip")
fit <- el_mean(precip, par = 40)
pVal(fit)
#> [1] 0.001601974
```
