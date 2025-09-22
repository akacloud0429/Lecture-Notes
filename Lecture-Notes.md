Lecture Notes
================
Luyun Ge
2025-09-21

- [Lecture 4 (Sep.16)](#lecture-4-sep16)
  - [Paths](#paths)
  - [Update the names of variables in `litters_df` (to remove capital
    and space
    between)](#update-the-names-of-variables-in-litters_df-to-remove-capital-and-space-between)
  - [Learning Assessment (CSV files)](#learning-assessment-csv-files)
  - [Use function without downloading the whole
    package](#use-function-without-downloading-the-whole-package)
  - [Fixing the missing datas](#fixing-the-missing-datas)
  - [Importing Data from EXCEL file](#importing-data-from-excel-file)
  - [Importing Data from SAS file](#importing-data-from-sas-file)
  - [Data Export](#data-export)

# Lecture 4 (Sep.16)

This lecture is about Data Wrangling - Data Import and Export

``` r
library(tidyverse)
```

## Paths

- absolute path: the full address of file on computer; cons: not
  portable

``` r
litters_df = 
  read_csv("~/Desktop/Fall2025/P8105 DS I/data_import_examples/FAS_litters.csv", na = c("NA",".",""))
#setwd() is also an absolute path
```

- relative path: directions to a file or folder from your current
  working directory; **portable**

``` r
litters_df_relative = 
  read_csv("../../data_import_examples/FAS_litters.csv", na = c("NA",".",""))
# ../.. Two directories up from current working directory
```

## Update the names of variables in `litters_df` (to remove capital and space between)

``` r
names(litters_df)
```

    ## [1] "Group"             "Litter Number"     "GD0 weight"       
    ## [4] "GD18 weight"       "GD of Birth"       "Pups born alive"  
    ## [7] "Pups dead @ birth" "Pups survive"

``` r
litters_df = 
  janitor::clean_names(litters_df)
names(litters_df)
## [1] "group"           "litter_number"   "gd0_weight"      "gd18_weight"    
## [5] "gd_of_birth"     "pups_born_alive" "pups_dead_birth" "pups_survive"
```

## Learning Assessment (CSV files)

Now importing the FAS_pups dataset:

``` r
pups_df = 
  read_csv("~/Desktop/Fall2025/P8105 DS I/data_import_examples/FAS_pups.csv", na = c("NA",".",""),skip = 3)
pups_df_relative = 
  read_csv("../../data_import_examples/FAS_pups.csv",na = c("NA",".",""),skip = 3)
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
# na will treat "NA", ".", "" as missing values
litters_df = 
  read_csv("~/Desktop/Fall2025/P8105 DS I/data_import_examples/FAS_litters.csv", na = c("NA",".",""), skip = 10)
```

## Importing Data from EXCEL file

``` r
mlb_df = 
  readxl::read_excel("../../data_import_examples/mlb11.xlsx")
```

If we only want part of columns

``` r
words_df = 
  readxl::read_excel("../../data_import_examples/LotR_Words.xlsx", range = "B3:D6")
```

## Importing Data from SAS file

``` r
pulse_df = 
  haven::read_sas("../../data_import_examples/public_pulse_data.sas7bdat")
names(pulse_df)
## [1] "ID"           "age"          "Sex"          "BDIScore_BL"  "BDIScore_01m"
## [6] "BDIScore_06m" "BDIScore_12m"
```

Clean the variable names:

``` r
pulse_df = janitor::clean_names(pulse_df)
names(pulse_df)
## [1] "id"            "age"           "sex"           "bdi_score_bl" 
## [5] "bdi_score_01m" "bdi_score_06m" "bdi_score_12m"
```

## Data Export

``` r
write.csv(words_df,"../../data_import_examples/words_df") 
```
