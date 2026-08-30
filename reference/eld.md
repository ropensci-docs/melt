# Empirical likelihood displacement

Computes empirical likelihood displacement for model diagnostics and
outlier detection.

## Usage

``` r
# S4 method for class 'EL'
eld(object, control = NULL)

# S4 method for class 'GLM'
eld(object, control = NULL)
```

## Arguments

- object:

  An object that inherits from
  [EL](https://docs.ropensci.org/melt/reference/EL-class.md).

- control:

  An object of class
  [ControlEL](https://docs.ropensci.org/melt/reference/ControlEL-class.md)
  constructed by
  [`el_control()`](https://docs.ropensci.org/melt/reference/el_control.md).
  Defaults to `NULL` and inherits the `control` slot in `object`.

## Value

An object of class
[ELD](https://docs.ropensci.org/melt/reference/ELD-class.md).

## Details

Let \\L(\theta)\\ be the empirical log-likelihood function based on the
full sample with \\n\\ observations. The maximum empirical likelihood
estimate is denoted by \\\hat{\theta}\\. Consider a reduced sample with
the \\i\\th observation deleted and the corresponding estimate
\\\hat{\theta}\_{(i)}\\. The empirical likelihood displacement is
defined by \$\$\textrm{ELD}\_i = 2\\L(\hat{\theta}) -
L(\hat{\theta}\_{(i)})\\.\$\$ If \\\textrm{ELD}\_i \\ is large, then the
\\i\\th observation is an influential point and can be inspected as a
possible outlier. `eld` computes \\\textrm{ELD}\_i \\ for \\i = 1,
\dots, n \\.

## References

Lazar NA (2005). “Assessing the Effect of Individual Data Points on
Inference From Empirical Likelihood.” *Journal of Computational and
Graphical Statistics*, **14**(3), 626–642.
[doi:10.1198/106186005X59568](https://doi.org/10.1198/106186005X59568) .

Zhu H, Ibrahim JG, Tang N, Zhang H (2008). “Diagnostic Measures for
Empirical Likelihood of General Estimating Equations.” *Biometrika*,
**95**(2), 489–507.
[doi:10.1093/biomet/asm094](https://doi.org/10.1093/biomet/asm094) .

## See also

[EL](https://docs.ropensci.org/melt/reference/EL-class.md),
[ELD](https://docs.ropensci.org/melt/reference/ELD-class.md),
[`el_control()`](https://docs.ropensci.org/melt/reference/el_control.md),
[`plot()`](https://docs.ropensci.org/melt/reference/plot.md)

## Examples

``` r
data("precip")
fit <- el_mean(precip, par = 30)
eld <- eld(fit)
plot(eld)
```
