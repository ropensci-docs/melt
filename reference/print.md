# Print methods

Provides print methods for objects.

## Usage

``` r
# S4 method for class 'EL'
print(x, digits = max(3L, getOption("digits") - 3L), ...)

# S4 method for class 'ELMT'
print(x, digits = max(3L, getOption("digits") - 3L), ...)

# S4 method for class 'ELT'
print(x, digits = max(3L, getOption("digits") - 3L), ...)

# S4 method for class 'LM'
print(x, digits = max(3L, getOption("digits") - 3L), ...)

# S4 method for class 'SummaryEL'
print(x, digits = max(3L, getOption("digits") - 3L), ...)

# S4 method for class 'SummaryELMT'
print(
  x,
  digits = max(3L, getOption("digits") - 3L),
  signif.stars = getOption("show.signif.stars"),
  ...
)

# S4 method for class 'SummaryELT'
print(x, digits = max(3L, getOption("digits") - 3L), ...)

# S4 method for class 'SummaryGLM'
print(
  x,
  digits = max(3L, getOption("digits") - 3L),
  signif.stars = getOption("show.signif.stars"),
  ...
)

# S4 method for class 'SummaryLM'
print(
  x,
  digits = max(3L, getOption("digits") - 3L),
  signif.stars = getOption("show.signif.stars"),
  ...
)
```

## Arguments

- x:

  An object to be printed.

- ...:

  Further arguments passed to methods.

- digits:

  A single integer for the number of significant digits to be passed to
  [`format()`](https://rdrr.io/r/base/format.html).

- signif.stars:

  A single logical. If `TRUE`, ‘significance stars’ are printed for each
  parameter.

## Value

The argument `x` (invisibly).

## See also

[EL](https://docs.ropensci.org/melt/reference/EL-class.md),
[ELMT](https://docs.ropensci.org/melt/reference/ELMT-class.md),
[ELT](https://docs.ropensci.org/melt/reference/ELT-class.md),
[LM](https://docs.ropensci.org/melt/reference/LM-class.md)

## Examples

``` r
data("precip")
fit <- el_mean(precip, par = 40)
print(fit)
#> 
#>  Empirical Likelihood
#> 
#> Model: mean 
#> 
#> Maximum EL estimates:
#> [1] 34.89
#> 
#> Chisq: 9.957, df: 1, Pr(>Chisq): 0.001602
#> EL evaluation: converged 
#> 
```
