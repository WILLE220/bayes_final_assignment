# Final Assignment R Code

The associated `final_assignment.R` code generates all the plots, models, and figures that 
are needed for the Final Assignment submission.  Below is an overview of the code, how to 
use it, and what is generated by running this code.

## Installation

Ensure that there is an up-to-date R code installed on your machine (the code will also
generate a `sessionInfo()` object so that library variations and installation variations 
can be assessed post-hoc).

Code has been written and tested on `R` `4.4.1` compiled on `macOS` `14.5` with an `arm`
chip. Detailed instructions on how to install `R` can be found [here](https://cran.r-project.org/doc/FAQ/R-FAQ.html#How-can-R-be-obtained_003f).

If you're using [`RStudio`](https://posit.co/download/rstudio-desktop/), you can use
the following code to install all the needed libraries:

```R
pkgs <- rownames(installed.packages())
if (!("optparse" %in% pkgs)) install.packages(
  "optparse", repos = "https://cloud.r-project.org"
)
if (!("brms" %in% pkgs)) install.packages(
  "brms", repos = "https://cloud.r-project.org"
)
if (!("dplyr" %in% pkgs)) install.packages(
  "dplyr", repos = "https://cloud.r-project.org"
)
if (!("ggplot2" %in% pkgs)) install.packages(
  "ggplot2", repos = "https://cloud.r-project.org"
)
if (!("log4r" %in% pkgs)) install.packages(
  "log4r", repos = "https://cloud.r-project.org"
)
if (!("tidyverse" %in% pkgs)) install.packages(
  "tidyverse", repos = "https://cloud.r-project.org"
)
if (!("ggcorrplot" %in% pkgs)) install.packages(
  "ggcorrplot", repos = "https://cloud.r-project.org"
)
if (!("broom" %in% pkgs)) install.packages(
  "broom", repos = "https://cloud.r-project.org"
)
if (!("tidybayes" %in% pkgs)) install.packages(
  "tidybayes", repos = "https://cloud.r-project.org"
)
if (!("parallelly" %in% pkgs)) install.packages(
  "parallelly", repos = "https://cloud.r-project.org"
)
if (!("mgcv" %in% pkgs)) install.packages(
  "mgcv", repos = "https://cloud.r-project.org"
)
if (!("randomForest" %in% pkgs)) install.packages(
  "randomForest", repos = "https://cloud.r-project.org"
)
if (!("caret" %in% pkgs)) install.packages(
  "caret", repos = "https://cloud.r-project.org"
)
if (!("doParallel" %in% pkgs)) install.packages(
  "doParallel", repos = "https://cloud.r-project.org"
)
if (!("doSNOW" %in% pkgs)) install.packages(
  "doSNOW", repos = "https://cloud.r-project.org"
)
if (!("foreach" %in% pkgs)) install.packages(
  "foreach", repos = "https://cloud.r-project.org"
)
if (!("parallel" %in% pkgs)) install.packages(
  "parallel", repos = "https://cloud.r-project.org"
)
if (!("rsample" %in% pkgs)) install.packages(
  "rsample", repos = "https://cloud.r-project.org"
)
if (!("projpred" %in% pkgs)) install.packages(
  "projpred", repos = "https://cloud.r-project.org"
)
if (!("doRNG" %in% pkgs)) install.packages(
  "doRNG", repos = "https://cloud.r-project.org"
)
```

## Code Overview

The code expects a `BostonHousing.Rdata` file to exist somewhere on your machine, but 
the code can be run either via `Rscript` or interactively through RStudio.

Below are the important variables to set:

* `seed` - the random seed (integer)
* `draws` - the number of draws to run BRMS (integer)
* `output` - the output directory for the saving models and diagnostics
* `file` - the input `BostonHousing.RData` file
* `cores` - the number of cores to use (if set to 0 the program will parallelize
            across a reasonable number of cores)
* `holdout` - the percentage to holdout for prior model fitting and validation

An example of running the code via `Rscript` is below:

```bash
Rscript final_assignment.R --file BostonHousing.RData
```

This will set reasonable default arguments for all variables, but if you would
like to see this expanded to all default variables:

```bash
Rscript final_assignment.R --file BostonHousing.RData --seed 42 --draws 10000 --output . --cores 0 --holdout 0.1
```

There will be a number of log messages generated, but once the script is finished 
running you will result in a folder structure like:

```
(base) ➜  final_assignment tree .
.
├── README.md
├── BostonHousing.RData
├── analysis
│   ├── ...
├── final_assignment.R
├── bayes_models
│   ├── ...
├── diagnostics
│   ├── ...
```

The folders created are summarized below:

* `analysis` - overview data diagnostics and analytics 
* `bayes_models` - the `brms` models saved along with coefficients and LOO comparisons
* `diagnostics` - autocorrelation, trace, ppc, and coefficient plots
* `prior_models` - the models with just the priors sampled

### Maintainers

* Alex Lee (1586432)
* Okko Willeboordse (1307142)
* Karlijn de Kool (1414224)
* Miro Tanck (1048452)