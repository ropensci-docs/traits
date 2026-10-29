# Amniote life history dataset

Amniote life history dataset

## Usage

``` r
tr_ernest(read = TRUE, ...)
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

When using this data, cite the paper:

Myhrvold, N. P., Baldridge, E., Chan, B., Sivam, D., Freeman, D. L. and
Ernest, S. K. M. (2015), An amniote life-history database to perform
comparative analyses with birds, mammals, and reptiles. Ecology, 96:
3109. https://doi.org/10.1890/15-0846R.1

As well as the Dryad data package:

L. Freeman, Daniel; P. Myhrvold, Nathan; Chan, Benjamin; Sivam, Dhileep;
Ernest, S. K. Morgan; Baldridge, Elita (2016): Full Archive. figshare.
https://doi.org/10.6084/m9.figshare.3563457.v1

## References

https://doi.org/10.1890/15-0846R.1
https://doi.org/10.6084/m9.figshare.3563457.v1

## Examples

``` r
# \donttest{
if (interactive()) {
  res <- tr_ernest()
  res$data
  res$references
  res$sparse
  res$range_count
}
# }
```
