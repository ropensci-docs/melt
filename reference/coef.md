# Model coefficients

Extracts the maximum empirical likelihood estimates from a model.

## Usage

``` r
# S4 method for class 'EL'
coef(object, ...)

# S4 method for class 'ELMT'
coef(object, ...)

# S4 method for class 'SummaryEL'
coef(object, ...)

# S4 method for class 'SummaryLM'
coef(object, ...)
```

## Arguments

- object:

  An object that contains the maximum empirical likelihood estimates.

- ...:

  Further arguments passed to methods.

## Value

The form of the value returned by `coef()` depends on the class of its
argument.

## Methods (by class)

- `coef(EL)`: Extracts the numeric vector of the maximum empirical
  likelihood estimates.

- `coef(ELMT)`: Extracts the list of numeric vectors of the maximum
  empirical likelihood estimates. Each element of the list corresponds
  to a distinct hypothesis.

- `coef(SummaryEL)`: Extracts the numeric vector of the maximum
  empirical likelihood estimates.

- `coef(SummaryLM)`: Extracts a matrix with the results of significance
  tests.

## See also

[EL](https://docs.ropensci.org/melt/reference/EL-class.md),
[ELMT](https://docs.ropensci.org/melt/reference/ELMT-class.md)

## Examples

``` r
data("mtcars")
fit <- el_lm(mpg ~ wt, data = mtcars)
coef(fit)
#> (Intercept)          wt 
#>   37.285126   -5.344472 
```
