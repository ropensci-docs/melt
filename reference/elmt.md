# Empirical likelihood multiple tests

Tests multiple linear hypotheses simultaneously.

## Usage

``` r
# S4 method for class 'EL'
elmt(object, rhs = NULL, lhs = NULL, alpha = 0.05, control = NULL)
```

## Arguments

- object:

  An object that inherits from
  [EL](https://docs.ropensci.org/melt/reference/EL-class.md).

- rhs:

  A numeric vector (column matrix) or a list of numeric vectors for the
  right-hand sides of hypotheses. Defaults to `NULL`. See ‘Details’.

- lhs:

  A list or a numeric matrix for the left-hand sides of hypotheses. For
  a list `lhs`, each element must be specified as a single instance of
  the `lhs` in
  [`elt()`](https://docs.ropensci.org/melt/reference/elt.md). For a
  matrix `lhs`, each row gives a linear combination of the parameters in
  `object`. The number of columns must be equal to the number of
  parameters. Defaults to `NULL`. See ‘Details’.

- alpha:

  A single numeric for the overall significance level. Defaults to
  `0.05`.

- control:

  An object of class
  [ControlEL](https://docs.ropensci.org/melt/reference/ControlEL-class.md)
  constructed by
  [`el_control()`](https://docs.ropensci.org/melt/reference/el_control.md).
  Defaults to `NULL` and inherits the `control` slot in `object`.

## Value

An object of class of
[ELMT](https://docs.ropensci.org/melt/reference/ELMT-class.md).

## Details

`elmt()` tests multiple hypotheses simultaneously. Each hypothesis
corresponds to the constrained empirical likelihood ratio described in
[CEL](https://docs.ropensci.org/melt/reference/CEL-class.md). `rhs` and
`lhs` cannot be both `NULL`. The right-hand side and left-hand side of
each hypothesis must be specified as described in
[`elt()`](https://docs.ropensci.org/melt/reference/elt.md).

For specifying linear contrasts more conveniently, `rhs` and `lhs` also
take a numeric vector and a numeric matrix, respectively. Each element
of `rhs` and each row of `lhs` correspond to a contrast (hypothesis).

The vector of empirical likelihood ratio statistics asymptotically
follows a multivariate chi-square distribution under the complete null
hypothesis. The multiple testing procedure asymptotically controls the
family-wise error rate at the level `alpha`. Based on the distribution
of the maximum of the test statistics, the adjusted p-values are
estimated by Monte Carlo simulation.

## References

Kim E, MacEachern SN, Peruggia M (2023). “Empirical likelihood for the
analysis of experimental designs.” *Journal of Nonparametric
Statistics*, **35**(4), 709–732.
[doi:10.1080/10485252.2023.2206919](https://doi.org/10.1080/10485252.2023.2206919)
.

Kim E, MacEachern SN, Peruggia M (2024). “melt: Multiple Empirical
Likelihood Tests in R.” *Journal of Statistical Software*, **108**(5),
1–33. [doi:10.18637/jss.v108.i05](https://doi.org/10.18637/jss.v108.i05)
.

## See also

[EL](https://docs.ropensci.org/melt/reference/EL-class.md),
[ELMT](https://docs.ropensci.org/melt/reference/ELMT-class.md),
[`elt()`](https://docs.ropensci.org/melt/reference/elt.md),
[`el_control()`](https://docs.ropensci.org/melt/reference/el_control.md)

## Examples

``` r
## Bivariate mean (list `rhs` & no `lhs`)
set.seed(143)
data("women")
fit <- el_mean(women, par = c(65, 135))
rhs <- list(c(64, 133), c(66, 140))
elmt(fit, rhs = rhs)
#> 
#>  Empirical Likelihood Multiple Tests
#> 
#> Overall significance level: 0.05 
#> 
#> Calibration: Multivariate chi-square 
#> 
#> Hypotheses:
#>   Chisq Df
#> 1 2.069  2
#> 2 1.255  2
#> 

## Pairwise comparison (no `rhs` & list `lhs`)
data("clothianidin")
fit2 <- el_lm(clo ~ -1 + trt, clothianidin)
lhs2 <- list(
  "trtNaked - trtFungicide",
  "trtFungicide - trtLow",
  "trtLow - trtHigh"
)
elmt(fit2, lhs = lhs2)
#> 
#>  Empirical Likelihood Multiple Tests
#> 
#> Overall significance level: 0.05 
#> 
#> Calibration: Multivariate chi-square 
#> 
#> Hypotheses:
#>                             Estimate Chisq Df
#> trtNaked - trtFungicide = 0  -1.0525 5.510  1
#> trtFungicide - trtLow = 0    -0.6269 1.062  1
#> trtLow - trtHigh = 0         -1.4932 3.774  1
#> 

## Arbitrary hypotheses (list `rhs` & list `lhs`)
data("mtcars")
fit3 <- el_lm(mpg ~ wt + qsec, data = mtcars)
lhs3 <- list(c(1, 4, 0), rbind(c(0, 1, 0), c(0, 0, 1)))
rhs3 <- list(0, c(-6, 1))
elmt(fit3, rhs = rhs3, lhs = lhs3)
#> 
#>  Empirical Likelihood Multiple Tests
#> 
#> Overall significance level: 0.05 
#> 
#> Calibration: Multivariate chi-square 
#> 
#> Hypotheses:
#>   Chisq Df
#> 1 0.037  1
#> 2 2.790  2
#> 
```
