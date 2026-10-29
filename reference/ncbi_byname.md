# Retrieve gene sequences from NCBI by taxon name and gene names.

Retrieve gene sequences from NCBI by taxon name and gene names.

## Usage

``` r
ncbi_byname(
  taxa,
  gene = "COI",
  seqrange = "1:3000",
  getrelated = FALSE,
  verbose = TRUE,
  batch_size = 100,
  ...
)
```

## Arguments

- taxa:

  (character) Scientific name to search for.

- gene:

  (character) Gene or genes (in a vector) to search for. See examples.

- seqrange:

  (character) Sequence range, as e.g., `"1:1000"`. This is the range of
  sequence lengths to search for. So `"1:1000"` means search for
  sequences from 1 to 1000 characters in length.

- getrelated:

  (logical) If `TRUE`, gets the longest sequences of a species in the
  same genus as the one searched for. If `FALSE`, returns nothing if no
  match found.

- verbose:

  (logical) If `TRUE` (default), informative messages printed.

- batch_size:

  An integer specifying the number of names to query per batch.

- ...:

  Curl options passed on to
  [crul::verb-GET](https://docs.ropensci.org/crul/reference/verb-GET.html)

## Value

data.frame

## Details

Removes predicted sequences so you don't have to remove them. Predicted
sequences are those with accession numbers that have "XM\_" or "XR\_"
prefixes. This function retrieves one sequences for each species,
picking the longest available for the given gene.

## See also

[`ncbi_searcher()`](https://docs.ropensci.org/traits/reference/ncbi_searcher.md),
[`ncbi_byid()`](https://docs.ropensci.org/traits/reference/ncbi_byid.md)

## Author

Scott Chamberlain

## Examples

``` r
# \donttest{
if (interactive()) {
  # A single species
  ncbi_byname(taxa = "Acipenser brevirostrum")

  # Many species
  species <- c("Colletes similis", "Halictus ligatus", "Perdita californica")
  ncbi_byname(taxa = species, gene = c("coi", "co1"), seqrange = "1:2000")
}
# }
```
