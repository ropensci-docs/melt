# SD class

S4 class for standard deviation. It inherits from
[EL](https://docs.ropensci.org/melt/reference/EL-class.md) class.

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

- `logp`:

  A numeric vector of the log probabilities of the empirical likelihood.

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

- `weights`:

  A numeric vector of the re-scaled weights used for the model fitting.

- `coefficients`:

  A numeric vector of the maximum empirical likelihood estimates of the
  parameters.

- `method`:

  A single character for the method dispatch in internal functions.

- `data`:

  A numeric matrix of the data for the model fitting.

- `control`:

  An object of class
  [ControlEL](https://docs.ropensci.org/melt/reference/ControlEL-class.md)
  constructed by
  [`el_control()`](https://docs.ropensci.org/melt/reference/el_control.md).

## Examples

``` r
showClass("SD")
#> Class "SD" [package "melt"]
#> 
#> Slots:
#>                                                                        
#> Name:         optim         logp         logl        loglr    statistic
#> Class:         list      numeric      numeric      numeric      numeric
#>                                                                        
#> Name:            df         pval         nobs         npar      weights
#> Class:      integer      numeric      integer      integer      numeric
#>                                                           
#> Name:  coefficients       method         data      control
#> Class:      numeric    character          ANY    ControlEL
#> 
#> Extends: "EL"
```
