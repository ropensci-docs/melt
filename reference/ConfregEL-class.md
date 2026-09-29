# ConfregEL class

S4 class for confidence region. It inherits from `"matrix"`.

## Slots

- `estimates`:

  A numeric vector of length two for the parameter estimates.

- `level`:

  A single numeric for the confidence level required.

- `cv`:

  A single numeric for the critical value for calibration of empirical
  likelihood ratio statistic.

- `pnames`:

  A character vector of length two for the name of parameters.

## Examples

``` r
showClass("ConfregEL")
#> Class "ConfregEL" [package "melt"]
#> 
#> Slots:
#>                                                         
#> Name:      .Data estimates     level        cv    pnames
#> Class:    matrix   numeric   numeric   numeric character
#> 
#> Extends: 
#> Class "matrix", from data part
#> Class "array", by class "matrix", distance 2
#> Class "structure", by class "matrix", distance 3
#> Class "vector", by class "matrix", distance 4, with explicit coerce
```
