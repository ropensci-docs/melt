# Chi-square statistic

Extracts the chi-square statistic from a model.

## Usage

``` r
# S4 method for class 'EL'
chisq(object, ...)

# S4 method for class 'ELMT'
chisq(object, ...)

# S4 method for class 'ELT'
chisq(object, ...)

# S4 method for class 'SummaryEL'
chisq(object, ...)

# S4 method for class 'SummaryELMT'
chisq(object, ...)

# S4 method for class 'SummaryELT'
chisq(object, ...)

# S4 method for class 'SummaryLM'
chisq(object, ...)
```

## Arguments

- object:

  An object that contains the chi-square statistic.

- ...:

  Further arguments passed to methods.

## Value

The form of the value returned by `chisq()` depends on the class of its
argument.

## Methods (by class)

- `chisq(EL)`: Extracts the chi-square statistic.

- `chisq(ELMT)`: Extracts the vector of chi-square statistics.

- `chisq(ELT)`: Extracts the chi-square statistic.

- `chisq(SummaryEL)`: Extracts the chi-square statistic.

- `chisq(SummaryELMT)`: Extracts the vector of chi-square statistics.

- `chisq(SummaryELT)`: Extracts the chi-square statistic.

- `chisq(SummaryLM)`: Extracts the chi-square statistic for the overall
  test of the model.

## See also

[EL](https://docs.ropensci.org/melt/reference/EL-class.md),
[ELMT](https://docs.ropensci.org/melt/reference/ELMT-class.md),
[ELT](https://docs.ropensci.org/melt/reference/ELT-class.md),
[`pVal()`](https://docs.ropensci.org/melt/reference/pVal.md)

## Examples

``` r
data("precip")
fit <- el_mean(precip, par = 40)
chisq(fit)
#> [1] 9.957478
```
