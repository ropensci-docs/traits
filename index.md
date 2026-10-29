# traits: Species Trait Data from Around the Web

# traits

[![R-CMD-check](https://github.com/ropensci/traits/actions/workflows/R-CMD-check.yaml/badge.svg)](https://github.com/ropensci/traits/actions/workflows/R-CMD-check.yaml)
[![rstudio mirror
downloads](https://cranlogs.r-pkg.org/badges/traits)](https://github.com/r-hub/cranlogs.app)
[![cran
version](https://www.r-pkg.org/badges/version/traits)](https://CRAN.R-project.org/package=traits)
[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.11224037.svg)](https://doi.org/10.5281/zenodo.11224037)

R client for various sources of species trait data.

Docs: <https://docs.ropensci.org/traits/>

What is a trait? A “trait” for the purposes of this package is broadly
defined as an aspect of a species that can be described or measured,
such as physical traits (size, length, height, color), behavioral traits
(running speed, etc.), and even variables that make up the niche of the
species (e.g., habitat).

Included in `traits` with the associated function prefix or function
name:

| Source | Function prefix | Link |
|:---|:---|:---|
| BETYdb | `betydb_` | <https://www.betydb.org/> |
| NCBI | `ncbi_` | <https://www.ncbi.nlm.nih.gov/> |
| Encyclopedia of Life | `traitbank_` | <https://github.com/EOL/publishing/blob/master/doc/api.md> |
| Birdlife International | `birdlife_` | <https://www.birdlife.org/> |
| LEDA Traitbase | `leda_` |  |
| Zanne et al. plant dataset | `tr_zanne` |  |
| Amniote life history dataset | `tr_ernest` |  |

Talk to us on the issues page
(<https://github.com/ropensci/traits/issues>) if you know of a source of
traits data with an API, and we’ll see about including it.

## Installation

CRAN

``` r

install.packages("traits")
```

R-Universe (alternative)

``` r

install.packages(
  "traits",
  repos = c("https://ropensci.r-universe.dev", "https://cloud.r-project.org")
)
```

Development version from GitHub

``` r

remotes::install_github("ropensci/traits")
```

``` r

library("traits")
library("dplyr")
```

## Contributors

- [Scott Chamberlain](https://github.com/sckott)
- [Zachary Foster](https://github.com/zachary-foster)
- [Ignasi Bartomeus](https://github.com/ibartomeus)
- [David LeBauer](https://github.com/dlebauer)
- [David Harris](https://github.com/davharris)
- [Chris Black](https://github.com/infotroph)
- [Rupert Collins](https://github.com/boopsboops)

## Meta

- Please [report any issues or
  bugs](https://github.com/ropensci/traits/issues).
- License: MIT
- Get citation information for `traits` in R doing
  `citation(package = 'traits')`
- Please note that this package is released with a [Contributor Code of
  Conduct](https://ropensci.org/code-of-conduct/). By contributing to
  this project, you agree to abide by its terms.
