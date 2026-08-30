# Search for traits by taxa names

Search for traits by taxa names

## Usage

``` r
taxa_search(x, db, ...)
```

## Arguments

- x:

  (character) Taxonomic name(s) to search for

- db:

  (character) only 'ncbi' for now - other options maybe in the future

- ...:

  Curl options passed on to
  [`GET`](https://httr.r-lib.org/reference/GET.html)

## Value

A `data.frame`

## Author

Scott Chamberlain

## Examples

``` r
# \donttest{
if (interactive()) {
  taxa_search("Poa annua", db = "ncbi")
}
# }
```
