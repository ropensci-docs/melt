# EL class

S4 class for empirical likelihood.

## Details

Let \\X_i\\ be independent and identically distributed \\p\\-dimensional
random variable from an unknown distribution \\P\\ for \\i = 1, \dots,
n\\. We assume that \\P\\ has a positive definite covariance matrix. For
a parameter of interest \\\theta(F) \in {\rm{I\\R}}^p\\, consider a
\\p\\-dimensional smooth estimating function \\g(X_i, \theta)\\ with a
moment condition \$\$\textrm{E}\[g(X_i, \theta)\] = 0.\$\$ We assume
that there exists an unique \\\theta_0\\ that solves the above equation.
Given a value of \\\theta\\, the (profile) empirical likelihood ratio is
defined by \$\$R(\theta) = \max\_{p_i}\left\\\prod\_{i = 1}^n np_i :
\sum\_{i = 1}^n p_i g(X_i, \theta) = 0, p_i \geq 0, \sum\_{i = 1}^n p_i
= 1 \right\\.\$\$ The Lagrange multiplier \\\lambda \equiv
\lambda(\theta)\\ of the dual problem leads to \$\$p_i =
\frac{1}{n}\frac{1}{1 + \lambda^\top g(X_i, \theta)},\$\$ where
\\\lambda\\ solves \$\$\frac{1}{n}\sum\_{i = 1}^n \frac{g(X_i, \theta)}
{1 + \lambda^\top g(X_i, \theta)} = 0.\$\$ Then the empirical
log-likelihood ratio is given by \$\$\log R(\theta) = -\sum\_{i = 1}^n
\log(1 + \lambda^\top g(X_i, \theta)).\$\$ This problem can be
efficiently solved by the Newton-Raphson method when the zero vector is
contained in the interior of the convex hull of \\\\g(X_i, \theta)\\\_{i
= 1}^n\\.

It is known that \\-2\log R(\theta_0)\\ converges in distribution to
\\\chi^2_p\\, where \\\chi^2_p\\ has a chi-square distribution with
\\p\\ degrees of freedom. See the references below for more details.

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

## References

Owen A (2001). *Empirical Likelihood*. Chapman & Hall/CRC.
[doi:10.1201/9781420036152](https://doi.org/10.1201/9781420036152) .

Qin J, Lawless J (1994). “Empirical Likelihood and General Estimating
Equations.” *The Annals of Statistics*, **22**(1), 300–325.
[doi:10.1214/aos/1176325370](https://doi.org/10.1214/aos/1176325370) .

## Examples

``` r
showClass("EL")
#> Class "EL" [package "melt"]
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
#> Known Subclasses: 
#> Class "CEL", directly
#> Class "SD", directly
#> Class "LM", by class "CEL", distance 2
#> Class "GLM", by class "CEL", distance 3
#> Class "QGLM", by class "CEL", distance 4
```
