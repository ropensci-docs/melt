# Confidence interval for model parameters

Computes confidence intervals for one or more parameters in a model.

## Usage

``` r
# S4 method for class 'EL'
confint(object, parm, level = 0.95, cv = NULL, control = NULL)

# S4 method for class 'ELMT'
confint(object, cv = NULL, control = NULL)
```

## Arguments

- object:

  An object that inherits from
  [EL](https://docs.ropensci.org/melt/reference/EL-class.md) or
  [ELMT](https://docs.ropensci.org/melt/reference/ELMT-class.md).

- parm:

  A specification of which parameters are to be given confidence
  intervals, either a vector of numbers or a vector of names. If
  missing, all parameters are considered.

- level:

  A single numeric for the confidence level required. Defaults to
  `0.95`.

- cv:

  A single numeric for the critical value for calibration of empirical
  likelihood ratio statistic. Defaults to `NULL` and set to
  `qchisq(level, 1L)`. If non-`NULL`, `level` is ignored.

- control:

  An object of class
  [ControlEL](https://docs.ropensci.org/melt/reference/ControlEL-class.md)
  constructed by
  [`el_control()`](https://docs.ropensci.org/melt/reference/el_control.md).
  Defaults to `NULL` and inherits the `control` slot in `object`.

## Value

A matrix with columns giving lower and upper confidence limits for each
parameter. In contrast to other methods that rely on studentization, the
lower and upper limits obtained from empirical likelihood do not
correspond to the `(1 - level) / 2` and `1 - (1 - level) / 2` in %,
respectively.

## References

Owen A (1990). “Empirical Likelihood Ratio Confidence Regions.” *The
Annals of Statistics*, **18**(1), 90–120.
[doi:10.1214/aos/1176347494](https://doi.org/10.1214/aos/1176347494) .

## See also

[EL](https://docs.ropensci.org/melt/reference/EL-class.md),
[ELMT](https://docs.ropensci.org/melt/reference/ELMT-class.md),
[`confreg()`](https://docs.ropensci.org/melt/reference/confreg.md),
[`elt()`](https://docs.ropensci.org/melt/reference/elt.md),
[`el_control()`](https://docs.ropensci.org/melt/reference/el_control.md)

## Examples

``` r
data("mtcars")
fit <- el_lm(mpg ~ ., data = mtcars)
confint(fit, parm = c(2, 3))
#>             lower     upper
#> cyl  -0.426725127 0.3802687
#> disp  0.006409155 0.0218920
```
