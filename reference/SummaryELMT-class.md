# SummaryELMT class

S4 class for a summary of
[ELMT](https://docs.ropensci.org/melt/reference/ELMT-class.md) objects.

## Slots

- `aliased`:

  A named logical vector showing if the original coefficients are
  aliased.

## Examples

``` r
showClass("SummaryELMT")
#> Class "SummaryELMT" [package "melt"]
#> 
#> Slots:
#>                                                                             
#> Name:  estimates statistic        df      pval        cv       rhs       lhs
#> Class:      list   numeric   integer   numeric   numeric   numeric    matrix
#>                           
#> Name:      alpha calibrate
#> Class:   numeric character
```
