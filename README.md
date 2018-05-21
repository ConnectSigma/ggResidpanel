
ggResidpanel <img align="right" width="120" height="135" src="./images/gg_resid_sticker4.png">
==============================================================================================

ggResidpanel is an R package for creating panels of diagnostic plots for residuals from a model using ggplot2 and interactive versions of the plots using plotly.

Overview
--------

The package provides three functions that allow the user to assess diagnostic plots of residuals from a model.

**`resid_panel`** This function creates a panel of residual diagnostic plots given a model of type "lm", "glm", "lmerMod", and "glmerMod". It allows the user to select a panel of plots from the options in the package or create their own panel by selecting from the plots available for this function.

**`resid_auxpanel`**: This function creates a panel of residual diagnostic plots given inputs of residuals and fitted values to use for models not accepted by `resid_panel`. Users can select the "SAS" panel option or create their own panel from the plots available for this function.

**`resid_interact`**: This function creates interactive versions of residual diagnostic plots given a model. It accepts models of type "lm", "glm", "lmerMod", and "glmerMod". It allows the user to select one plot to make interactive from the plots available for this function.

Below are the descriptions of the plots currently available. (Note that not all plots are available for all model types.)

-   `"boxplot"`: A boxplot of residuals
-   `"cookd"`: A plot of Cook's D values versus observation numbers
-   `"hist"`: A histogram of residuals (optional number of bins)
-   `"ls"`: A location-scale plot of residuals
-   `"qq"`: A normal quantile plot of residuals (optional confidence bands)
-   `"lev"`: A plot of leverage values versus residuals
-   `"resid"`: A plot of residuals versus predicted values (optional smoother)
-   `"yvp"`: A plot of observed response values versus predicted values

The package allows for the formatting options of `scale`, `theme`, `axis.text.size`, `title.text.size`, `title.opt`.

See the documentation for more details.

Installation
------------

Follow these instructions to install ggResidpanel.

Install the package devtools (if not already installed).

``` r
install.packages("devtools")
```

Load the devtools library.

``` r
library(devtools)
```

Install ggResidpanel from the GitHub repository.

``` r
devtools::install_github("goodekat/ggResidpanel")
```

Examples
--------

``` r
# Load the library
library(ggResidpanel)

# Fit a linear model
lm_model <- lm(Volume ~ Girth, data = trees)

# Create the default panel of plots
resid_panel(lm_model, bins = 20)
```

![](README_files/figure-markdown_github-ascii_identifiers/unnamed-chunk-4-1.png)

``` r
# Create the R panel of plots and change the theme to classic
resid_panel(lm_model, bins = 20, plots = "R", theme = "classic")
```

![](README_files/figure-markdown_github-ascii_identifiers/unnamed-chunk-4-2.png)

``` r
# Create a panel with all plots available
resid_panel(lm_model, plots = "all", bins = 20)
```

![](README_files/figure-markdown_github-ascii_identifiers/unnamed-chunk-4-3.png)

``` r
# Fit a glme model using a Poisson family
glm_model <- glm(count ~ spray, family = "poisson", data = InsectSprays)

# Specify three plots to use, request no title, change the theme to gray, and 
# indicate three columns
resid_panel(glm_model, plots = c("resid", "qq", "hist"), bins = 20, 
            title.opt = FALSE, theme = "gray", ind.ncol = 3)
```

![](README_files/figure-markdown_github-ascii_identifiers/unnamed-chunk-5-1.png)
