# Search for traits from BETYdb

Search for traits from BETYdb

Get details about a single item from a table

## Usage

``` r
betydb_record(
  id,
  table,
  api_version = NULL,
  betyurl = NULL,
  fmt = NULL,
  key = NULL,
  user = NULL,
  pwd = NULL,
  progress = TRUE,
  ...
)

betydb_trait(
  id,
  genus = NULL,
  species = NULL,
  api_version = NULL,
  betyurl = NULL,
  fmt = "json",
  key = NULL,
  user = NULL,
  pwd = NULL,
  progress = TRUE,
  ...
)

betydb_specie(
  id,
  genus = NULL,
  species = NULL,
  api_version = NULL,
  betyurl = NULL,
  fmt = "json",
  key = NULL,
  user = NULL,
  pwd = NULL,
  progress = TRUE,
  ...
)

betydb_citation(
  id,
  genus = NULL,
  species = NULL,
  api_version = NULL,
  betyurl = NULL,
  fmt = "json",
  key = NULL,
  user = NULL,
  pwd = NULL,
  progress = TRUE,
  ...
)

betydb_site(
  id,
  api_version = NULL,
  betyurl = NULL,
  fmt = "json",
  key = NULL,
  user = NULL,
  pwd = NULL,
  progress = TRUE,
  ...
)

betydb_experiment(
  id,
  api_version = NULL,
  betyurl = NULL,
  fmt = "json",
  key = NULL,
  user = NULL,
  pwd = NULL,
  progress = TRUE,
  ...
)
```

## Arguments

- id:

  (integer) One or more ids for a species, site, variable, etc.

- table:

  (character) Name of the database table with which this ID is
  associated.

- api_version:

  (character) Which version of the BETY API should we query? One of "v0"
  or "beta". Default is `options("betydb_api_version")` if set,
  otherwise "v0".

- betyurl:

  (string) URL to target BETYdb. Default is `"https://www.betydb.org/"`.
  This can be also be set with `options("betydb_url")`. Note: only
  <https://www.betydb.org/> is officially supported.

- fmt:

  (character) Format to return data in, one of json, xml, csv. Only json
  currently supported.

- key:

  (character) An API key. Use this or user/pwd combo. Save in your
  `.Rprofile` file as `options(betydb_key = "your40digitkey")`. Optional

- user, pwd:

  (character) A user name and password. Use a user/pwd combo or an API
  key. Save in your `.Rprofile` file as
  `options(betydb_user = "yournamehere")` and
  `options(betydb_pwd = "yourpasswordhere")`. Optional

- progress:

  show progress bar? default: `TRUE`

- ...:

  Curl options passed on to
  [`GET`](https://httr.r-lib.org/reference/GET.html). Optional

- genus:

  (character) A genus name. Optional

- species:

  (character) A specific epithet. Optional

## Value

For betydb_trait, betydb_specie, betydb_citation, betydb_site, and
betydb_experiment, a named list of information about the requested
object. For functions that query multiple records, a data.frame
containing the query results.

## Details

BETYdb is focused on bioenergy crops and related ecological data. This
package officially supports the main public instance at
<https://www.betydb.org/>.

This package queries plant traits, phenotypes, biomass yields, and
ecosystem functions. It does not currently interface with the workflow
and provenance data that support PEcAn Project (pecanproject.org) and
TERRA REF (terraref.org) software.

API documentation:
<https://pecan.gitbooks.io/betydb-data-access/content/API.html> API
endpoints are here: <https://www.betydb.org/api/docs> This package
currently uses the original 'v0' API by default. To use a newer version,
set `api_version`. Newer versions of the API will support database
inserts.

## Authentication

Defers to use API key first since it's simpler, but if you don't have an
API key, you can supply a username and password.

## Functions

Singular functions like `betydb_trait` accept an id and additional
parameters, and return a list of variable outputs depending on the
inputs.

However, plural functions like `betydb_traits` accept query parameters,
but not ids, and always return a single data.frame.

`betydb_search("Search terms", ...)` is a convenience wrapper that
passes all further arguments to
[`betydb_query`](https://docs.ropensci.org/traits/reference/betydb_query.md)`(table = "search", search = "Search terms", ...)`.
See there for details on possible arguments.

## References

API documentation
<https://pecan.gitbooks.io/betydb-data-access/content/API.html> and
https://www.betydb.org/api/docs

## See also

[`betydb_query`](https://docs.ropensci.org/traits/reference/betydb_query.md)

## Examples

``` r
# \donttest{
if (interactive()) {
  # General Search
  out <- betydb_search(query = "Switchgrass Yield")
  if (NROW(out)) {
    mean_result <- tapply(as.numeric(out$mean), out$id, function(z) mean(z, na.rm = TRUE))
    sort(mean_result, decreasing = TRUE)
  }
  # Get by ID
  ## Traits
  betydb_trait(id = 10)
  ## Species
  betydb_specie(id = 1)
  ## Citations
  betydb_citation(id = 1)
  ## Site information
  betydb_site(id = 795)
}
# }
```
