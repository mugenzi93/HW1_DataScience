p8105\_hw1\_cm3928
================
Clement Mugenzi
9/14/2019

``` r
library(tidyverse)
```

    ## ── Attaching packages ────────────────────────────────────────── tidyverse 1.2.1 ──

    ## ✔ ggplot2 3.2.1     ✔ purrr   0.3.2
    ## ✔ tibble  2.1.3     ✔ dplyr   0.8.3
    ## ✔ tidyr   0.8.3     ✔ stringr 1.4.0
    ## ✔ readr   1.3.1     ✔ forcats 0.4.0

    ## ── Conflicts ───────────────────────────────────────────── tidyverse_conflicts() ──
    ## ✖ dplyr::filter() masks stats::filter()
    ## ✖ dplyr::lag()    masks stats::lag()

``` r
hw_df <- tibble(
  rad_sample = rnorm(8),
  log_vec = rad_sample > 0,
  char_vec = "12345678",
  vec_factor = factor(c("kvnkndki", "12544478",
                        "kfnksnks", "kvnkndki",
                        "12544478", "kfnksnks",
                        "kvnkndki", "12544478"))
)

mean_samp = mean(pull(hw_df, rad_sample))
mean_log = mean(pull(hw_df, log_vec))
mean_char = mean(pull(hw_df, char_vec))
```

    ## Warning in mean.default(pull(hw_df, char_vec)): argument is not numeric or
    ## logical: returning NA

``` r
mean_fac = mean(pull(hw_df, vec_factor))
```

    ## Warning in mean.default(pull(hw_df, vec_factor)): argument is not numeric
    ## or logical: returning NA

A warning message is generated because I am trying to calculate the mean
of character variables and that is not possible. I am going to have to
convert some (if not all) my variables to numeric in order to obtain
their respective mean.
