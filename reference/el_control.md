# Control parameters for computation

Specifies computational details of (constrained) empirical likelihood.

## Usage

``` r
el_control(
  maxit = 200L,
  maxit_l = 25L,
  tol = 1e-06,
  tol_l = 1e-06,
  step = NULL,
  th = NULL,
  verbose = FALSE,
  keep_data = TRUE,
  nthreads,
  seed = NULL,
  an = NULL,
  b = 10000L,
  m = 1000000L
)
```

## Arguments

- maxit:

  A single integer for the maximum number of iterations for constrained
  minimization of empirical likelihood. Defaults to `200`.

- maxit_l:

  A single integer for the maximum number of iterations for evaluation
  of empirical likelihood. Defaults to `25`.

- tol:

  A single numeric for the convergence tolerance for the constrained
  minimization. Defaults to `1e-06`.

- tol_l:

  A single numeric for the relative convergence tolerance for the
  evaluation. Defaults to `1e-06`.

- step:

  A single numeric for the step size for projected gradient descent
  method. Defaults to `NULL` and sets the step size to the reciprocal of
  the sample size.

- th:

  A single numeric for the threshold for the negative empirical
  log-likelihood ratio. The iteration stops if the value exceeds the
  threshold. Defaults to `NULL` and sets the threshold to `200 * d`,
  where `d` corresponds to the degrees of freedom of the limiting
  chi-squared distribution of the statistic.

- verbose:

  A single logical. If `TRUE`, a message on the convergence status is
  printed when fitting objects that inherit from class
  [EL](https://docs.ropensci.org/melt/reference/EL-class.md). Defaults
  to `FALSE`.

- keep_data:

  A single logical. If `TRUE`, the data used for fitting objects that
  inherit from class
  [EL](https://docs.ropensci.org/melt/reference/EL-class.md) are stored
  for later use with other methods. Defaults to `TRUE`.

- nthreads:

  A single integer for the number of threads for parallel computation
  via OpenMP (if available). Defaults to half the available threads. For
  better performance, it is generally recommended in most platforms to
  limit the number of threads to the number of physical cores. Note that
  it applies to the following functions that involve multiple
  evaluations or optimizations:
  [`confint()`](https://docs.ropensci.org/melt/reference/confint.md),
  [`confreg()`](https://docs.ropensci.org/melt/reference/confreg.md),
  [`el_lm()`](https://docs.ropensci.org/melt/reference/el_lm.md),
  [`el_glm()`](https://docs.ropensci.org/melt/reference/el_glm.md),
  [`eld()`](https://docs.ropensci.org/melt/reference/eld.md), and
  [`elt()`](https://docs.ropensci.org/melt/reference/elt.md).

- seed:

  A single integer for the seed for random number generation. It only
  applies to [`elt()`](https://docs.ropensci.org/melt/reference/elt.md)
  when `calibrate` is set to `"boot"`. Defaults to `NULL`. In this case,
  a seed is set to a random integer generated from 1 to the maximum
  integer supported by R on the machine, which is determined by
  [`set.seed()`](https://rdrr.io/r/base/Random.html). Only one seed is
  needed even when multiple threads are used with `nthreads`. Each
  thread is given a separate seed to produce a non-overlapping but
  reproducible sequence of random numbers. The Xoshiro256+ pseudo-random
  number generator is used internally to work with OpenMP.

- an:

  A single numeric representing the scaling factor for adjusted
  empirical likelihood calibration. It only applies to
  [`elt()`](https://docs.ropensci.org/melt/reference/elt.md) when
  `calibrate` is set to `"ael"`. Defaults to `NULL`.

- b:

  A single integer for the number of bootstrap replicates. It only
  applies to [`elt()`](https://docs.ropensci.org/melt/reference/elt.md)
  when `calibrate` is set to `"boot"`. Defaults to `10000`.

- m:

  A single integer for the number of Monte Carlo samples. It only
  applies to
  [`elmt()`](https://docs.ropensci.org/melt/reference/elmt.md). Defaults
  to `1e+06`.

## Value

An object of class of
[ControlEL](https://docs.ropensci.org/melt/reference/ControlEL-class.md).

## See also

[`el_eval()`](https://docs.ropensci.org/melt/reference/el_eval.md),
[`elt()`](https://docs.ropensci.org/melt/reference/elt.md)

## Examples

``` r
optcfg <- el_control(maxit = 300, step = 0.01, th = 200, nthreads = 1)
```
