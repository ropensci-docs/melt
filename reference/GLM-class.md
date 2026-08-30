# GLM class

S4 class for generalized linear models. It inherits from
[LM](https://docs.ropensci.org/melt/reference/LM-class.md) class.

## Details

The overall test involves a constrained optimization problem. All the
parameters except for the intercept are constrained to zero. The `optim`
slot contains the results. When there is no intercept, all parameters
are set to zero, and the results need to be understood in terms of
[EL](https://docs.ropensci.org/melt/reference/EL-class.md) class since
no constrained optimization is involved. Once the solution is found, the
log probabilities (`logp`) and the (constrained) empirical likelihood
values (`logl`, `loglr`, `statistic`) readily follow, along with the
degrees of freedom (`df`) and the \\p\\-value (`pval`). The significance
tests for each parameter also involve constrained optimization problems
where only one parameter is constrained to zero. The `sigTests` slot
contains the results.

## Slots

- `family`:

  A [`family`](https://rdrr.io/r/stats/family.html) object used.

- `dispersion`:

  A single numeric for the estimated dispersion parameter.

- `sigTests`:

  A list of the following results of significance tests:

  - `statistic` A numeric vector of minus twice the (constrained)
    empirical log-likelihood ratios with asymptotic chi-square
    distributions.

  - `iterations` An integer vector for the number of iterations
    performed for each parameter.

  - `convergence` A logical vector for the convergence status of each
    parameter.

  - `cstr` A single logical for whether constrained EL optimization is
    performed or not.

- `call`:

  A matched call.

- `terms`:

  A [`terms`](https://rdrr.io/r/stats/terms.html) object used.

- `misc`:

  A list of various outputs obtained from the model fitting process.
  They are used in other generics and methods.

- `optim`:

  A list of the following optimization results:

  - `par` A numeric vector of the solution to the (constrained)
    optimization problem.

  - `lambda` A numeric vector of the Lagrange multipliers of the dual
    problem corresponding to `par`.

  - `iterations` A single integer for the number of iterations
    performed.

  - `convergence` A single logical for the convergence status.

- `logp`:

  A numeric vector of the log probabilities of the (constrained)
  empirical likelihood.

- `logl`:

  A single numeric of the (constrained) empirical log-likelihood.

- `loglr`:

  A single numeric of the (constrained) empirical log-likelihood ratio.

- `statistic`:

  A single numeric of minus twice the (constrained) empirical
  log-likelihood ratio with an asymptotic chi-square distribution.

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
showClass("GLM")
#> Class "GLM" [package "melt"]
#> 
#> Slots:
#>                                                                        
#> Name:        family   dispersion     sigTests         call        terms
#> Class:       family      numeric          ANY         call        terms
#>                                                                        
#> Name:          misc        optim         logp         logl        loglr
#> Class:         list         list      numeric      numeric      numeric
#>                                                                        
#> Name:     statistic           df         pval         nobs         npar
#> Class:      numeric      integer      numeric      integer      integer
#>                                                                        
#> Name:       weights coefficients       method         data      control
#> Class:      numeric      numeric    character          ANY    ControlEL
#> 
#> Extends: 
#> Class "LM", directly
#> Class "CEL", by class "LM", distance 2
#> Class "EL", by class "LM", distance 3
#> 
#> Known Subclasses: "QGLM"
```
