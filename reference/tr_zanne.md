# Zanne et al. plant dataset

Zanne et al. plant dataset

## Usage

``` r
tr_zanne(read = TRUE, ...)
```

## Arguments

- read:

  (logical) read in csv files. Default: `TRUE`

- ...:

  Curl options passed on to
  [`crul::HttpClient()`](https://docs.ropensci.org/crul/reference/HttpClient.html)

## Value

paths to the files (character) if `read=FALSE` or a list of data.frame's
if `read=TRUE`

## Details

This data is a dataset stored on Dryad (doi: 10.5061/dryad.63q27). When
using this data, cite the paper:

Zanne AE, Tank DC, Cornwell WK, Eastman JM, Smith SA, FitzJohn RG,
McGlinn DJ, O'Meara BC, Moles AT, Reich PB, Royer DL, Soltis DE, Stevens
PF, Westoby M, Wright IJ, Aarssen L, Bertin RI, Calaminus A, Govaerts R,
Hemmings F, Leishman MR, Oleksyn J, Soltis PS, Swenson NG, Warman L,
Beaulieu JM, Ordonez A (2014) Three keys to the radiation of angiosperms
into freezing environments. Nature 506(7486): 89-92.
http://dx.doi.org/10.1038/nature12872

As well as the Dryad data package:

Zanne AE, Tank DC, Cornwell WK, Eastman JM, Smith SA, FitzJohn RG,
McGlinn DJ, O'Meara BC, Moles AT, Reich PB, Royer DL, Soltis DE, Stevens
PF, Westoby M, Wright IJ, Aarssen L, Bertin RI, Calaminus A, Govaerts R,
Hemmings F, Leishman MR, Oleksyn J, Soltis PS, Swenson NG, Warman L,
Beaulieu JM, Ordonez A (2013) Data from: Three keys to the radiation of
angiosperms into freezing environments. Dryad Digital Repository.
http://dx.doi.org/10.5061/dryad.63q27.2

## References

http://datadryad.org/resource/doi:10.5061/dryad.63q27

## Examples

``` r
# \donttest{
if (interactive()) {
  res <- tr_zanne()
  res$tax_lookup
  res$woodiness
  res$freezing
  res$leaf_phenology
}
# }
```
