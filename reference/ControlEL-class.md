# ControlEL class

S4 class for computational details of empirical likelihood.

## Slots

- `maxit`:

  A single integer for the maximum number of iterations for the
  optimization with respect to \\\theta\\.

- `maxit_l`:

  A single integer for the maximum number of iterations for the
  optimization with respect to \\\lambda\\.

- `tol`:

  A single numeric for the convergence tolerance denoted by
  \\\epsilon\\. The iteration stops when \$\$\\P \nabla
  l(\theta^{(k)})\\ \< \epsilon.\$\$

- `tol_l`:

  A single numeric for the relative convergence tolerance denoted by
  \\\delta\\. The iteration stops when \$\$\\\lambda^{(k)} -
  \lambda^{(k - 1)}\\ \< \delta\\\lambda^{(k - 1)}\\ + \delta^2.\$\$

- `step`:

  A single numeric for the step size \\\gamma\\ for the projected
  gradient descent method.

- `th`:

  A single numeric for the threshold for the negative empirical
  log-likelihood ratio.

- `verbose`:

  A single logical for whether to print a message on the convergence
  status.

- `keep_data`:

  A single logical for whether to keep the data used for fitting model
  objects.

- `nthreads`:

  A single integer for the number of threads for parallel computation
  via OpenMP (if available).

- `seed`:

  A single integer for the seed for random number generation.

- `an`:

  A single numeric representing the scaling factor for adjusted
  empirical likelihood calibration.

- `b`:

  A single integer for the number of bootstrap replicates.

- `m`:

  A single integer for the number of Monte Carlo samples.

## Examples

``` r
showClass("ControlEL")
#> Class "ControlEL" [package "melt"]
#> 
#> Slots:
#>                                                                             
#> Name:      maxit   maxit_l       tol     tol_l      step        th   verbose
#> Class:   integer   integer   numeric   numeric       ANY       ANY   logical
#>                                                                   
#> Name:  keep_data  nthreads      seed        an         b         m
#> Class:   logical   integer       ANY       ANY   integer   integer
```
