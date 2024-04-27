# **FATools R Package Development Notes**

### Package Description

* The goal of FATools is to leverage the power of R to make the analysis of fatty acid (FA) data streamlined and reproducable.

* The package should contain functions commonly used to process, analyze, and plot FA data that results from chromatographic analyses. 

* These functions should allow for reproducible and traceable FA analyses and promote consistency in the work-products generated from the CTEL Biomarker Lab. 

* The functions are written in R and are intended to be used in R, however, they may be incorporated into bash scripts so they can be used by non-R users. 

### Pacakge Notes

I don't know if this doc should be included in the main repo, made into its own repo, or kept private. Figure this out. 

Overall, package documentation sucks and really needs to be reworked once the core functions are working.

# **Functions in Package**

## pretty_fa_names()

Function that accepts FA names in a variety of formats and will interconvert them between several supported standardized ways of writing FA names.

* ~~Needs a new name. Make it singular. Maybe change it to convert_fa_name().~~
* Needs to be more throughly tested. Someone should write some tests. 
* Need to add some error checking. Use regex to look for unusual chars or unusual formats. Return which FA are problematic so user can fix them. 

## find_fa_name()

Function to search through vector for fatty acid names. Returns a vector of indexes.

* Should this have any options to return different values?

```r

find_fa_name <- function(x) {
  # do tha thang
  grep("[1-9]?[0-9][[:punct:]][0-9][1-9]?", x)
}

```

# **Functions To Add**

## calc_gc_response_factor()

Function takes cross-tab file of peak area results from external standards and creates an array containing FA names & RF. 

```r
calc_gc_response_factor <- function(ext_std_areas, compound_table) {
    # Do some stuff.
}

# uses find_fa_name() to ID which columns to perform calculations on 

# calls pretty_fa_names() on FA columns to standardize FA names.

# calculates linear model using peak area & FA concentration in external standard to calculate instrument response factors. 

# returns a dataframe with FA & RF values
```

## convert_area_to_conc()
Function to post-process GCMS data and convert peak areas into FAME concentrations.

```r
convert_area_to_conc <- function() {
    # Do tha thang.
}

# read in raw gcms output (peak areas)

# split data into two sections:
    # external standards
    # analytical samples

# calculate response factors on external samples
    # calls pretty_fa_names() to standardize
    # uses linear model with 0 intercept
    # 
```

## adjust_conc_for_tissue_mass()
Function to take FAME concentrations and adjust them for the amount of tissue extracted. Also needs to account for the fraction of lipid extract processed for derivatization. 

```r
adjust_conc_for_tissue_mass <- function() {
    # doit.
}
```

## convert_result_to_prop()
Function to convert concentrations into proportions. Basically all it needs to do is divide each FA concentration value by the sum of the row.

* This could even be used for peak areas, not just concentrations. 

```r
convert_result_to_prop <- function() {
    # doit.
}
```

# **R Package Development Resources**

[R Packages e-book](https://r-pkgs.org/whole-game.html)

[Tidy Design Principles](https://design.tidyverse.org/)

[Tidyverse Style Guide](https://style.tidyverse.org/functions.html)

[CRAN Repository Policy](https://cran.r-project.org/)

[GitHub Documentation](https://docs.github.com/en/get-started)

[Git Book](https://git-scm.com/book/en/v2)

[Git Visual Cheatsheet](https://ndpsoftware.com/git-cheatsheet.html#loc=workspace;)


# **Collaboration Guidelines**

[GitHub](https://github.com/miketommus/FATools) will be the main repository and "source of truth" for the project.

All dev work should be done on branches and then a pull request used to merge with master branch. 

Use of Git locally on your computer for version control is highly recommended. In order to keep the commit history clean, please use the [The Repeated Amend](https://happygitwithr.com/repeated-amend) technique and only push commis to the GitHub repo that represent a unified chunk of work. 

Clean, easy-to-read & maintain code. Minimize dependencies. 




