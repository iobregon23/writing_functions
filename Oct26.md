Oct26
================
Ixtaccihuatl Obregon
2023-10-26

``` r
library(tidyverse)
```

    ## ── Attaching core tidyverse packages ──────────────────────── tidyverse 2.0.0 ──
    ## ✔ dplyr     1.1.3     ✔ readr     2.1.4
    ## ✔ forcats   1.0.0     ✔ stringr   1.5.0
    ## ✔ ggplot2   3.4.3     ✔ tibble    3.2.1
    ## ✔ lubridate 1.9.2     ✔ tidyr     1.3.0
    ## ✔ purrr     1.0.2     
    ## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ## ✖ dplyr::filter() masks stats::filter()
    ## ✖ dplyr::lag()    masks stats::lag()
    ## ℹ Use the conflicted package (<http://conflicted.r-lib.org/>) to force all conflicts to become errors

``` r
library(rvest)
```

    ## 
    ## Attaching package: 'rvest'
    ## 
    ## The following object is masked from 'package:readr':
    ## 
    ##     guess_encoding

Start with code you’ve written outside for your function

``` r
x_vec = rnorm(25, mean = 5, sd = 3)

(x_vec - mean(x_vec)) / sd(x_vec)
```

    ##  [1] -0.8782137  1.5819760 -0.8819284 -0.3606779  0.7970441 -0.4635106
    ##  [7]  0.3225486  2.3261033  1.3032337 -0.3522328  0.6005817 -0.2156216
    ## [13]  0.6096288 -1.9012739 -0.4386497  0.5668045 -0.8077260 -0.4871177
    ## [19] -1.3628759 -0.3334986  0.8606089 -1.1035013 -0.7597539  0.2531458
    ## [25]  1.1249064

Writing a function!

``` r
z_scores = function(x) {
  if(!is.numeric(x)){
    stop("Argument x should be numeric")
  }else if (length(x) == 1){
    stop("Z score cannot be computed for length 1 vectors")
  }
  z = (x - mean(x)) / sd(x)
  z
}

z_scores(x_vec)
```

    ##  [1] -0.8782137  1.5819760 -0.8819284 -0.3606779  0.7970441 -0.4635106
    ##  [7]  0.3225486  2.3261033  1.3032337 -0.3522328  0.6005817 -0.2156216
    ## [13]  0.6096288 -1.9012739 -0.4386497  0.5668045 -0.8077260 -0.4871177
    ## [19] -1.3628759 -0.3334986  0.8606089 -1.1035013 -0.7597539  0.2531458
    ## [25]  1.1249064

``` r
z_scores(x = 3)

z_scores("my name is ixta")

z_scores(iris)

z_scores(sample(c(TRUE, FALSE), 25, replace = TRUE))
```
