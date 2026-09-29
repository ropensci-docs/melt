# SummaryELT class

S4 class for a summary of
[ELT](https://docs.ropensci.org/melt/reference/ELT-class.md) objects.

## Slots

- `optim`:

  A list of the following optimization results:

  - `par` A numeric vector of the solution to the (constrained)
    optimization problem.

  - `lambda` A numeric vector of the Lagrange multipliers of the dual
    problem corresponding to `par`.

  - `iterations` A single integer for the number of iterations
    performed.

  - `convergence` A single logical for the convergence status.

  - `cstr` A single logical for whether constrained EL optimization is
    performed or not.

- `logl`:

  A single numeric of the (constrained) empirical log-likelihood.

- `loglr`:

  A single numeric of the (constrained) empirical log-likelihood ratio.

- `statistic`:

  A single numeric of minus twice the (constrained) empirical
  log-likelihood ratio with an asymptotic chi-square distribution.

- `df`:

  A single integer for the chi-square degrees of freedom of the
  statistic.

- `pval`:

  A single numeric for the (calibrated) \\p\\-value of the statistic.

- `cv`:

  A single numeric for the critical value.

- `rhs`:

  A numeric vector for the right-hand side of the hypothesis.

- `lhs`:

  A numeric matrix for the left-hand side of the hypothesis.

- `alpha`:

  A single numeric for the significance level.

- `calibrate`:

  A single character for the calibration method used.

- `control`:

  An object of class
  [ControlEL](https://docs.ropensci.org/melt/reference/ControlEL-class.md)
  constructed by
  [`el_control()`](https://docs.ropensci.org/melt/reference/el_control.md).

## Examples

``` r
showClass("SummaryELT")
#> Class "SummaryELT" [package "melt"]
#> 
#> Slots:
#>                                                                             
#> Name:      optim      logl     loglr statistic        df      pval        cv
#> Class:      list   numeric   numeric   numeric   integer   numeric   numeric
#>                                                         
#> Name:        rhs       lhs     alpha calibrate   control
#> Class:   numeric    matrix   numeric character ControlEL
```
