# NBA Player Statistics Package

## Introduction

This package is designed to return specific datapoints on NBA players, given various year inputs. 


### Packaged Functions

``lebronPPG()`` 

Returns the points-per-game (PPG) for Lebron James from a single season defined by the `year` input.

``oldestPlayer():`` 

Returns the oldest player in the NBA from a single season defined by the `year` input.

``corrNum()`` 

Returns the correlation matrix for all numeric variables in a season defined by the `year` input.

### Example Usage

```
library(bball)

# get Lebron James' PPG in 2006
lebronPPG(2006)

# A tibble: 1 × 5
# Groups:   player [1]
  player        year     g   pts   ppg
  <chr>        <int> <int> <int> <dbl>
1 LeBron James  2006    79  2478  31.4

```
