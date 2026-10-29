# Retrieve gene sequences from NCBI by accession number.

Retrieve gene sequences from NCBI by accession number.

## Usage

``` r
ncbi_byid(ids, format = NULL, verbose = TRUE)
```

## Arguments

- ids:

  (character) GenBank ids to search for. One or more. Required.

- format:

  (character) Return type, e.g., `"fasta"`. NOW IGNORED.

- verbose:

  (logical) If `TRUE` (default), informative messages printed.

## Value

data.frame of the form:

- taxon - taxonomic name (may include some junk, but hard to parse off)

- taxonomy - organism lineage

- gene_desc - gene description

- organelle - if mitochondrial or chloroplast

- gi_no - GI number

- acc_no - accession number

- keyword - if official DNA barcode

- specimen_voucher - museum/lab accession number of vouchered material

- lat_lon - longitude/latitude of specimen collection event

- country - country/location of specimen collection event

- paper_title - title of study

- journal - journal study published in (if published)

- first_author - first author of study

- uploaded_date - date sequence was uploaded to GenBank

- length - sequence length

- sequence - sequence character string

## Details

If bad ids are included with good ones, the bad ones are silently
dropped. If all ids are bad you'll get a stop with error message.

## See also

[`ncbi_searcher()`](https://docs.ropensci.org/traits/reference/ncbi_searcher.md),
ncbi_byname()\]

## Author

Scott Chamberlain, Rupert Collins

## Examples

``` r
# \donttest{
if (interactive()) {
  # A single gene
  ncbi_byid(ids = "360040093")

  # Many genes (with different accession numbers)
  ncbi_byid(ids = c("360040093", "347448433"))
}
# }
```
