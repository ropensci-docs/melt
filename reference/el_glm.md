# Empirical likelihood for generalized linear models

Fits a generalized linear model with empirical likelihood.

## Usage

``` r
el_glm(
  formula,
  family = gaussian,
  data,
  weights = NULL,
  na.action,
  start = NULL,
  etastart = NULL,
  mustart = NULL,
  offset,
  control = el_control(),
  ...
)
```

## Arguments

- formula:

  An object of class [`formula`](https://rdrr.io/r/stats/formula.html)
  (or one that can be coerced to that class): a symbolic description of
  the model to be fitted.

- family:

  A description of the error distribution and link function to be used
  in the model. Only the result of a call to a family function is
  supported. See ‘Details’.

- data:

  An optional data frame, list or environment (or object coercible by
  [`as.data.frame()`](https://rdrr.io/r/base/as.data.frame.html) to a
  data frame) containing the variables in the formula. If not found in
  data, the variables are taken from `environment(formula)`.

- weights:

  An optional numeric vector of weights to be used in the fitting
  process. Defaults to `NULL`, corresponding to identical weights. If
  non-`NULL`, weighted empirical likelihood is computed.

- na.action:

  A function which indicates what should happen when the data contain
  `NA`s. The default is set by the `na.action` setting of
  [`options`](https://rdrr.io/r/base/options.html), and is `na.fail` if
  that is unset.

- start:

  Starting values for the parameters in the linear predictor. Defaults
  to `NULL` and is passed to
  [`glm.fit()`](https://rdrr.io/r/stats/glm.html).

- etastart:

  Starting values for the linear predictor. Defaults to `NULL` and is
  passed to [`glm.fit()`](https://rdrr.io/r/stats/glm.html).

- mustart:

  Starting values for the vector of means. Defaults to `NULL` and is
  passed to [`glm.fit()`](https://rdrr.io/r/stats/glm.html).

- offset:

  An optional expression for specifying an *a priori* known component to
  be included in the linear predictor during fitting. This should be
  `NULL` or a numeric vector or matrix of extents matching those of the
  response. One or more [`offset`](https://rdrr.io/r/stats/offset.html)
  terms can be included in the formula instead or as well, and if more
  than one are specified their sum is used.

- control:

  An object of class
  [ControlEL](https://docs.ropensci.org/melt/reference/ControlEL-class.md)
  constructed by
  [`el_control()`](https://docs.ropensci.org/melt/reference/el_control.md).

- ...:

  Additional arguments to be passed to
  [`glm.control()`](https://rdrr.io/r/stats/glm.control.html).

## Value

An object of class of
[GLM](https://docs.ropensci.org/melt/reference/GLM-class.md).

## Details

Suppose that we observe \\n\\ independent random variables \\{Z_i}
\equiv {(X_i, Y_i)}\\ from a common distribution, where \\X_i\\ is the
\\p\\-dimensional covariate (including the intercept if any) and \\Y_i\\
is the response. A generalized linear model specifies that
\\{\textrm{E}(Y_i \| X_i)} = {\mu_i}\\, \\{G(\mu_i)} = {X_i^\top
\theta}\\, and \\{\textrm{Var}(Y_i \| X_i)} = {\phi V(\mu_i)}\\, where
\\\theta = (\theta_0, \dots, \theta\_{p-1})\\ is an unknown
\\p\\-dimensional parameter, \\\phi\\ is an optional dispersion
parameter, \\G\\ is a known smooth link function, and \\V\\ is a known
variance function.

With \\H\\ denoting the inverse link function, define the quasi-score
\$\${g_1(Z_i, \theta)} = \left\\ H^\prime(X_i^\top \theta) \left(Y_i -
H(X_i^\top \theta)\right) / \left(\phi V\left(H(X_i^\top
\theta)\right)\right) \right\\ X_i.\$\$ Then we have the estimating
equations \\\sum\_{i = 1}^n g_1(Z_i, \theta) = 0\\. When \\\phi\\ is
known, the (profile) empirical likelihood ratio for a given \\\theta\\
is defined by \$\$R_1(\theta) = \max\_{p_i}\left\\\prod\_{i = 1}^n np_i
: \sum\_{i = 1}^n p_i g_1(Z_i, \theta) = 0,\\ p_i \geq 0,\\ \sum\_{i =
1}^n p_i = 1 \right\\.\$\$ With unknown \\\phi\\, we introduce another
estimating function based on the squared residuals. Let \\{\eta} =
{(\theta, \phi)}\\ and \$\${g_2(Z_i, \eta)} = \left(Y_i - H(X_i^\top
\theta)\right)^2 / \left(\phi^2 V\left(H(X_i^\top
\theta)\right)\right) - 1 / \phi.\$\$ Now the empirical likelihood ratio
is defined by \$\$R_2(\eta) = \max\_{p_i}\left\\\prod\_{i = 1}^n np_i :
\sum\_{i = 1}^n p_i g_1(Z_i, \eta) = 0,\\ \sum\_{i = 1}^n p_i g_2(Z_i,
\eta) = 0,\\ p_i \geq 0,\\ \sum\_{i = 1}^n p_i = 1 \right\\.\$\$
`el_glm()` first computes the parameter estimates by calling
[`glm.fit()`](https://rdrr.io/r/stats/glm.html) (with `...` if any) with
the `model.frame` and `model.matrix` obtained from the `formula`. Note
that the maximum empirical likelihood estimator is the same as the the
quasi-maximum likelihood estimator in our model. Next, it tests
hypotheses based on asymptotic chi-square distributions of the empirical
likelihood ratio statistics. Included in the tests are overall test with
\$\$H_0: \theta_1 = \theta_2 = \cdots = \theta\_{p-1} = 0,\$\$ and
significance tests for each parameter with \$\$H\_{0j}: \theta_j = 0,\\
j = 0, \dots, p-1.\$\$

The available families and link functions are as follows:

- `gaussian`: `"identity"`, `"log"`, and `"inverse"`.

- `binomial`: `"logit"`, `"probit"`, and `"log"`.

- `poisson`: `"log"`, `"identity"`, and `"sqrt"`.

- `quasipoisson`: `"log"`, `"identity"`, and `"sqrt"`.

## References

Chen SX, Cui H (2003). “An Extended Empirical Likelihood for Generalized
Linear Models.” *Statistica Sinica*, **13**(1), 69–81.

Kolaczyk ED (1994). “Empirical Likelihood for Generalized Linear
Models.” *Statistica Sinica*, **4**(1), 199–218.

## See also

[EL](https://docs.ropensci.org/melt/reference/EL-class.md),
[GLM](https://docs.ropensci.org/melt/reference/GLM-class.md),
[`el_lm()`](https://docs.ropensci.org/melt/reference/el_lm.md),
[`elt()`](https://docs.ropensci.org/melt/reference/elt.md),
[`el_control()`](https://docs.ropensci.org/melt/reference/el_control.md)

## Examples

``` r
data("warpbreaks")
fit <- el_glm(wool ~ .,
  family = binomial, data = warpbreaks, weights = NULL, na.action = na.omit,
  start = NULL, etastart = NULL, mustart = NULL, offset = NULL
)
summary(fit)
#> 
#>  Empirical Likelihood
#> 
#> Model: glm (binomial family with logit link)
#> 
#> Call:
#> el_glm(formula = wool ~ ., family = binomial, data = warpbreaks, 
#>     weights = NULL, na.action = na.omit, start = NULL, etastart = NULL, 
#>     mustart = NULL, offset = NULL)
#> 
#> Number of observations: 54 
#> Number of parameters: 4 
#> 
#> Parameter values under the null hypothesis:
#> (Intercept)      breaks    tensionM    tensionH 
#>   6.337e-08   0.000e+00   0.000e+00   0.000e+00 
#> 
#> Lagrange multipliers:
#> [1]  1.81250 -0.05261 -0.41072 -0.71437
#> 
#> Maximum EL estimates:
#> (Intercept)      breaks    tensionM    tensionH 
#>     1.67965    -0.04677    -0.44662    -0.67062 
#> 
#> logL: -217.4 , logLR: -1.97 
#> Chisq: 3.94, df: 3, Pr(>Chisq): 0.268
#> Constrained EL: converged 
#> 
#> Coefficients:
#>             Estimate Chisq Pr(>Chisq)  
#> (Intercept)  1.67965 6.226     0.0126 *
#> breaks      -0.04677 3.941     0.0471 *
#> tensionM    -0.44662 0.568     0.4511  
#> tensionH    -0.67062 1.628     0.2020  
#> ---
#> Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1
#> 
#> Dispersion for binomial family: 1
#> 
```
