Lab5
================
Sarang Patel
3/23/2022

``` r
library(devtools)
```

    ## Loading required package: usethis

``` r
library(tidyverse)
```

    ## ── Attaching packages ─────────────────────────────────────── tidyverse 1.3.1 ──

    ## ✓ ggplot2 3.3.6     ✓ purrr   0.3.4
    ## ✓ tibble  3.1.5     ✓ dplyr   1.0.7
    ## ✓ tidyr   1.1.4     ✓ stringr 1.4.0
    ## ✓ readr   2.1.1     ✓ forcats 0.5.1

    ## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ## x dplyr::filter() masks stats::filter()
    ## x dplyr::lag()    masks stats::lag()

``` r
library(dplyr)
library(corrplot)
```

    ## corrplot 0.92 loaded

<https://github.com/sarangpmr/bball/>

# Package Setup

## Question 1

The three functions have been created and added to an R package
(following the processes in “Intro to R package….R”). They can be found
in the public repo
[HERE](https://github.com/sarangpmr/bball/tree/main/R). There are three
functions total: \* Function 1: lebronPPG.R + This function takes the
PPG for Lebron James for a given NBA season (one of the seasons that he
has played). \* Function 2: oldestPlayer.R + This function returns the
oldest player for a given NBA season. \* Function 3: corrNum.R + This
function returns the correlation matrix for all numeric variables in a
given year.

## Question 2

The package has been created.

## Question 3

The package has been uploaded to Github (correctly, this time). It can
be found [HERE](https://github.com/sarangpmr/bball/).

# Package Usage

## Question 4

Let’s now install the package in R.

``` r
install_github("sarangpmr/bball")
```

    ## Skipping install of 'bball' from a github remote, the SHA1 (ad6feba8) has not changed since last install.
    ##   Use `force = TRUE` to force installation

``` r
library(bball)
```

## Question 5

Let’s now run each of the functions and make sure they are working
correctly.

Testing out that the .Rda file correctly imports a data frame:

``` r
# test out the .Rda file works correctly and returns a data frame.
data(nba)
class(nba)
```

    ## [1] "data.frame"

``` r
head(nba, 10)
```

    ##     X year          player pos age  tm  g gs mp per    ts x3p_ar  f_tr orb drb
    ## 1   1 1950 Curly Armstrong G-F  31 FTW 63 NA NA  NA 0.368     NA 0.467  NA  NA
    ## 2   2 1950    Cliff Barker  SG  29 INO 49 NA NA  NA 0.435     NA 0.387  NA  NA
    ## 3   3 1950   Leo Barnhorst  SF  25 CHS 67 NA NA  NA 0.394     NA 0.259  NA  NA
    ## 4   4 1950      Ed Bartels   F  24 TOT 15 NA NA  NA 0.312     NA 0.395  NA  NA
    ## 5   5 1950      Ed Bartels   F  24 DNN 13 NA NA  NA 0.308     NA 0.378  NA  NA
    ## 6   6 1950      Ed Bartels   F  24 NYK  2 NA NA  NA 0.376     NA 0.750  NA  NA
    ## 7   7 1950     Ralph Beard   G  22 INO 60 NA NA  NA 0.422     NA 0.301  NA  NA
    ## 8   8 1950      Gene Berce G-F  23 TRI  3 NA NA  NA 0.275     NA 0.313  NA  NA
    ## 9   9 1950   Charlie Black F-C  28 TOT 65 NA NA  NA 0.346     NA 0.395  NA  NA
    ## 10 10 1950   Charlie Black F-C  28 FTW 36 NA NA  NA 0.362     NA 0.480  NA  NA
    ##    trb ast stl blk tov usg blanl  ows  dws   ws ws_48 blank2 obpm dbpm bpm vorp
    ## 1   NA  NA  NA  NA  NA  NA    NA -0.1  3.6  3.5    NA     NA   NA   NA  NA   NA
    ## 2   NA  NA  NA  NA  NA  NA    NA  1.6  0.6  2.2    NA     NA   NA   NA  NA   NA
    ## 3   NA  NA  NA  NA  NA  NA    NA  0.9  2.8  3.6    NA     NA   NA   NA  NA   NA
    ## 4   NA  NA  NA  NA  NA  NA    NA -0.5 -0.1 -0.6    NA     NA   NA   NA  NA   NA
    ## 5   NA  NA  NA  NA  NA  NA    NA -0.5 -0.1 -0.6    NA     NA   NA   NA  NA   NA
    ## 6   NA  NA  NA  NA  NA  NA    NA  0.0  0.0  0.0    NA     NA   NA   NA  NA   NA
    ## 7   NA  NA  NA  NA  NA  NA    NA  3.6  1.2  4.8    NA     NA   NA   NA  NA   NA
    ## 8   NA  NA  NA  NA  NA  NA    NA -0.1  0.0 -0.1    NA     NA   NA   NA  NA   NA
    ## 9   NA  NA  NA  NA  NA  NA    NA -2.2  5.0  2.8    NA     NA   NA   NA  NA   NA
    ## 10  NA  NA  NA  NA  NA  NA    NA -0.7  2.2  1.5    NA     NA   NA   NA  NA   NA
    ##     fg fga  fg_2 x3p x3pa x3p_2 x2p x2pa x2p_2  e_fg  ft fta  ft_2 orb_2 drb_2
    ## 1  144 516 0.279  NA   NA    NA 144  516 0.279 0.279 170 241 0.705    NA    NA
    ## 2  102 274 0.372  NA   NA    NA 102  274 0.372 0.372  75 106 0.708    NA    NA
    ## 3  174 499 0.349  NA   NA    NA 174  499 0.349 0.349  90 129 0.698    NA    NA
    ## 4   22  86 0.256  NA   NA    NA  22   86 0.256 0.256  19  34 0.559    NA    NA
    ## 5   21  82 0.256  NA   NA    NA  21   82 0.256 0.256  17  31 0.548    NA    NA
    ## 6    1   4 0.250  NA   NA    NA   1    4 0.250 0.250   2   3 0.667    NA    NA
    ## 7  340 936 0.363  NA   NA    NA 340  936 0.363 0.363 215 282 0.762    NA    NA
    ## 8    5  16 0.313  NA   NA    NA   5   16 0.313 0.313   0   5 0.000    NA    NA
    ## 9  226 813 0.278  NA   NA    NA 226  813 0.278 0.278 209 321 0.651    NA    NA
    ## 10 125 435 0.287  NA   NA    NA 125  435 0.287 0.287 132 209 0.632    NA    NA
    ##    trb_2 ast_2 stl_2 blk_2 tov_2  pf pts
    ## 1     NA   176    NA    NA    NA 217 458
    ## 2     NA   109    NA    NA    NA  99 279
    ## 3     NA   140    NA    NA    NA 192 438
    ## 4     NA    20    NA    NA    NA  29  63
    ## 5     NA    20    NA    NA    NA  27  59
    ## 6     NA     0    NA    NA    NA   2   4
    ## 7     NA   233    NA    NA    NA 132 895
    ## 8     NA     2    NA    NA    NA   6  10
    ## 9     NA   163    NA    NA    NA 273 661
    ## 10    NA    75    NA    NA    NA 140 382

Testing out that the first function, lebronPPG():

``` r
# test out the first function, lebronPPG()
lebronPPG(2001) # this should return an error
```

    ## [1] "Error: LeBron did not play in this season! Please try a season between 2004 and 2017."

``` r
lebronPPG(2006)
```

    ## Adding missing grouping variables: `player`

    ## # A tibble: 1 × 5
    ## # Groups:   player [1]
    ##   player        year     g   pts   ppg
    ##   <chr>        <int> <int> <int> <dbl>
    ## 1 LeBron James  2006    79  2478  31.4

Testing out the second function, oldestPlayer():

``` r
oldestPlayer(1990)
```

    ## # A tibble: 1 × 3
    ## # Groups:   year [1]
    ##    year player           age
    ##   <int> <chr>          <int>
    ## 1  1990 Caldwell Jones    39

Testing out the third function, corrNum():

``` r
corrNum(2006)
```

    ## Warning in cor(data, use = "pairwise.complete.obs"): the standard deviation is
    ## zero

![](Lab5_files/figure-gfm/unnamed-chunk-6-1.png)<!-- -->
