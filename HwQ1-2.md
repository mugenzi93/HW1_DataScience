p8105\_hw1\_cm3928
================
Clement Mugenzi
9/14/2019

# Question 1

## First Part

Here, the package Tidyverse was loaded but the code chunk hidden.

``` r
hw_df <- tibble(
  rad_sample = rnorm(8),
  log_vec = rad_sample > 0,
  char_vec = c("1", "2", "3", "4", "5", "6", "7", "8"),
  vec_factor = factor(c("male", "female",
                        "female", "female",
                        "male", "male",
                        "male", "female"))
)

mean_samp = mean(pull(hw_df, rad_sample))
mean_samp
```

    ## [1] -0.3114962

``` r
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

Below I will convert the logical, character, and factor variables to
numeric using the ‘as.numeric’ function.

``` r
as.numeric(pull(hw_df, log_vec))
as.numeric(pull(hw_df, char_vec))
as.numeric(pull(hw_df, vec_factor))
```

## What happens?

  - When as.numeric is applied on the logical variable, I get zeros and
    ones back, which represents FALSE and TRUE respectively. Therefore,
    the as.numeric basically converted characters into numbers. And when
    the mean function is applied on this new logical variable, I get
    0.375 as its mean (this mean is subjected to change every time this
    code is ran since we are dealing with a random sample).

  - Secondly, when as.numeric is applied on the char\_vec, the result is
    eight identical numbers since variables in a dataframe have to be of
    the same lenght. Therefore, since the character variable was inside
    quotes, the as.numeric fucntion produces real numbers (without
    quotes) but this function dows not convert this character variable
    to numeric.

  - Third, when as.numeric is applied on the vec\_factor, the result are
    numbers from one to three which represents the three levels and
    their distribution in the factor variable. Again as.numeric does not
    change this factor variable to numeric.

## Why?

The reason why we could not determine the mean of the last two variables
is because they are neither numeric not are they logical.

Yes, this explain why we could only find the mean of the random sample
and logical variable (as they are numeric and logical) but not the mean
for character and factor variables.

## Second Part

In this section, I will perform three different tasks in the same code
chunk.

1.  First, I will convert the logical vector to numeric, and multiply
    the random sample by the result
2.  I will convert the logical vector to a factor, and multiply the
    random sample by the result
3.  Third, I will convert the logical vector to a factor and then
    convert the result to numeric, and multiply the random sample by the
    result

<!-- end list -->

``` r
# (1)
log_as_num <- as.numeric(pull(hw_df, log_vec))
log_as_num
```

    ## [1] 1 1 0 1 0 0 0 0

``` r
x <- log_as_num
y <- rnorm(8)
x * y # Where x is the converted logical variable and y the random sample.
```

    ## [1] -1.6743353 -0.2339612  0.0000000 -1.5792151  0.0000000  0.0000000
    ## [7]  0.0000000  0.0000000

``` r
# (2)
log_as_fac <- as.factor(log_as_num)
t <- log_as_fac
t * y
```

    ## Warning in Ops.factor(t, y): '*' not meaningful for factors

    ## [1] NA NA NA NA NA NA NA NA

``` r
# (3)
log_to_num <- as.numeric(log_as_fac)
d <- log_to_num
d * y # where d is the converted logical factor and y the random sample.
```

    ## [1] -3.34867056 -0.46792232  0.39040139 -3.15843025 -0.08985194 -0.96911113
    ## [7] -1.06165917 -1.17658661

# Question 2

## Creating a Dataframe

``` r
library(tidyverse)
rad_df <- tibble(
  x <- rnorm(500, sd = 0.5),
  y <- 1 + 4 * x + rnorm(500),
  
)
```

    ## Warning in 1 + 4 * x + rnorm(500): longer object length is not a multiple
    ## of shorter object length
