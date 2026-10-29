# CEL class

S4 class for constrained empirical likelihood. It inherits from
[EL](https://docs.ropensci.org/melt/reference/EL-class.md) class. Note
that the `optim` slot has constrained optimization results with respect
to the parameters, not the Lagrange multiplier.

## Details

Let \\l(\theta)\\ denote minus twice the empirical log-likelihood ratio
function. We consider a linear hypothesis of the form \$\$L\theta =
r,\$\$ where the left-hand-side \\L\\ is a \\q\\ by \\p\\ matrix and the
right-hand-side \\r\\ is a \\q\\-dimensional vector. Under some
regularity conditions, \\l(\theta)\\ converges in distribution to
\\\chi^2_q\\ under the constraint of hypothesis, i.e.,
\$\$\min\_{\theta: L\theta = r} l(\theta) \to_d \chi^2_q .\$\$

Minimization of \\l(\theta)\\ with respect to \\\theta\\ is
computationally expensive since it implicitly involves the evaluation
step as described in
[EL](https://docs.ropensci.org/melt/reference/EL-class.md). Further,
depending on the form of \\g(X_i, \theta)\\ and the constraint, the
optimization problem can be nonconvex and have multiple local minima.
For this reason, the package melt only considers linear hypotheses and
performs local minimization of \\l(\theta)\\ using projected gradient
descent method. With the orthogonal projection matrix \\P\\ and a step
size \\\gamma\\, the algorithm updates \\\theta\\ as \$\$\theta^{(k +
1)} \leftarrow \theta^{(k)} - \gamma P \nabla l(\theta^{(k)}),\$\$ where
\\\nabla l(\theta^{(k)})\\ denotes the gradient of \\l\\ at
\\\theta^{(k)}\\. The first order optimality condition is \\P \nabla
l(\theta) = 0\\, which is used as the stopping criterion.

## Slots

- `optim`:

  A list of the following optimization results:

  - `par` A numeric vector of the solution to the constrained
    optimization problem.

  - `lambda` A numeric vector of the Lagrange multipliers of the dual
    problem corresponding to `par`.

  - `iterations` A single integer for the number of iterations
    performed.

  - `convergence` A single logical for the convergence status.

  - `cstr` A single logical for whether constrained EL optimization is
    performed or not.

- `logp`:

  A numeric vector of the log probabilities of the constrained empirical
  likelihood.

- `logl`:

  A single numeric of the constrained empirical log-likelihood.

- `loglr`:

  A single numeric of the constrained empirical log-likelihood ratio.

- `statistic`:

  A single numeric of minus twice the constrained empirical
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

## References

Adimari G, Guolo A (2010). “A Note on the Asymptotic Behaviour of
Empirical Likelihood Statistics.” *Statistical Methods & Applications*,
**19**(4), 463–476.
[doi:10.1007/s10260-010-0137-9](https://doi.org/10.1007/s10260-010-0137-9)
.

Qin J, Lawless J (1995). “Estimating Equations, Empirical Likelihood and
Constraints on Parameters.” *Canadian Journal of Statistics*, **23**(2),
145–159. [doi:10.2307/3315441](https://doi.org/10.2307/3315441) .

## Examples

``` r
showClass("CEL")
#> Class "CEL" [package "melt"]
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
#> 
#> Known Subclasses: 
#> Class "LM", directly
#> Class "GLM", by class "LM", distance 2
#> Class "QGLM", by class "GLM", distance 3
```
