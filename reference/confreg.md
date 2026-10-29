# Confidence region for model parameters

Computes boundary points of a two-dimensional confidence region for
model parameters.

## Usage

``` r
# S4 method for class 'EL'
confreg(object, parm, level = 0.95, cv = NULL, npoints = 50L, control = NULL)
```

## Arguments

- object:

  An object that inherits from
  [EL](https://docs.ropensci.org/melt/reference/EL-class.md).

- parm:

  A specification of which parameters are to be given a confidence
  region, either a vector of numbers or a vector of names. It must be a
  vector of length two of the form `c(x, y)`. If missing, the first two
  parameter in `object` are considered.

- level:

  A single numeric for the confidence level required. Defaults to
  `0.95`. It is ignored if `cv` is non-`NULL`.

- cv:

  A single numeric for the critical value for calibration of empirical
  likelihood ratio statistic. Defaults to NULL and set to
  `qchisq(level, 2L)`. It must be compatible with the `th` value in
  `control`.

- npoints:

  A single integer for the number of boundary points to compute.
  Defaults to `50`.

- control:

  An object of class
  [ControlEL](https://docs.ropensci.org/melt/reference/ControlEL-class.md)
  constructed by
  [`el_control()`](https://docs.ropensci.org/melt/reference/el_control.md).
  Defaults to `NULL` and inherits the `control` slot in `object`.

## Value

An object of class
[ConfregEL](https://docs.ropensci.org/melt/reference/ConfregEL-class.md).

## References

Owen A (1990). “Empirical Likelihood Ratio Confidence Regions.” *The
Annals of Statistics*, **18**(1), 90–120.
[doi:10.1214/aos/1176347494](https://doi.org/10.1214/aos/1176347494) .

## See also

[EL](https://docs.ropensci.org/melt/reference/EL-class.md),
[`confint()`](https://docs.ropensci.org/melt/reference/confint.md),
[`elt()`](https://docs.ropensci.org/melt/reference/elt.md),
[`plot()`](https://docs.ropensci.org/melt/reference/plot.md),
[`el_control()`](https://docs.ropensci.org/melt/reference/el_control.md)

## Examples

``` r
data("mtcars")
fit <- el_lm(mpg ~ wt + qsec, data = mtcars)
cr <- confreg(fit, parm = c(2, 3), cv = qchisq(0.90, 2))
plot(cr)
```
