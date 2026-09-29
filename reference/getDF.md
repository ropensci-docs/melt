# Degrees of freedom

Extracts the degrees of freedom from a model.

## Usage

``` r
# S4 method for class 'EL'
getDF(object)

# S4 method for class 'ELMT'
getDF(object)

# S4 method for class 'ELT'
getDF(object)

# S4 method for class 'SummaryEL'
getDF(object)

# S4 method for class 'SummaryELMT'
getDF(object)

# S4 method for class 'SummaryLM'
getDF(object)
```

## Arguments

- object:

  An object that contains the degrees of freedom.

## Value

An integer vector.

## Methods (by class)

- `getDF(EL)`: Extracts the degrees of freedom.

- `getDF(ELMT)`: Extracts the vector of marginal degrees of freedom.

- `getDF(ELT)`: Extracts the (chi-square) degrees of freedom.

- `getDF(SummaryEL)`: Extracts the degrees of freedom.

- `getDF(SummaryELMT)`: Extracts the vector of marginal degrees of
  freedom.

- `getDF(SummaryLM)`: Extracts the degrees of freedom.

## See also

[EL](https://docs.ropensci.org/melt/reference/EL-class.md),
[ELMT](https://docs.ropensci.org/melt/reference/ELMT-class.md),
[ELT](https://docs.ropensci.org/melt/reference/ELT-class.md)

## Examples

``` r
data("faithful")
fit <- el_mean(faithful, par = c(3.5, 70))
getDF(fit)
#> [1] 2
```
