# Clothianidin concentration in maize plants

A dataset summarizing field experiments result of seed treatments on
clothianidin concentration.

## Usage

``` r
data("clothianidin")
```

## Format

A data frame with 102 observations and 3 variables:

- blk:

  New blocks constructed from original data. The format is 'days post
  planting_original block_year'.

- trt:

  Seed treatment.

- clo:

  Log transformed clothianidin concentration (µg).

## Source

Alford A, Krupke CH (2017). “Translocation of the Neonicotinoid Seed
Treatment Clothianidin in Maize.” *PLOS ONE*, **12**(3), 1–19.
[doi:10.1371/journal.pone.0173836](https://doi.org/10.1371/journal.pone.0173836)
.

## Details

The original data is provided by Alford and Krupke (2017). Only some of
the shoot region observations are taken from the original data and
processed for illustration.

## Examples

``` r
data("clothianidin")
clothianidin
#>         blk       trt          clo
#> 1   05_1_15 Fungicide  0.683358043
#> 2   06_1_14 Fungicide -1.343711663
#> 3   06_1_14      High  4.160300828
#> 4   06_3_14     Naked -1.266373694
#> 5   06_3_14 Fungicide  0.266203041
#> 6   06_4_14 Fungicide  0.082056593
#> 7   06_4_14      High  2.863378490
#> 8   09_1_15 Fungicide  1.288084147
#> 9   14_1_15     Naked -3.210700261
#> 10  14_1_15       Low -0.560228996
#> 11  14_3_15 Fungicide -1.867225950
#> 12  14_3_15      High  1.612473146
#> 13  14_4_15       Low  0.534477123
#> 14  16_1_15     Naked -5.184915659
#> 15  16_1_15 Fungicide -2.010318248
#> 16  16_1_15       Low  0.088207528
#> 17  16_1_15      High  1.713161913
#> 18  16_2_15     Naked -2.846879759
#> 19  16_2_15 Fungicide -2.718947107
#> 20  16_2_15       Low  0.215424056
#> 21  16_2_15      High  2.451993796
#> 22  16_3_15     Naked -3.531220341
#> 23  16_3_15 Fungicide -3.148843182
#> 24  16_3_15       Low -0.261376556
#> 25  16_3_15      High  1.586224634
#> 26  16_4_15     Naked -3.622925062
#> 27  16_4_15 Fungicide -2.483104017
#> 28  16_4_15       Low  0.003110452
#> 29  16_4_15      High  1.293410198
#> 30  19_1_15     Naked -3.939436661
#> 31  19_1_15 Fungicide -2.765904787
#> 32  19_1_15       Low -1.119407219
#> 33  19_1_15      High  1.526810884
#> 34  19_2_15     Naked -3.981492598
#> 35  19_2_15 Fungicide -3.317277042
#> 36  19_2_15       Low -1.140167204
#> 37  19_2_15      High  0.705647391
#> 38  19_3_15 Fungicide -3.188437821
#> 39  19_3_15       Low -1.207272248
#> 40  19_3_15      High  1.311046037
#> 41  19_4_15     Naked -3.723697545
#> 42  19_4_15 Fungicide -2.226847059
#> 43  19_4_15       Low -0.217086785
#> 44  19_4_15      High  0.333726798
#> 45  20_1_14     Naked -3.864591430
#> 46  20_1_14 Fungicide -4.515366320
#> 47  20_2_14     Naked -4.008676782
#> 48  20_2_14       Low -2.422512504
#> 49  20_2_14      High  1.667412263
#> 50  20_3_14 Fungicide -4.829713464
#> 51  20_3_14       Low -1.666673475
#> 52  20_3_14      High -0.281333426
#> 53  20_4_14 Fungicide -4.275357576
#> 54  20_4_14      High -0.605320236
#> 55  34_1_14     Naked -6.918566510
#> 56  34_1_14 Fungicide -5.560681591
#> 57  34_1_14       Low -6.020845161
#> 58  34_1_14      High -4.341585666
#> 59  34_2_14     Naked -4.570684029
#> 60  34_2_14 Fungicide -5.894837780
#> 61  34_2_14       Low -5.158555424
#> 62  34_2_14      High -5.772264441
#> 63  34_3_14     Naked -6.185233294
#> 64  34_3_14 Fungicide -6.035916455
#> 65  34_3_14       Low -5.840233669
#> 66  34_3_14      High -2.629107001
#> 67  34_4_14     Naked -6.660058832
#> 68  34_4_14 Fungicide -4.674579644
#> 69  34_4_14       Low -4.199705078
#> 70  34_4_14      High -4.810683566
#> 71  47_1_15     Naked -4.925091754
#> 72  47_1_15 Fungicide -5.365736825
#> 73  47_1_15       Low -4.706559761
#> 74  47_1_15      High -4.086746645
#> 75  47_2_15     Naked -5.371571727
#> 76  47_2_15 Fungicide -5.502139716
#> 77  47_2_15       Low -3.894777436
#> 78  47_2_15      High -4.723718957
#> 79  47_3_15     Naked -5.761104612
#> 80  47_3_15 Fungicide -4.302901382
#> 81  47_3_15       Low -5.270795002
#> 82  47_3_15      High -3.939092302
#> 83  47_4_15     Naked -4.101298822
#> 84  47_4_15 Fungicide -4.962184789
#> 85  47_4_15       Low -4.375258048
#> 86  47_4_15      High -3.997383917
#> 87  61_1_15     Naked -4.717642389
#> 88  61_1_15 Fungicide -5.403566637
#> 89  61_1_15       Low -5.310987880
#> 90  61_1_15      High -5.622689967
#> 91  61_2_15     Naked -5.707058650
#> 92  61_2_15 Fungicide -5.210762344
#> 93  61_2_15       Low -5.262075663
#> 94  61_2_15      High -5.325407079
#> 95  61_3_15     Naked -4.893831729
#> 96  61_3_15 Fungicide -5.086644868
#> 97  61_3_15       Low -5.230318367
#> 98  61_3_15      High -3.711771239
#> 99  61_4_15     Naked -4.025933828
#> 100 61_4_15 Fungicide -5.000619872
#> 101 61_4_15       Low -4.169193748
#> 102 61_4_15      High -5.348263289
```
