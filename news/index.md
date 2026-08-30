# Changelog

## melt 1.11.4

CRAN release: 2024-05-17

### MINOR IMPROVEMENTS

- The internal pseudo-random number generator has been switched from
  Xoshiro256+ to Xoshiro256++ with the release of the new dqrng package.

## melt 1.11.3

CRAN release: 2024-04-12

### NEW FEATURES

- New `"ael"` option has been added in the `calibrate` argument of
  [`elt()`](https://docs.ropensci.org/melt/reference/elt.md) for
  adjusted empirical likelihood calibration.

### MINOR IMPROVEMENTS

- The package vignette has been updated.

## melt 1.11.2

CRAN release: 2024-03-21

### MINOR IMPROVEMENTS

- The package vignette has been updated.

## melt 1.11.1

CRAN release: 2024-03-01

### MINOR IMPROVEMENTS

- Some function arguments now utilize the checkmate package for
  validation.

- The package vignette has been updated.

## melt 1.11.0

CRAN release: 2024-02-17

### MINOR IMPROVEMENTS

- Updated package vignette with the publication in the Journal of
  Statistical Software.

### DEPRECATED AND DEFUNCT

- Removed `el_pairwise()` and associated methods.

- Removed
  [`sigTests()`](https://docs.ropensci.org/melt/reference/sigTests.md)
  for objects inheriting from `SummaryLM`.

## melt 1.10.0

CRAN release: 2023-05-23

### NEW FEATURES

- [`el_glm()`](https://docs.ropensci.org/melt/reference/el_glm.md)
  accepts `quasipoisson` family with `"sqrt"` link function for the
  argument `family`.

### DEPRECATED AND DEFUNCT

- [`sigTests()`](https://docs.ropensci.org/melt/reference/sigTests.md)
  is deprecated in favor of
  [`coef()`](https://docs.ropensci.org/melt/reference/coef.md) for an
  object that inherits from `SummaryLM` and will be removed in a future
  release.

- [`logLik()`](https://rdrr.io/r/stats/logLik.html) is removed.

## melt 1.9.0

CRAN release: 2022-11-04

### NEW FEATURES

- [`confint()`](https://docs.ropensci.org/melt/reference/confint.md) is
  applicable to an `EMLT` object to produce simultaneous confidence
  intervals.

- All model objects gain `control` slot of `ControlEL` class. All
  methods that apply to these objects inherit `control` unless it is
  overwritten by the user explicitly.

### MINOR IMPROVEMENTS

- [`summary()`](https://docs.ropensci.org/melt/reference/summary.md) is
  applicable to an object that inherits from `EL`, `ELT`, and `EMLT`.

- A more informative message is printed regarding the convergence
  status.

- `optim` slot in all model or summary objects gains a single logical
  element `cstr` that shows whether a constrained EL computation is
  involved or not.

### DEPRECATED AND DEFUNCT

- [`logLik()`](https://rdrr.io/r/stats/logLik.html) is deprecated and
  will be removed in a future release.

### BUG FIXES

- [`confreg()`](https://docs.ropensci.org/melt/reference/confreg.md)
  checks whether `parm` matches the parameters in `object` when a
  `character` vector is specified for `parm`.

## melt 1.8.0

CRAN release: 2022-09-21

### NEW FEATURES

- New accessor method
  [`logProb()`](https://docs.ropensci.org/melt/reference/logProb.md)
  extracts a model’s log probabilities of empirical likelihood.

- [`el_lm()`](https://docs.ropensci.org/melt/reference/el_lm.md) and
  [`el_glm()`](https://docs.ropensci.org/melt/reference/el_glm.md) gain
  an argument `offset`.

- [`el_glm()`](https://docs.ropensci.org/melt/reference/el_glm.md)
  accepts `quasipoisson` family with `"identity"` link function for the
  argument `family`.

- [`elt()`](https://docs.ropensci.org/melt/reference/elt.md) accepts a
  character vector for the argument `lhs`, allowing a symbolic
  description of a hypothesis.

- `eltmt()` accepts a character vector as an element of the argument
  `lhs`, allowing a symbolic description of hypotheses.

- [`plot()`](https://docs.ropensci.org/melt/reference/plot.md) applies
  to an object that inherits from `EL` to plot empirical likelihood
  displacement values versus observation index.

- New dataset `thiamethoxam` added.

### MINOR IMPROVEMENTS

- [`coef()`](https://docs.ropensci.org/melt/reference/coef.md) and
  [`getDF()`](https://docs.ropensci.org/melt/reference/getDF.md) is
  applicable to an object of class `EMLT`.

- [`print()`](https://docs.ropensci.org/melt/reference/print.md) shows
  the tested hypothesis when applied to an object of class `ELT`.

- [`print()`](https://docs.ropensci.org/melt/reference/print.md) shows
  the tested hypotheses, the estimates, and marginal degrees of freedom
  when applied to an object of class `ELMT`. The description of the
  hypotheses and the estimates are printed only when the marginal
  degrees of freedom are all one.

- `"boot"` option in the `calibrate` argument of
  [`elt()`](https://docs.ropensci.org/melt/reference/elt.md) yields a
  more reliable result when applied to an object that inherits from
  `LM`.

- Internal routines for projection operation do not compute an explicit
  inverse (thanks to [@awstringer1](https://github.com/awstringer1)).

### BUG FIXES

- [`elmt()`](https://docs.ropensci.org/melt/reference/elmt.md) returns a
  correct critical value when applied to an object of class `QGLM`.

- `"boot"` option in the `calibrate` argument of
  [`elt()`](https://docs.ropensci.org/melt/reference/elt.md) works with
  an object of class `SD`.

## melt 1.7.0

CRAN release: 2022-08-12

### NEW FEATURES

- [`el_glm()`](https://docs.ropensci.org/melt/reference/el_glm.md)
  accepts `quasipoisson` family with `"log"` link function for the
  argument `family`.

- New accessor methods added
  ([`chisq()`](https://docs.ropensci.org/melt/reference/chisq.md),
  [`critVal()`](https://docs.ropensci.org/melt/reference/critVal.md),
  [`getDF()`](https://docs.ropensci.org/melt/reference/getDF.md),
  [`getOptim()`](https://docs.ropensci.org/melt/reference/getOptim.md),
  [`sigTests()`](https://docs.ropensci.org/melt/reference/sigTests.md),
  [`logL()`](https://docs.ropensci.org/melt/reference/logL.md), and
  [`pVal()`](https://docs.ropensci.org/melt/reference/pVal.md)).

- [`conv()`](https://docs.ropensci.org/melt/reference/conv.md) is
  applicable to an object returned by
  [`summary()`](https://docs.ropensci.org/melt/reference/summary.md).

### MINOR IMPROVEMENTS

- [`print()`](https://docs.ropensci.org/melt/reference/print.md) shows
  class-specific information.

- `p.value` returned by
  [`el_eval()`](https://docs.ropensci.org/melt/reference/el_eval.md) is
  renamed to `pval` for consistency with other functions.

### BUG FIXES

- [`confint()`](https://docs.ropensci.org/melt/reference/confint.md) and
  [`confreg()`](https://docs.ropensci.org/melt/reference/confreg.md) are
  not applicable to an object whose `data` is `NULL`.

## melt 1.6.0

CRAN release: 2022-07-10

### BREAKING CHANGES

- [`el_mean()`](https://docs.ropensci.org/melt/reference/el_mean.md)
  takes arguments in a different order to comply with the ‘tidyverse’
  style. It takes the data argument `x` first, followed by the parameter
  specification `par` as `el_mean(x, par)`.

- `lht()` is renamed to
  [`elt()`](https://docs.ropensci.org/melt/reference/elt.md).

- `model` argument in
  [`el_mean()`](https://docs.ropensci.org/melt/reference/el_mean.md),
  [`el_lm()`](https://docs.ropensci.org/melt/reference/el_lm.md), and
  [`el_glm()`](https://docs.ropensci.org/melt/reference/el_glm.md) are
  removed. Use `keep_data` in
  [`el_control()`](https://docs.ropensci.org/melt/reference/el_control.md).

### NEW FEATURES

- New package dependencies are added (BH, dqrng, and graphics).

- New [`elt()`](https://docs.ropensci.org/melt/reference/elt.md)
  replaces `lht()`. It accepts additional arguments `alpha` and
  `calibrate`.

- New [`el_sd()`](https://docs.ropensci.org/melt/reference/el_sd.md)
  performs empirical likelihood test for the standard deviation.

- New [`elmt()`](https://docs.ropensci.org/melt/reference/elmt.md) tests
  multiple hypotheses with empirical likelihood.

- New [`weights()`](https://docs.ropensci.org/melt/reference/weights.md)
  extracts the re-scaled weights from a model.

- New [`formula()`](https://rdrr.io/r/stats/formula.html) extracts the
  model formula used from a model.

- New [`nobs()`](https://docs.ropensci.org/melt/reference/nobs.md)
  extracts the number of observations from a model.

- New [`conv()`](https://docs.ropensci.org/melt/reference/conv.md)
  extracts the convergence status from a model.

- New [`logLR()`](https://docs.ropensci.org/melt/reference/logLR.md)
  extracts the log empirical likelihood ratio from a model.

- [`el_control()`](https://docs.ropensci.org/melt/reference/el_control.md)
  gains additional arguments `verbose`, `keep_data`, `seed`, `b`, and
  `m`.

### MINOR IMPROVEMENTS

- `cv` argument in
  [`confint()`](https://docs.ropensci.org/melt/reference/confint.md) and
  [`confreg()`](https://docs.ropensci.org/melt/reference/confreg.md)
  defaults to `NULL`. If non-`NULL`, `level` is ignored.

- `probit` link produces a more accurate result in
  [`el_glm()`](https://docs.ropensci.org/melt/reference/el_glm.md).

- [`print()`](https://docs.ropensci.org/melt/reference/print.md) for an
  `EL` object shows whether the data are weighted or not.

- All row or column names (if any) of input data are preserved in a
  fitted `EL` object.

### BUG FIXES

- [`confint()`](https://docs.ropensci.org/melt/reference/confint.md) and
  [`confreg()`](https://docs.ropensci.org/melt/reference/confreg.md)
  check if the `cv` argument is compatible with the `th` value set by
  `control_el()`.

## melt 1.5.2

CRAN release: 2022-06-15

### NEW FEATURES

- `lht()` accepts both numeric vector and matrix for `lhs` and `rhs`
  arguments.

- OpenMP parallelization is available for
  [`confint()`](https://docs.ropensci.org/melt/reference/confint.md) by
  specifying `nthreads` through `control` argument.

### DEPRECATED AND DEFUNCT

- `el_test()` is removed.

- `el_pairwise()` is deprecated and will be removed in a future release.

## melt 1.5.1

CRAN release: 2022-05-06

### BUG FIXES

- Unit test errors are fixed.

## melt 1.5.0

CRAN release: 2022-05-03

### NEW FEATURES

- S4 classes, generics, and methods are adopted throughout the package.

- New [`confreg()`](https://docs.ropensci.org/melt/reference/confreg.md)
  constructs confidence regions.

- New [`eld()`](https://docs.ropensci.org/melt/reference/eld.md)
  computes empirical likelihood displacement values.

- New
  [`el_control()`](https://docs.ropensci.org/melt/reference/el_control.md)
  the specifies `control` argument.

- New [`el_glm()`](https://docs.ropensci.org/melt/reference/el_glm.md)
  performs empirical likelihood tests to generalized linear models. More
  families and link functions will be supported in a future release.

- [`confint()`](https://docs.ropensci.org/melt/reference/confint.md)
  gains `cv` argument for a user-supplied critical value.

### DEPRECATED AND DEFUNCT

- `el_aov()` is removed.

- `el_test()` is deprecated and will be removed in a future release.

## melt 1.4.0

CRAN release: 2022-04-03

### NEW FEATURES

- New `lht()` performs linear hypothesis testing.

- New [`confint()`](https://docs.ropensci.org/melt/reference/confint.md)
  constructs confidence intervals.

- New [`logLik()`](https://rdrr.io/r/stats/logLik.html) extracts
  empirical log-likelihood.

### DEPRECATED AND DEFUNCT

- `el_aov()` is deprecated in favor of
  [`el_lm()`](https://docs.ropensci.org/melt/reference/el_lm.md). It
  will be removed in a future release.

## melt 1.3.0

CRAN release: 2022-03-07

### NEW FEATURES

- [`el_eval()`](https://docs.ropensci.org/melt/reference/el_eval.md) is
  added for direct computation with custom estimating functions.

- [`el_mean()`](https://docs.ropensci.org/melt/reference/el_mean.md) and
  [`el_lm()`](https://docs.ropensci.org/melt/reference/el_lm.md) accepts
  an optional `weights` argument for weighted EL. Arguments on
  optimization are now handled by a new `control` argument. It will be
  used in other functions in future releases.

## melt 1.2.0

CRAN release: 2022-01-30

### NEW FEATURES

- New [`el_lm()`](https://docs.ropensci.org/melt/reference/el_lm.md)
  performs empirical likelihood tests for linear models.

## melt 1.1.0

CRAN release: 2021-12-22

### NEW FEATURES

- New `el_aov()` performs a one-way analysis of variance.

## melt 1.0.1

CRAN release: 2021-10-08

### BUG FIXES

- Header file issues related to OpenMP and C++ array class are fixed.

## melt 1.0.0

CRAN release: 2021-09-29

- Released on CRAN.
