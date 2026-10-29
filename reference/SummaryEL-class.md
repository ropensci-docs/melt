# SummaryEL class

S4 class for a summary of
[EL](https://docs.ropensci.org/melt/reference/EL-class.md) objects.

## Slots

- `optim`:

  A list of the following optimization results:

  - `par` A numeric vector of the specified parameters.

  - `lambda` A numeric vector of the Lagrange multipliers of the dual
    problem corresponding to `par`.

  - `iterations` A single integer for the number of iterations
    performed.

  - `convergence` A single logical for the convergence status.

  - `cstr` A single logical for whether constrained EL optimization is
    performed or not.

- `logl`:

  A single numeric of the empirical log-likelihood.

- `loglr`:

  A single numeric of the empirical log-likelihood ratio.

- `statistic`:

  A single numeric of minus twice the empirical log-likelihood ratio
  with an asymptotic chi-square distribution.

- `df`:

  A single integer for the degrees of freedom of the statistic.

- `pval`:

  A single numeric for the \\p\\-value of the statistic.

- `nobs`:

  A single integer for the number of observations.

- `npar`:

  A single integer for the number of parameters.

- `weighted`:

  A single logical for whether the data are weighted or not.

- `coefficients`:

  A numeric vector of the maximum empirical likelihood estimates of the
  parameters.

- `method`:

  A single character for the method dispatch in internal functions.

- `control`:

  An object of class
  [ControlEL](https://docs.ropensci.org/melt/reference/ControlEL-class.md)
  constructed by
  [`el_control()`](https://docs.ropensci.org/melt/reference/el_control.md).

## Examples

``` r
showClass("SummaryEL")
#> Class "SummaryEL" [package "melt"]
#> 
#> Slots:
#>                                                                        
#> Name:         optim         logl        loglr    statistic           df
#> Class:         list      numeric      numeric      numeric      integer
#>                                                                        
#> Name:          pval         nobs         npar     weighted coefficients
#> Class:      numeric      integer      integer      logical      numeric
#>                                 
#> Name:        method      control
#> Class:    character    ControlEL
```
