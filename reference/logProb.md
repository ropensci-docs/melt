# Log probabilities

Extracts log probabilities of empirical likelihood from a model.

## Usage

``` r
# S4 method for class 'EL'
logProb(object, ...)

# S4 method for class 'ELT'
logProb(object, ...)
```

## Arguments

- object:

  An object that inherits from
  [EL](https://docs.ropensci.org/melt/reference/EL-class.md) or
  [ELT](https://docs.ropensci.org/melt/reference/ELT-class.md).

- ...:

  Further arguments passed to methods.

## Value

A numeric vector.

## See also

[EL](https://docs.ropensci.org/melt/reference/EL-class.md),
[ELT](https://docs.ropensci.org/melt/reference/ELT-class.md)

## Examples

``` r
data("precip")
fit <- el_mean(precip, par = 40)
logProb(fit)
#>              Mobile              Juneau             Phoenix         Little Rock 
#>           -2.966226           -3.748590           -4.881451           -3.990394 
#>         Los Angeles          Sacramento       San Francisco              Denver 
#>           -4.776668           -4.724847           -4.664914           -4.792326 
#>            Hartford          Wilmington          Washington        Jacksonville 
#>           -4.153093           -4.243128           -4.277509           -3.757376 
#>               Miami             Atlanta            Honolulu               Boise 
#>           -3.493682           -3.997299           -4.625315           -4.815363 
#>             Chicago              Peoria        Indianapolis          Des Moines 
#>           -4.388145           -4.371719           -4.282695           -4.468608 
#>             Wichita          Louisville         New Orleans            Portland 
#>           -4.472894           -4.161886           -3.651361           -4.226853 
#>           Baltimore              Boston             Detroit    Sault Ste. Marie 
#>           -4.199123           -4.179245           -4.464303           -4.449091 
#>              Duluth Minneapolis/St Paul             Jackson         Kansas City 
#>           -4.481410           -4.568660           -3.965845           -4.325723 
#>            St Louis         Great Falls               Omaha                Reno 
#>           -4.352609           -4.760760           -4.481410           -4.878605 
#>             Concord       Atlantic City         Albuquerque              Albany 
#>           -4.345348           -4.089271           -4.870017           -4.411153 
#>             Buffalo            New York           Charlotte             Raleigh 
#>           -4.347774           -4.243128           -4.173492           -4.179245 
#>            Bismarck          Cincinnati           Cleveland            Columbus 
#>           -4.741331           -4.274906           -4.374082           -4.325723 
#>       Oklahoma City            Portland        Philadelphia          Pittsburgh 
#>           -4.455639           -4.310747           -4.251168           -4.345348 
#>          Providence            Columbia         Sioux Falls             Memphis 
#>           -4.170603           -4.060621           -4.591709           -3.969389 
#>           Nashville              Dallas             El Paso             Houston 
#>           -4.073456           -4.352609           -4.870017           -4.000733 
#>      Salt Lake City          Burlington             Norfolk            Richmond 
#>           -4.757548           -4.431417           -4.114067           -4.176373 
#>      Seattle Tacoma             Spokane          Charleston           Milwaukee 
#>           -4.280106           -4.721517           -4.226853           -4.504465 
#>            Cheyenne            San Juan 
#>           -4.767154           -3.527270 
```
