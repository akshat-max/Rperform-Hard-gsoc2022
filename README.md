# Rperform-Hard-gsoc2022


A version of this package for your version of R might be available elsewhere
#  Rperfom tests
This repository contains the solution for the hard tests of the project "Rperform" of GSOC 2022.

## Installation
To install the package we can follow:
```R
install.packages("devtools")
require("devtools")
devtools::install_github("analyticalmonk/Rperform")
```

## Installation issue 
After some checks I found that there was a problem, So I need to force install it  
```R
Skipping install of 'Rperform' from a github remote, the SHA1 (11c8cf49) has not changed since last install.
  Use `force = TRUE` to force installation
```

## Tests execution
Now that the package is installed we can execute the `time_compare()` to obtain the runtime details of a test file and testthat blocks over a specified number of commits. After downloading the source [nc](https://github.com/tdhock/nc/pulls?q=is%3Apr+) from CRAN we can execute the following funciton.

```R
setwd("path/to/nc")
library(Rperform)
time_compare(test_path = "tests/testthat/test-engine.r", num_commits = 2)
```


#### Error
Error in base::substr(commit_val@summary, start = 1, stop = 15) : 
trying to get slot "summary" from an object (class "git_commit") that is not an S4 object

#### Solution

This error occurred due to the breaking changes that had happened to git2r sometime back due to them switching to S3 objects from S4. The latest git2r version that Rperform will work with is 0.21.0.

is was temporary fixed, via modifing the DESCRIPTION file but it was not enough, so we need to fix breaking changes that had happened to git2r due to switching to S3 objects from S4.

  



