
# PSIndependenceTest: Independence Tests For Two-way, Three-way And Four-way Contingency Tables

**author: Piotr Sulewski, Pomeranian University** <!-- badges: start -->
<!-- badges: end -->

The goal of the package is to put into practice the modular and
logarithmic minimum tests for independence in two-way, three-way and
four-way contingency tables. Statistic value, cv value and p-value are
calculated. This package also includes three table generation functions
and six data sets. To read more about the package please see (and cite
:)) papers:

Sulewski, P. (2016). Moc testów niezależności w tablicy dwudzielczej
większej niż 2×2. Przegląd statystyczny 63(2), 190-210.

Sulewski, P. (2019). The LMS for Testing Independence in Two-way
Contingency Tables. Biometrical Letters 56(1), 17-43.

Sulewski, P. (2018). Power Analysis Of Independence Testing for the
Three-Way Con-tingency Tables of Small Sizes. Journal of Applied
Statistics 45(13), 2481-2498.

Sulewski, P. (2021). Logarithmic Minimum Test for Independence in Three
Way Con-tingency Table of Small Sizes. Journal of Statistical
Computation and Simulation 91(13), 2780-2799.

## Installation

You can install the development version of **PSIndependenceTest** from
[GitHub](https://github.com/) with:

``` r
library(remotes)
remotes::install_github("PiotrSule/PSIndependenceTest")
#> Skipping install of 'PSIndependenceTest' from a github remote, the SHA1 (9fed97fa) has not changed since last install.
#>   Use `force = TRUE` to force installation
```

**This package includes four data sets**

The first one, **table1**, consist of 40 observations presented as
two-way contingency table 2 x 2. See details: Sulewski, P. (2017). A new
test for independence in 2x2 contingency tables. Acta Universitatis
Lodziensis. Folia Oeconomica 4(330), 55–75.

The second one, **table2**, consist of 25 observations described the
effect of a treatment for rheumatoid arthritis vs. a placebo presented
as two-way contingency table 2 x 3. See details: Sulewski, P. (2019).
The LMS for Testing Independence in Two-way Contingency Tables.
Biometrical Letters 56 (1), 17-43.

The third one, **table3**, consist of 695 observations described the
frequency of watching videos at home or at friends’ homes for young
people between 7 and 15 years of age, cross-classified according to age
and sex. Data are presented as three-way contingency table 3 x 3 x 2.
See details: Sulewski, P. (2021). Logarithmic Minimum Test for
Independence in Three Way Contingency Table of Small Sizes. Journal of
Statistical Computation and Simulation 91(13), 2780-2799

The fourth one, **table4**, consist of 100 observations obtained using
the Monte Carlo method when Ho is true, i.e. all probabilities pijt
equal 1/24. Data is presented as three-way contingency table 2 x 3 x 4.

The fifth one, **table5**,provides information on the fate of passengers
on the fatal maiden voyage of the ocean liner ‘Titanic’, summarized
according to economic status (class), sex, age and survival. Data is
presented as four-way contingency table 4 x 2 x 2 x 2. The sample size
equals 2201.

The sixth one, **table6**, consist of 100 observations obtained using
the Monte Carlo method when Ho is true, i.e. all probabilities pijtu
equal 1/16. Data is presented as four-way contingency table 2 x 2 x 2 x
2.

``` r
library(PSIndependenceTest)
dim(table1)
#> [1] 2 2
length(table2)
#> [1] 6
```

### Functions

**GenTab2**

This function generating the two-way contingency table with the Monte
Carlo method

``` r
GenTab2(matrix(1/8, nrow = 2, ncol = 4), 50)
#>      [,1] [,2] [,3] [,4]
#> [1,]    4    7    7   12
#> [2,]    4    6    6    4
GenTab2(matrix(1/12, nrow = 4, ncol = 3), 60)
#>      [,1] [,2] [,3]
#> [1,]    2    7    6
#> [2,]    8    3    8
#> [3,]    4    4    6
#> [4,]    5    4    3
```

**Mod2.stat**

This function returns the statistic value of the modular independence
test in the two-way contingency table.

``` r
Mod2.stat(table1)
#> [1] 1.273572
Mod2.stat(GenTab2(matrix(1/12, nrow = 3, ncol = 4), 60))
#> [1] 3.22124
```

**Mod2.cv**

This function returns the critical value of the modular independence
test in the two-way contingency table.

``` r
Mod2.cv(2, 2, 40, 0.05, B = 1e3) 
#> [1] 1.25
Mod2.cv(2, 3, 25, 0.1, B = 1e4) 
#> [1] 2.543885
```

**Mod2.pvalue**

This function returns the p-value of the modular independence test in
the two-way contingency table.

``` r
Mod2.pvalue(Mod2.stat(table1), 2, 2, 40, B = 1e3)
#> [1] 0.05994006
Mod2.pvalue(Mod2.stat(table2), 2, 3, 40, B = 1e4)
#> [1] 0.00049995
```

**Mod2.test**

This function returns the test statistic and p-value of the logarithmic
minimum independence test in the two-way contingency table.

``` r
Mod2.test(table1, B = 1e3)
#> 
#>  Modular test for independence in two-way contingency table
#> 
#> data:  table1
#> D = 1.2736, p-value = 0.05
Mod2.test(table1, B = 1e4)
#> 
#>  Modular test for independence in two-way contingency table
#> 
#> data:  table1
#> D = 1.2736, p-value = 0.0457
```

**Lms2.stat**

This function returns the statistic value of the logarithmic minimum
independence test in the two-way contingency table.

``` r
Lms2.stat(table1)
#> [1] 1.660665
Lms2.stat(GenTab2(matrix(1/12, nrow = 3, ncol = 4), 60))
#> [1] 2.981018
```

**Lms2.cv**

This function returns the critical value of the logarithmic minimum
independence test in the two-way contingency table.

``` r
Lms2.cv(2, 2, 40, 0.05, B = 1e3) 
#> [1] 1.268456
Lms2.cv(2, 3, 25, 0.1, B = 1e4) 
#> [1] 3.054568
```

**Lms2.pvalue**

This function returns the p-value of the logarithmic minimum
independence test in the two-way contingency table.

``` r
Lms2.pvalue(Lms2.stat(table1), 2, 2, 40, B = 1e3)
#> [1] 0.01598402
Lms2.pvalue(Lms2.stat(table2), 2, 3, 40, B = 1e4)
#> [1] 0.00019998
```

**Lms2.test**

This function returns the test statistic and p-value of the logarithmic
minimum independence test in the two-way contingency table.

``` r
Lms2.test(table1, B = 1e3)
#> 
#>  Modular test for independence in two-way contingency table
#> 
#> data:  table1
#> D = 1.6607, p-value = 0.018
Lms2.test(table1, B = 1e4)
#> 
#>  Modular test for independence in two-way contingency table
#> 
#> data:  table1
#> D = 1.6607, p-value = 0.0184
```

**GenTab3**

This function generating the three-way contingency table with the Monte
Carlo method

``` r
GenTab3(array(1/12, dim=c(2,2,3)), 60)
#> , , 1
#> 
#>      [,1] [,2]
#> [1,]    8    5
#> [2,]    6    5
#> 
#> , , 2
#> 
#>      [,1] [,2]
#> [1,]    6    4
#> [2,]    2    8
#> 
#> , , 3
#> 
#>      [,1] [,2]
#> [1,]    3    6
#> [2,]    2    5
GenTab3(array(1/18, dim=c(2,3,3)), 80)
#> , , 1
#> 
#>      [,1] [,2] [,3]
#> [1,]    5    2    8
#> [2,]    2    5    3
#> 
#> , , 2
#> 
#>      [,1] [,2] [,3]
#> [1,]    5    4    1
#> [2,]    4    4    5
#> 
#> , , 3
#> 
#>      [,1] [,2] [,3]
#> [1,]    6    5    9
#> [2,]    1    5    6
```

**Mod3.stat**

This function returns the statistic value of the modular independence
test in the three-way contingency table.

``` r
Mod3.stat(table3)
#> [1] 2.641208
Mod3.stat(GenTab3(array(1/12, dim=c(2,2,3)), 60))
#> [1] 2.714127
```

**Mod3.cv**

This function returns the critical value of the modular independence
test in the three-way contingency table.

``` r
Mod3.cv(2, 3, 4, 100, 0.05, B = 1e3) 
#> [1] 10.52972
Mod3.cv(2, 3, 4, 100, 0.1, B = 1e4) 
#> [1] 10.04156
```

**Mod3.pvalue**

This function returns the p-value of the modular independence test in
the three-way contingency table.

``` r
Mod3.pvalue(Mod3.stat(table4), 2, 3, 4, 100, B = 1e3)
#> [1] 0.1898102
Mod3.pvalue(Mod3.stat(table4), 2, 3, 4, 100, B = 1e4)
#> [1] 0.2042796
```

**Mod3.test**

This function returns the test statistic and p-value of the modular
independence test in the three-way contingency table.

``` r
Mod3.test(table4, B = 1e3)
#> 
#>  Modular test for independence in three-way contingency table
#> 
#> data:  table4
#> D = 9.3451, p-value = 0.208
Mod3.test(table4, B = 1e4)
#> 
#>  Modular test for independence in three-way contingency table
#> 
#> data:  table4
#> D = 9.3451, p-value = 0.2032
```

**Lms3.stat**

This function returns the statistic value of the logarithmic minimum
independence test in the three-way contingency table.

``` r
Lms3.stat(table4)
#> [1] 10.12261
Lms3.stat(GenTab3(array(1/27, dim = c(3, 3, 3)), 100))
#> [1] 9.867053
```

**Lms3.cv**

This function returns the critical value of the logarithmic minimum
independence test in the three-way contingency table.

``` r
Lms3.cv(2, 3, 4, 100, 0.05, B = 1e3) 
#> [1] 23.03878
Lms3.cv(2, 3, 4, 100, 0.1, B = 1e4) 
#> [1] 20.82746
```

**Lms3.pvalue**

This function returns the p-value of the logarithmic minimum
independence test in the three-way contingency table.

``` r
Lms3.pvalue(Lms3.stat(table4), 2, 3, 4, 100, B = 1e3)
#> [1] 0.4275724
Lms3.pvalue(Lms3.stat(table4), 2, 3, 4, 40, B = 1e4)
#> [1] 0.9975002
```

**Lms3.test**

This function returns the test statistic and p-value of the logarithmic
minimum independence test in the three-way contingency table.

``` r
Lms3.test(table4, B = 1e3)
#> 
#>  Logarithmic minimum test for independence in three-way contingency
#>  table
#> 
#> data:  table4
#> D = 10.123, p-value = 0.4184
Lms3.test(table4, B = 1e4)
#> 
#>  Logarithmic minimum test for independence in three-way contingency
#>  table
#> 
#> data:  table4
#> D = 10.123, p-value = 0.4182
```

**GenTab4**

This function generating the four-way contingency table with the Monte
Carlo method.

``` r
GenTab4(array(1/16, dim=c(2,2,2,2)), 100)
#> , , 1, 1
#> 
#>      [,1] [,2]
#> [1,]    4    5
#> [2,]    9    6
#> 
#> , , 2, 1
#> 
#>      [,1] [,2]
#> [1,]    8    6
#> [2,]    7    5
#> 
#> , , 1, 2
#> 
#>      [,1] [,2]
#> [1,]    6    6
#> [2,]    4    6
#> 
#> , , 2, 2
#> 
#>      [,1] [,2]
#> [1,]    8    9
#> [2,]    3    8
GenTab4(array(1/36, dim=c(2,3,2,3)), 150)
#> , , 1, 1
#> 
#>      [,1] [,2] [,3]
#> [1,]    7    4    6
#> [2,]    6    6    5
#> 
#> , , 2, 1
#> 
#>      [,1] [,2] [,3]
#> [1,]    4    2    6
#> [2,]    3    3    1
#> 
#> , , 1, 2
#> 
#>      [,1] [,2] [,3]
#> [1,]    6    2    7
#> [2,]    6    6    3
#> 
#> , , 2, 2
#> 
#>      [,1] [,2] [,3]
#> [1,]    4    3    4
#> [2,]    1    4    6
#> 
#> , , 1, 3
#> 
#>      [,1] [,2] [,3]
#> [1,]    5    4    2
#> [2,]    1    3    5
#> 
#> , , 2, 3
#> 
#>      [,1] [,2] [,3]
#> [1,]    7    6    3
#> [2,]    4    1    4
```

**Mod4.stat**

This function returns the statistic value of the modular independence
test in the four-way contingency table.

``` r
Mod4.stat(table5)
#> [1] 46.70092
Mod4.stat(table6)
#> [1] 17.816
```

**Mod4.cv**

This function returns the critical value of the modular independence
test in the four-way contingency table.

``` r
Mod4.cv(2, 2, 2, 2, 100, 0.05, B = 1e3)
#> [1] 5.921911
Mod4.cv(2, 2, 2, 2, 100, 0.1, B = 1e4)
#> [1] 5.605168
```

**Mod4.pvalue**

This function returns the p-value of the modular independence test in
the four-way contingency table.

``` r
Mod4.pvalue(Mod4.stat(table6), 2, 2, 2, 2, 100, B = 1e3)
#> [1] 0
Mod4.pvalue(Mod4.stat(table6), 2, 2, 2, 2, 100, B = 1e4)
#> [1] 0
```

**Mod4.test**

This function returns the test statistic and p-value of the modular
independence test in the -way contingency table.

``` r
Mod4.test(table6, B = 1e3)
#> 
#>  Modular test for independence in four-way contingency table
#> 
#> data:  table6
#> D = 17.816, p-value < 2.2e-16
Mod4.test(table6, B = 1e4)
#> 
#>  Modular test for independence in four-way contingency table
#> 
#> data:  table6
#> D = 17.816, p-value < 2.2e-16
```

**Lms4.stat**

This function returns the statistic value of the logarithmic minimum
independence test in the four-way contingency table.

``` r
Lms4.stat(table5)
#> [1] 36.92145
Lms4.stat(table6)
#> [1] 37.49846
```

**Lms4.cv**

This function returns the critical value of the logarithmic minimum
independence test in the four-way contingency table.

``` r
Lms4.cv(2, 2, 2, 2, 100, 0.05, B = 1e3) 
#> [1] 3.933356
Lms4.cv(2, 2, 2, 2, 100, 0.1, B = 1e4) 
#> [1] 3.435829
```

**Lms4.pvalue**

This function returns the p-value of the logarithmic minimum
independence test in the four-way contingency table.

``` r
Lms4.pvalue(Lms4.stat(table6), 2, 2, 2, 2, 100, B = 1e3)
#> [1] 0
Lms4.pvalue(Lms4.stat(table6), 2, 2, 2, 2, 100, B = 1e4)
#> [1] 0
```

**Lms4.test**

This function returns the test statistic and p-value of the logarithmic
minimum independence test in the four-way contingency table.

``` r
Lms4.test(table6, B = 1e3)
#> 
#>  Logarithmic minimum test for independence in four-way contingency table
#> 
#> data:  table6
#> D = 37.498, p-value = 9.999e-05
Lms4.test(table6, B = 1e4)
#> 
#>  Logarithmic minimum test for independence in four-way contingency table
#> 
#> data:  table6
#> D = 37.498, p-value < 2.2e-16
```
