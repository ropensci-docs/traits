# Search for traits from EOL's Traitbank

Search for traits from EOL's Traitbank

## Usage

``` r
traitbank(query, key = NULL, ...)
```

## Arguments

- query:

  (character) a query to the EOL Cypher service that holds Traitbank
  data. required. no default query given. see examples

- key:

  (character) EOL Cypher query API key. required, either passed in or as
  an environment variable

- ...:

  Curl options passed on to
  [`verb-GET`](https://docs.ropensci.org/crul/reference/verb-GET.html)

## Value

a list

## Details

`traitbank` is an interface to the EOL Cypher query. Note that the
previous interface EOL had for Traits has been completely replaced -
thus, this function is completely different. You no longer query by EOL
page id, but using the query language for a database called Neo4J. See
the docs for help. Later we plan to make a more user friendly interface
to get Traitbank data that doesn't require knowing the Neo4J query
syntax

## Authentication

You'll need an EOL cypher key to use this function. Get one by signing
in to your EOL account https://eol.org/users/sign_in then head to
https://eol.org/services/authenticate to get a key. Store your key in
your .Renviron file or similar under the name "EOL_CYPHER_KEY", and we
will use that key in this function. Alternatively, you can pass in your
key to the key parameter, but we do not recommend doing that as you risk
accidentally committing your key to the public web.

## References

https://github.com/EOL/eol_website/blob/master/doc/api.md
https://github.com/EOL/eol_website/blob/master/doc/query-examples.md

## Examples

``` r
# \donttest{
if (interactive()) {
  # traitbank_query function
  traitbank(query = "MATCH (n:Trait) RETURN n LIMIT 1;")

  # traitbank function
  res <- traitbank(query = "MATCH (n:Trait) RETURN n LIMIT 2;")
  res
}
# }
```
