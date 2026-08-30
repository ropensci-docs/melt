# ELMT class

S4 class for empirical likelihood multiple tests.

## Slots

- `estimates`:

  A list of numeric vectors of the estimates of the linear hypotheses.

- `statistic`:

  A numeric vector of minus twice the (constrained) empirical
  log-likelihood ratios with asymptotic chi-square distributions.

- `df`:

  An integer vector of the marginal degrees of freedom of the statistic.

- `pval`:

  A numeric vector for the multiplicity adjusted \\p\\-values.

- `cv`:

  A single numeric for the multiplicity adjusted critical value.

- `rhs`:

  A numeric vector for the right-hand sides of the hypotheses.

- `lhs`:

  A numeric matrix for the left-hand side of the hypotheses.

- `alpha`:

  A single numeric for the overall significance level.

- `calibrate`:

  A single character for the calibration method used.

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
showClass("ELMT")
#> Class "ELMT" [package "melt"]
#> 
#> Slots:
#>                                                                        
#> Name:     estimates    statistic           df         pval           cv
#> Class:         list      numeric      integer      numeric      numeric
#>                                                                        
#> Name:           rhs          lhs        alpha    calibrate      weights
#> Class:      numeric       matrix      numeric    character      numeric
#>                                                           
#> Name:  coefficients       method         data      control
#> Class:      numeric    character          ANY    ControlEL
```
