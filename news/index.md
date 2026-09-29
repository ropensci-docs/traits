# Changelog

## traits 0.6.0 (unreleased)

CRAN release: 2026-04-10

#### REMOVED FUNCTIONS

- Fully removed previously defunct functions:
  - `tr_usda()` (defunct since v0.5.0,
    [\#122](https://github.com/ropensci/traits/issues/122))
  - `coral_*` functions (defunct since v0.5.0,
    [\#124](https://github.com/ropensci/traits/issues/124))
  - `is_native()`, `g_invasive()`, `eol_invasive()`, `fe_native()`
    (defunct since v0.3.0,
    [\#72](https://github.com/ropensci/traits/issues/72))

#### MINOR IMPROVEMENTS

- Updated package documentation and examples to reflect current APIs
- Changed from to in examples that require internet access.
- Documented return values.

## traits 0.5.2 (2025-04-10)

#### Minor Improvements

- Set up automatic archiving of releases on Zenodo.
- Added `CITATION.cff` file
  ([\#133](https://github.com/ropensci/traits/issues/133)).
- Added DOI to `README` and `CITATION.cff`
  ([\#134](https://github.com/ropensci/traits/issues/134)).
- Added `inst/CITATION`.

#### Bug Fixes

- Fixed syntax error in `test-ncbi.R` causing test failures.
- Added missing `batch_size` argument to `ncbi_byname` documentation
  ([\#132](https://github.com/ropensci/traits/issues/132)).
- Changed ‘country’ to ‘geo_loc_name’ in
  [`ncbi_byid()`](https://docs.ropensci.org/traits/reference/ncbi_byid.md)
  ([\#136](https://github.com/ropensci/traits/issues/136)).

## traits 0.5.1

CRAN release: 2024-05-17

#### NEW FEATURES

- David LeBauer ([@dlebauer](https://github.com/dlebauer)) is now the
  maintainer of the traits package. Many thanks to previous maintainer
  Scott Chamberlain!

## traits 0.5.0

CRAN release: 2020-08-27

#### DEFUNCT

- `tr_usda()` is defunct. The API is down for good
  ([\#122](https://github.com/ropensci/traits/issues/122))
- all `coral_*` functions are defunct
  ([\#124](https://github.com/ropensci/traits/issues/124))

#### MINOR IMPROVEMENTS

- replace httr with crul
  ([\#89](https://github.com/ropensci/traits/issues/89))
- fix BETYdb tess
  ([\#123](https://github.com/ropensci/traits/issues/123))

#### BUG FIXES

- [`ncbi_searcher()`](https://docs.ropensci.org/traits/reference/ncbi_searcher.md)
  fix: we weren’t including the NCBI Entrez API key even when it was
  found ([\#120](https://github.com/ropensci/traits/issues/120))

## traits 0.4.2

CRAN release: 2019-06-29

#### MINOR IMPROVEMENTS

- betydb gains alias for API versions
  ([\#114](https://github.com/ropensci/traits/issues/114))

#### BUG FIXES

- `taxa_search`: removed `traitbank` option because
  [`traits::traitbank()`](https://docs.ropensci.org/traits/reference/traitbank.md)
  used internally has completely changed and it’s no longer feasible to
  do a straight-forward taxon search for all traits in EOL’s Traitbank
  ([\#115](https://github.com/ropensci/traits/issues/115))

## traits 0.4.0

CRAN release: 2019-06-07

#### NEW FEATURES

- New package author: Chris Black
  ([@infotroph](https://github.com/infotroph))
  ([\#106](https://github.com/ropensci/traits/issues/106))
- betydb functions now can do pagination
  ([\#94](https://github.com/ropensci/traits/issues/94))
- betydb functions gain progress parameter to optionally suppress the
  progress bar ([\#113](https://github.com/ropensci/traits/issues/113))
- EOL Traitbank completely changed their query interface - function no
  longer works as it did before. for now, you have to specify your own
  query that’s rather complex, see docs for help. Later on we can try to
  simplify queries for users
  ([\#112](https://github.com/ropensci/traits/issues/112))

#### MINOR IMPROVEMENTS

- table in README for different sources and clarify what traits are
  ([\#110](https://github.com/ropensci/traits/issues/110))
  ([\#111](https://github.com/ropensci/traits/issues/111))
- fixed link to Birdlife
  ([\#108](https://github.com/ropensci/traits/issues/108))

#### BUG FIXES

- fix to
  [`ncbi_searcher()`](https://docs.ropensci.org/traits/reference/ncbi_searcher.md)
  to prevent failures in some cases
  ([\#107](https://github.com/ropensci/traits/issues/107)) thanks
  [@zachary-foster](https://github.com/zachary-foster)
- fix to
  [`ncbi_byid()`](https://docs.ropensci.org/traits/reference/ncbi_byid.md):
  ten new fields added to the output
  ([\#101](https://github.com/ropensci/traits/issues/101))
  ([\#102](https://github.com/ropensci/traits/issues/102)) thanks
  [@boopsboops](https://github.com/boopsboops)

## traits 0.3.0

CRAN release: 2017-09-22

#### DEFUNCT

- Four functions are now defunct - those involving getting data on
  whether a species if native/invasive in a particular region. See
  `?traits-defunct` for more information. Deprecated functions:
  `eol_invasive_()`, `fe_native()`, `g_invasive()`, `is_native()`
  ([\#72](https://github.com/ropensci/traits/issues/72))

#### NEW FEATURES

- Gains new function `tr_ernest` for a dataset of Amniote life history
  data ([\#60](https://github.com/ropensci/traits/issues/60))
- Gains new function `tr_usda` for the USDA plants database
  ([\#61](https://github.com/ropensci/traits/issues/61))
- Gains new function `tr_zanne` for a dataset of plant growth data
  ([\#73](https://github.com/ropensci/traits/issues/73))
- BetyDB functions gain automatic paging of large requests where API
  supports it, i.e. not in v0
  ([\#94](https://github.com/ropensci/traits/issues/94))

#### MINOR IMPROVEMENTS

- Change Coral database base URL to https
  ([\#99](https://github.com/ropensci/traits/issues/99))
- Now requiring `readr > 1.0`
  ([\#76](https://github.com/ropensci/traits/issues/76))
- Changed `ncbi_*()` functions to give back `NA` types that match
  data.frame column classes to make combining easier
  ([\#96](https://github.com/ropensci/traits/issues/96))
- replace
  [`xml2::xml_find_one`](http://xml2.r-lib.org/reference/xml_find_all.md)
  with
  [`xml2::xml_find_first`](http://xml2.r-lib.org/reference/xml_find_all.md)
  throughout ([\#97](https://github.com/ropensci/traits/issues/97))
- namespace all fxn calls for base pkgs, remove from Imports
  ([\#98](https://github.com/ropensci/traits/issues/98))
- BetyDB cleanup ([\#25](https://github.com/ropensci/traits/issues/25))
  ([\#77](https://github.com/ropensci/traits/issues/77))
  ([\#82](https://github.com/ropensci/traits/issues/82))
  ([\#88](https://github.com/ropensci/traits/issues/88))

#### BUG FIXES

- Fixed `birdlife*` functions that needed to change URL structure due to
  changes in the Birdlife website
  ([\#100](https://github.com/ropensci/traits/issues/100))
- Fixes to
  [`traitbank()`](https://docs.ropensci.org/traits/reference/traitbank.md)
  ([\#79](https://github.com/ropensci/traits/issues/79))
  ([\#80](https://github.com/ropensci/traits/issues/80)) thanks
  [@dschlaep](https://github.com/dschlaep) !
- `ncbi_*()` fxns now use https
  ([\#95](https://github.com/ropensci/traits/issues/95))

## traits 0.2.0

CRAN release: 2016-03-18

#### DEPRECATED

- Marked four functions as deprecated - those involving getting data on
  whether a species if native/invasive in a particular region. See
  `?traits-deprecated` for more information. Deprecated functions:
  `eol_invasive_()`, `fe_native()`, `g_invasive()`, `is_native()`
  ([\#63](https://github.com/ropensci/traits/issues/63))

#### MINOR IMPROVEMENTS

- Standardized outputs of all data - all data.frame column names should
  be lowercase now
  ([\#47](https://github.com/ropensci/traits/issues/47))
- With all
  [`httr::content()`](https://httr.r-lib.org/reference/content.html)
  calls now explicitly setting encoding to `UTF-8`, and parsing to
  `text`, then manually parsing either JSON or XML later
  ([\#65](https://github.com/ropensci/traits/issues/65))
- Replaced `XML` with `xml2` for XML parsing
  ([\#67](https://github.com/ropensci/traits/issues/67))

## traits 0.1.2

CRAN release: 2015-09-12

#### NEW FEATURES

- [`ncbi_searcher()`](https://docs.ropensci.org/traits/reference/ncbi_searcher.md)
  gains new parameter `fuzzy` to toggle fuzzy taxonomic ID search or
  exact search. ([\#34](https://github.com/ropensci/traits/issues/34))
  (thx [@mpnelsen](https://github.com/mpnelsen))

#### MINOR IMPROVEMENTS

- Importing only functions (via `importFrom`) used across all imports
  now. In addition, `importFrom` for all non-base R pkgs, including
  `methods`, `stats` and `utils` packages
  ([\#36](https://github.com/ropensci/traits/issues/36))
- Changed the `trait` parameter in
  [`traitbank()`](https://docs.ropensci.org/traits/reference/traitbank.md)
  function to `pageid`, because EOL expects a page identifier, which is
  associated with a taxon, not a trait. The previous parameter name was
  very misleading.

## traits 0.1.0

CRAN release: 2015-06-12

#### NEW FEATURES

- released to CRAN
