
<!-- README.md is generated from README.Rmd. Please edit that file -->

# themis

<!-- badges: start -->

[![Lifecycle:
experimental](https://img.shields.io/badge/lifecycle-experimental-orange.svg)](https://www.tidyverse.org/lifecycle/#experimental)
[![CRAN
status](https://www.r-pkg.org/badges/version/themis)](https://CRAN.R-project.org/package=themis)
<!-- badges: end -->

**themis** contain extra steps for the
[`recipes`](https://CRAN.R-project.org/package=recipes) package for
dealingwith unbalanced data. The name **themis** is that of the [ancient
Greek
god](https://thishollowearth.wordpress.com/2012/07/02/god-of-the-week-themis/)
who is typically depicted with a balance.

![](https://thishollowearth.files.wordpress.com/2012/07/themis.jpg)

## Installation

~~You can install the released version of themis from
[CRAN](https://CRAN.R-project.org) with:~~

``` r
install.packages("themis")
```

Install the development version from GitHub with:

``` r
require("devtools")
install_github("emilhvitfeldt/themis")
```

## Example

Following is a example of using the \[SMOTE\] algorithm to deal with
unbalanced data

``` r
library(recipes)
library(themis)

data(okc)

sort(table(okc$Class, useNA = "always"))
#> 
#>  <NA>  stem other 
#>     0  9539 50316

ds_rec <- recipe(Class ~ age + height, data = okc) %>%
  step_smote(Class) %>%
  prep()

table(juice(ds_rec)$Class, useNA = "always")
#> 
#>  stem other  <NA> 
#> 28617 38156     0
```

## Code of Conduct

Please note that the ‘themis’ project is released with a [Contributor
Code of Conduct](.github/CODE_OF_CONDUCT.md). By contributing to this
project, you agree to abide by its terms.