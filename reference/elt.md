# Empirical likelihood test

Tests a linear hypothesis with various calibration options.

## Usage

``` r
# S4 method for class 'EL'
elt(
  object,
  rhs = NULL,
  lhs = NULL,
  alpha = 0.05,
  calibrate = "chisq",
  control = NULL
)
```

## Arguments

- object:

  An object that inherits from
  [EL](https://docs.ropensci.org/melt/reference/EL-class.md).

- rhs:

  A numeric vector or a column matrix for the right-hand side of
  hypothesis, with as many entries as the rows in `lhs`. Defaults to
  `NULL`. See ‘Details’.

- lhs:

  A numeric matrix or a vector (treated as a row matrix) for the
  left-hand side of a hypothesis. Each row gives a linear combination of
  the parameters in `object`. The number of columns must be equal to the
  number of parameters. Or a character vector with a symbolic
  description of the hypothesis is allowed. Defaults to `NULL`. See
  ‘Details’.

- alpha:

  A single numeric for the significance level. Defaults to `0.05`.

- calibrate:

  A single character representing the calibration method. It is
  case-insensitive and must be one of `"ael"`, `"boot"`, `"chisq"`, or
  `"f"`. Defaults to `"chisq"`. See ‘Details’.

- control:

  An object of class
  [ControlEL](https://docs.ropensci.org/melt/reference/ControlEL-class.md)
  constructed by
  [`el_control()`](https://docs.ropensci.org/melt/reference/el_control.md).
  Defaults to `NULL` and inherits the `control` slot in `object`.

## Value

An object of class of
[ELT](https://docs.ropensci.org/melt/reference/ELT-class.md). If `lhs`
is non-`NULL`, the `optim` slot corresponds to that of
[CEL](https://docs.ropensci.org/melt/reference/CEL-class.md). Otherwise,
it corresponds to that of
[EL](https://docs.ropensci.org/melt/reference/EL-class.md).

## Details

`elt()` performs the constrained minimization of \\l(\theta)\\ described
in [CEL](https://docs.ropensci.org/melt/reference/CEL-class.md). `rhs`
and `lhs` cannot be both `NULL`. For non-`NULL` `lhs`, it is required
that `lhs` have full row rank \\q \leq p\\ and \\p\\ be equal to the
number of parameters in the `object`.

Depending on the specification of `rhs` and `lhs`, we have the following
three cases:

1.  If both `rhs` and `lhs` are non-`NULL`, the constrained minimization
    is performed with the right-hand side \\r\\ and the left-hand side
    \\L\\ as \$\$\inf\_{\theta: L\theta = r} l(\theta).\$\$

2.  If `rhs` is `NULL`, \\r\\ is set to the zero vector as
    \\\inf\_{\theta: L\theta = 0} l(\theta)\\.

3.  If `lhs` is `NULL`, \\L\\ is set to the identity matrix and the
    problem reduces to evaluating at \\r\\ as \\l(r)\\.

`calibrate` specifies the calibration method used. Four methods are
available: `"ael"` (adjusted empirical likelihood calibration), `"boot"`
(bootstrap calibration), `"chisq"` (chi-square calibration), and `"f"`
(\\F\\ calibration). When `lhs` is not `NULL`, only `"chisq"` is
available. `"f"` is applicable only to the mean parameter. The `an` slot
in `control` applies specifically to `"ael"`, while the `nthreads`,
`seed`, and `B` slots apply to `"boot"`.

## References

Adimari G, Guolo A (2010). “A Note on the Asymptotic Behaviour of
Empirical Likelihood Statistics.” *Statistical Methods & Applications*,
**19**(4), 463–476.
[doi:10.1007/s10260-010-0137-9](https://doi.org/10.1007/s10260-010-0137-9)
.

Chen J, Variyath AM, Abraham B (2008). “Adjusted Empirical Likelihood
and Its Properties.” *Journal of Computational and Graphical
Statistics*, **17**(2), 426–443.

Kim E, MacEachern SN, Peruggia M (2024). “melt: Multiple Empirical
Likelihood Tests in R.” *Journal of Statistical Software*, **108**(5),
1–33. [doi:10.18637/jss.v108.i05](https://doi.org/10.18637/jss.v108.i05)
.

Qin J, Lawless J (1995). “Estimating Equations, Empirical Likelihood and
Constraints on Parameters.” *Canadian Journal of Statistics*, **23**(2),
145–159. [doi:10.2307/3315441](https://doi.org/10.2307/3315441) .

## See also

[EL](https://docs.ropensci.org/melt/reference/EL-class.md),
[ELT](https://docs.ropensci.org/melt/reference/ELT-class.md),
[`elmt()`](https://docs.ropensci.org/melt/reference/elmt.md),
[`el_control()`](https://docs.ropensci.org/melt/reference/el_control.md)

## Examples

``` r
## Adjusted empirical likelihood calibration
data("precip")
fit <- el_mean(precip, 32)
elt(fit, rhs = 100, calibrate = "ael")
#> 
#>  Empirical Likelihood Test
#> 
#> Hypothesis:
#> par = 100
#> 
#> Significance level: 0.05, Calibration: Adjusted EL 
#> 
#> Statistic: 45.48, Critical value: 3.841
#> p-value: 1.539e-11 
#> EL evaluation: converged 
#> 

## Bootstrap calibration
elt(fit, rhs = 32, calibrate = "boot")
#> 
#>  Empirical Likelihood Test
#> 
#> Hypothesis:
#> par = 32
#> 
#> Significance level: 0.05, Calibration: Bootstrap 
#> 
#> Statistic: 2.997, Critical value: 3.928
#> p-value: 0.084 
#> EL evaluation: converged 
#> 

## F calibration
elt(fit, rhs = 32, calibrate = "f")
#> 
#>  Empirical Likelihood Test
#> 
#> Hypothesis:
#> par = 32
#> 
#> Significance level: 0.05, Calibration: F 
#> 
#> Statistic: 2.997, Critical value: 3.98
#> p-value: 0.0879 
#> EL evaluation: converged 
#> 

## Test of no treatment effect
data("clothianidin")
contrast <- matrix(c(
  1, -1, 0, 0,
  0, 1, -1, 0,
  0, 0, 1, -1
), byrow = TRUE, nrow = 3)
fit2 <- el_lm(clo ~ -1 + trt, clothianidin)
elt(fit2, lhs = contrast)
#> 
#>  Empirical Likelihood Test
#> 
#> Hypothesis:
#> trtNaked - trtFungicide = 0
#> trtFungicide - trtLow = 0
#> trtLow - trtHigh = 0
#> 
#> Significance level: 0.05, Calibration: Chi-square 
#> 
#> Statistic: 26.6, Critical value: 7.815
#> p-value: 7.148e-06 
#> Constrained EL: converged 
#> 

## A symbolic description of the same hypothesis
elt(fit2, lhs = c(
  "trtNaked - trtFungicide",
  "trtFungicide - trtLow",
  "trtLow - trtHigh"
))
#> 
#>  Empirical Likelihood Test
#> 
#> Hypothesis:
#> trtNaked - trtFungicide = 0
#> trtFungicide - trtLow = 0
#> trtLow - trtHigh = 0
#> 
#> Significance level: 0.05, Calibration: Chi-square 
#> 
#> Statistic: 26.6, Critical value: 7.815
#> p-value: 7.148e-06 
#> Constrained EL: converged 
#> 
```
