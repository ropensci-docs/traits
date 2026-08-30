# Search for gene sequences available for taxa from NCBI.

Search for gene sequences available for taxa from NCBI.

## Usage

``` r
ncbi_searcher(
  taxa = NULL,
  id = NULL,
  seqrange = "1:3000",
  getrelated = FALSE,
  fuzzy = FALSE,
  limit = 500,
  entrez_query = NULL,
  hypothetical = FALSE,
  verbose = TRUE,
  sleep = 0L
)
```

## Arguments

- taxa:

  (character) Scientific name to search for.

- id:

  (`character`) Taxonomic id to search for. Not compatible with argument
  `taxa`.

- seqrange:

  (character) Sequence range, as e.g., `"1:1000"`. This is the range of
  sequence lengths to search for. So `"1:1000"` means search for
  sequences from 1 to 1000 characters in length.

- getrelated:

  (logical) If `TRUE`, gets the longest sequences of a species in the
  same genus as the one searched for. If `FALSE`, returns nothing if no
  match found.

- fuzzy:

  (logical) Whether to do fuzzy taxonomic ID search or exact search. If
  `TRUE`, we use `xXarbitraryXx[porgn:__txid<ID>]`, but if `FALSE`, we
  use `txid<ID>`. Default: `FALSE`

- limit:

  (`numeric`) Number of sequences to search for and return. Max of
  10,000. If you search for 6000 records, and only 5000 are found, you
  will of course only get 5000 back.

- entrez_query:

  (`character`; length 1) An Entrez-format query to filter results with.
  This is useful to search for sequences with specific characteristics.
  The format is the same as the one used to seach genbank.
  (<https://www.ncbi.nlm.nih.gov/books/NBK3837/#EntrezHelp.Entrez_Searching_Options>)

- hypothetical:

  (`logical`; length 1) If `FALSE`, an attempt will be made to not
  return hypothetical or predicted sequences judging from accession
  number prefixs (XM and XR). This can result in less than the `limit`
  being returned even if there are more sequences available, since this
  filtering is done after searching NCBI.

- verbose:

  (logical) If `TRUE` (default), informative messages printed.

- sleep:

  (integer) number of seconds to sleep before each HTTP request. use if
  running to 429 Too Many Requests errors from NCBI. default: 0 (no
  sleep)

## Value

`data.frame` of results if a single input is given. A list of
`data.frame`s if multiple inputs are given.

## Authentication

NCBI rate limits requests. If you set an API key you have a higher rate
limit. Set your API key like `Sys.setenv(ENTREZ_KEY="yourkey")` or you
can use
[`?rentrez::set_entrez_key`](https://docs.ropensci.org/rentrez/reference/set_entrez_key.html).
set verbose curl output
([`crul::set_verbose()`](https://docs.ropensci.org/crul/reference/crul-options.html))
to make sure your api key is being sent in the requests

## See also

[`ncbi_byid`](https://docs.ropensci.org/traits/reference/ncbi_byid.md),
[`ncbi_byname`](https://docs.ropensci.org/traits/reference/ncbi_byname.md)

## Author

Scott Chamberlain, Zachary Foster <zacharyfoster1989@gmail.com>

## Examples

``` r
# \donttest{
if (interactive()) {
  # A single species
  out <- ncbi_searcher(taxa = "Umbra limi", seqrange = "1:2000")
  # Get the same species information using a taxonomy id
  out <- ncbi_searcher(id = "75935", seqrange = "1:2000")
  # If the taxon name is unique, using the taxon name and id are equivalent
  all(ncbi_searcher(id = "75935") == ncbi_searcher(taxa = "Umbra limi"))
  # If the taxon name is not unique, use taxon id
  #  "266948" is the uid for the butterfly genus, but there is also a genus
  #  of orchids with the
  #  same name
  nrow(ncbi_searcher(id = "266948")) == nrow(ncbi_searcher(taxa = "Satyrium"))
  # get list of genes available, removing non-unique
  unique(out$gene_desc)
  # does the string 'RAG1' exist in any of the gene names
  out[grep("RAG1", out$gene_desc, ignore.case = TRUE), ]

  # A single species without records in NCBI
  out <- ncbi_searcher(taxa = "Sequoia wellingtonia", seqrange = "1:2000",
    getrelated = TRUE)

  # Many species, can run in parallel or not using plyr
  species <- c("Salvelinus alpinus", "Ictalurus nebulosus", "Carassius auratus")
  out2 <- ncbi_searcher(taxa = species, seqrange = "1:2000")
  lapply(out2, head)
  library("plyr")
  out2df <- ldply(out2) # make data.frame of all
  unique(out2df$gene_desc) # get list of genes available, removing non-unique
  out2df[grep("12S", out2df$gene_desc, ignore.case = TRUE), ]

  # Using the getrelated and entrez_query options
  ncbi_searcher(taxa = "Olpidiopsidales", limit = 5, getrelated = TRUE,
              entrez_query = "18S[title] AND 28S[title]")

  # get refseqs
  one <- ncbi_searcher(taxa = "Salmonella enterica",
    entrez_query = "srcdb_refseq[PROP]")
  two <- ncbi_searcher(taxa = "Salmonella enterica")
}
# }
```
