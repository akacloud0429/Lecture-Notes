Lecture Notes
================
Luyun Ge
2025-09-21

- [Lecture 4 (Sep.16)](#lecture-4-sep16)
  - [Paths](#paths)
  - [Update the names of variables in `litters_df` (to remove capital
    and space
    between)](#update-the-names-of-variables-in-litters_df-to-remove-capital-and-space-between)
  - [Learning Assessment](#learning-assessment)
  - [Use function without downloading the whole
    package](#use-function-without-downloading-the-whole-package)
  - [Fixing the missing datas](#fixing-the-missing-datas)

# Lecture 4 (Sep.16)

``` r
library(tidyverse)
```

    ## ── Attaching core tidyverse packages ──────────────────────── tidyverse 2.0.0 ──
    ## ✔ dplyr     1.1.4     ✔ readr     2.1.5
    ## ✔ forcats   1.0.0     ✔ stringr   1.5.1
    ## ✔ ggplot2   3.5.2     ✔ tibble    3.3.0
    ## ✔ lubridate 1.9.4     ✔ tidyr     1.3.1
    ## ✔ purrr     1.1.0     
    ## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ## ✖ dplyr::filter() masks stats::filter()
    ## ✖ dplyr::lag()    masks stats::lag()
    ## ℹ Use the conflicted package (<http://conflicted.r-lib.org/>) to force all conflicts to become errors

## Paths

- absolute path: the full address of file on computer; cons: not
  portable

``` r
litters_df = 
  read_csv("~/Desktop/Fall2025/P8105 DS I/data_import_examples/FAS_litters.csv")
## Rows: 49 Columns: 8
## ── Column specification ────────────────────────────────────────────────────────
## Delimiter: ","
## chr (4): Group, Litter Number, GD0 weight, GD18 weight
## dbl (4): GD of Birth, Pups born alive, Pups dead @ birth, Pups survive
## 
## ℹ Use `spec()` to retrieve the full column specification for this data.
## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.
#setwd() is also an absolute path
```

- relative path: directions to a file or folder from your current
  working directory; **portable**

``` r
litters_df_relative = 
  read_csv("../../data_import_examples/FAS_litters.csv")
## Rows: 49 Columns: 8
## ── Column specification ────────────────────────────────────────────────────────
## Delimiter: ","
## chr (4): Group, Litter Number, GD0 weight, GD18 weight
## dbl (4): GD of Birth, Pups born alive, Pups dead @ birth, Pups survive
## 
## ℹ Use `spec()` to retrieve the full column specification for this data.
## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.
# ../.. Two directories up from current working directory
```

``` r
names(litters_df)
```

    ## [1] "Group"             "Litter Number"     "GD0 weight"       
    ## [4] "GD18 weight"       "GD of Birth"       "Pups born alive"  
    ## [7] "Pups dead @ birth" "Pups survive"

## Update the names of variables in `litters_df` (to remove capital and space between)

``` r
litters_df = 
  janitor::clean_names(litters_df)
names(litters_df)
## [1] "group"           "litter_number"   "gd0_weight"      "gd18_weight"    
## [5] "gd_of_birth"     "pups_born_alive" "pups_dead_birth" "pups_survive"
```

## Learning Assessment

Now importing the FAS_pups dataset:

``` r
pups_df = 
  read_csv("~/Desktop/Fall2025/P8105 DS I/data_import_examples/FAS_pups.csv", na = c("NA",".",""),skip = 3)
## Rows: 313 Columns: 6
## ── Column specification ────────────────────────────────────────────────────────
## Delimiter: ","
## chr (1): Litter Number
## dbl (5): Sex, PD ears, PD eyes, PD pivot, PD walk
## 
## ℹ Use `spec()` to retrieve the full column specification for this data.
## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.
pups_df_relative = 
  read_csv("../../data_import_examples/FAS_pups.csv",na = c("NA",".",""),skip = 3)
## Rows: 313 Columns: 6
## ── Column specification ────────────────────────────────────────────────────────
## Delimiter: ","
## chr (1): Litter Number
## dbl (5): Sex, PD ears, PD eyes, PD pivot, PD walk
## 
## ℹ Use `spec()` to retrieve the full column specification for this data.
## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.
```

``` r
# to view the data
skimr::skim(litters_df)
```

## Use function without downloading the whole package

`package`:`function`

``` r
dplyr::filter
stats::filter
```

## Fixing the missing datas

``` r
litters_df = 
  read_csv("~/Desktop/Fall2025/P8105 DS I/data_import_examples/FAS_litters.csv", na = c("NA",".",""), skip = 10)
```

    ## New names:
    ## Rows: 39 Columns: 8
    ## ── Column specification
    ## ──────────────────────────────────────────────────────── Delimiter: "," chr
    ## (2): Con8, #3/5/2/2/95 dbl (6): 28.5, NA, 20, 8...6, 0, 8...8
    ## ℹ Use `spec()` to retrieve the full column specification for this data. ℹ
    ## Specify the column types or set `show_col_types = FALSE` to quiet this message.
    ## • `8` -> `8...6`
    ## • `8` -> `8...8`
