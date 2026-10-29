# Plot methods

Provides plot methods for objects.

## Usage

``` r
# S4 method for class 'ConfregEL'
plot(x, y, ...)

# S4 method for class 'EL'
plot(x, y, ...)

# S4 method for class 'ELD'
plot(x, y, ...)
```

## Arguments

- x:

  An object to be plotted.

- y:

  Not used.

- ...:

  Further graphical parameters (see
  [`par`](https://rdrr.io/r/graphics/par.html)).

## Value

No return value, called for side effects.

## Methods (by class)

- `plot(ConfregEL)`: Plots a two-dimensional confidence region for model
  parameters.

- `plot(EL)`: Plots empirical likelihood displacement values versus
  observation index.
  [`eld()`](https://docs.ropensci.org/melt/reference/eld.md) is called
  implicitly.

- `plot(ELD)`: Plots empirical likelihood displacement values versus
  observation index.

## See also

[ConfregEL](https://docs.ropensci.org/melt/reference/ConfregEL-class.md),
[EL](https://docs.ropensci.org/melt/reference/EL-class.md),
[ELD](https://docs.ropensci.org/melt/reference/ELD-class.md),
[`confreg()`](https://docs.ropensci.org/melt/reference/confreg.md),
[`eld()`](https://docs.ropensci.org/melt/reference/eld.md)

## Examples

``` r
## Model
data("mtcars")
fit <- el_lm(hp ~ wt, data = mtcars)

## Confidence region
out1 <- confreg(fit, npoints = 500)
plot(out1)


## Empirical likelihood displacement
out2 <- eld(fit)
plot(out2)


## A shortcut to `ELD`
plot(fit)
```
