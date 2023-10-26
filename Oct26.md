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

    ##  [1]  0.61321669  0.82596299  0.06183258 -0.62437202  0.22148072  0.59465405
    ##  [7]  0.51223130  0.76135598  0.21761374 -1.40891602  1.63669521  1.21428340
    ## [13] -1.16558236  0.57850257 -0.14123302 -1.73050565 -1.59441873 -0.81428214
    ## [19]  1.19771091  0.36288571 -0.12376242 -0.23464675  1.45814193 -1.71759940
    ## [25] -0.70124927

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

    ##  [1]  0.61321669  0.82596299  0.06183258 -0.62437202  0.22148072  0.59465405
    ##  [7]  0.51223130  0.76135598  0.21761374 -1.40891602  1.63669521  1.21428340
    ## [13] -1.16558236  0.57850257 -0.14123302 -1.73050565 -1.59441873 -0.81428214
    ## [19]  1.19771091  0.36288571 -0.12376242 -0.23464675  1.45814193 -1.71759940
    ## [25] -0.70124927

``` r
z_scores(x = 3)

z_scores("my name is ixta")

z_scores(iris)

z_scores(sample(c(TRUE, FALSE), 25, replace = TRUE))
```

``` r
mean_and_sd = function(x) {
  
  if (!is.numeric(x)) {
    stop("Argument x should be numeric")
  } else if (length(x) == 1) {
    stop("Cannot be computed for length 1 vectors")
  }
  
  mean_x = mean(x)
  sd_x = sd(x)

  list(mean = mean_x, 
       sd = sd_x)
}

mean_and_sd(x_vec)
```

    ## $mean
    ## [1] 3.962473
    ## 
    ## $sd
    ## [1] 2.768166

## Start getting means and stds

``` r
x_vec = rnorm(n = 30, mean = 5, sd = 0.5)

tibble(
  mean = mean(x_vec), 
  sd = sd(x_vec)
)
```

    ## # A tibble: 1 × 2
    ##    mean    sd
    ##   <dbl> <dbl>
    ## 1  4.99 0.568

Write a function that uses ‘n’, a true mean, and true SD as inputs.

``` r
sim_mean_sd = function(n_obs, mu, sigma){
  x_vec = rnorm(n = n_obs, mean = mu, sd = sigma)

  tibble(
  mean = mean(x_vec), 
  sd = sd(x_vec)
)
}

sim_mean_sd(n_obs = 30, mu = 5, sigma = 0.5)
```

    ## # A tibble: 1 × 2
    ##    mean    sd
    ##   <dbl> <dbl>
    ## 1  5.05 0.486
