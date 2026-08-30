# Convergence check

Extracts the convergence status from a model.

## Usage

``` r
# S4 method for class 'CEL'
conv(object, ...)

# S4 method for class 'EL'
conv(object, ...)

# S4 method for class 'ELT'
conv(object, ...)

# S4 method for class 'SummaryEL'
conv(object, ...)

# S4 method for class 'SummaryELT'
conv(object, ...)

# S4 method for class 'SummaryLM'
conv(object, ...)
```

## Arguments

- object:

  An object that contains the convergence status.

- ...:

  Further arguments passed to methods.

## Value

A single logical.

## Methods (by class)

- `conv(CEL)`: Extracts the convergence status of the model with respect
  to the parameter.

- `conv(EL)`: Extracts the convergence status of the model with respect
  to the Lagrange multiplier.

- `conv(ELT)`: Extracts the convergence status of the test with respect
  to the parameter (or the Lagrange multiplier if the argument `lhs` is
  `NULL`).

- `conv(SummaryEL)`: Extracts the convergence status of the model with
  respect to the Lagrange multiplier.

- `conv(SummaryELT)`: Extracts the convergence status of the test with
  respect to the parameter (or the Lagrange multiplier if the argument
  `lhs` is `NULL`).

- `conv(SummaryLM)`: Extracts the convergence status of the model. See
  the documentation of
  [EL](https://docs.ropensci.org/melt/reference/EL-class.md) and
  [CEL](https://docs.ropensci.org/melt/reference/CEL-class.md).

## See also

[CEL](https://docs.ropensci.org/melt/reference/CEL-class.md),
[EL](https://docs.ropensci.org/melt/reference/EL-class.md),
[ELT](https://docs.ropensci.org/melt/reference/ELT-class.md),
[`getOptim()`](https://docs.ropensci.org/melt/reference/getOptim.md)

## Examples

``` r
## Convergence check for the overall model test
data("mtcars")
fit <- el_lm(mpg ~ ., data = mtcars)
conv(fit)
#> [1] TRUE
```
