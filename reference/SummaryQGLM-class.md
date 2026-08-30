# SummaryQGLM class

S4 class for a summary of
[QGLM](https://docs.ropensci.org/melt/reference/QGLM-class.md) objects.
It inherits from
[SummaryGLM](https://docs.ropensci.org/melt/reference/SummaryGLM-class.md)
class.

## Slots

- `family`:

  A [`family`](https://rdrr.io/r/stats/family.html) object used.

- `dispersion`:

  A single numeric for the estimated dispersion parameter.

- `coefficients`:

  A numeric matrix of the results of significance tests.

- `intercept`:

  A single logical for whether the given model has an intercept term or
  not.

- `na.action`:

  Information returned by
  [`model.frame`](https://rdrr.io/r/stats/model.frame.html) on the
  special handling of `NA`s.

- `call`:

  A matched call.

- `terms`:

  A [`terms`](https://rdrr.io/r/stats/terms.html) object used.

- `aliased`:

  A named logical vector showing if the original coefficients are
  aliased.

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

  A single numeric of the empirical log-likelihood.

- `loglr`:

  A single numeric of the empirical log-likelihood ratio.

- `statistic`:

  A single numeric of minus twice the (constrained) empirical
  log-likelihood ratio for the overall test.

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

- `method`:

  A single character for the method dispatch in internal functions.

- `control`:

  An object of class
  [ControlEL](https://docs.ropensci.org/melt/reference/ControlEL-class.md)
  constructed by
  [`el_control()`](https://docs.ropensci.org/melt/reference/el_control.md).

## Examples

``` r
showClass("SummaryQGLM")
#> Class "SummaryQGLM" [package "melt"]
#> 
#> Slots:
#>                                                                        
#> Name:        family   dispersion coefficients    intercept    na.action
#> Class:       family      numeric       matrix      logical          ANY
#>                                                                        
#> Name:          call        terms      aliased        optim         logl
#> Class:         call        terms      logical         list      numeric
#>                                                                        
#> Name:         loglr    statistic           df         pval         nobs
#> Class:      numeric      numeric      integer      numeric      integer
#>                                                           
#> Name:          npar     weighted       method      control
#> Class:      integer      logical    character    ControlEL
#> 
#> Extends: 
#> Class "SummaryGLM", directly
#> Class "SummaryLM", by class "SummaryGLM", distance 2
```
