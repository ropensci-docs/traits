# Get bird habitat information from BirdLife/IUCN

Get bird habitat information from BirdLife/IUCN

## Usage

``` r
birdlife_habitat(id)
```

## Arguments

- id:

  A single IUCN species ID

## Value

a `data.frame` with level 1 and level 2 habitat classes, as well as
importance ratings and occurrence type (e.g. breeding or non-breeding).
The habitat classification scheme is described at
https://www.iucnredlist.org/resources/classification-schemes

## See also

Other birdlife:
[`birdlife_threats()`](https://docs.ropensci.org/traits/reference/birdlife_threats.md)

## Author

David J. Harris <harry491@gmail.com>

## Examples

``` r
# \donttest{
if (interactive()) {
  # Setophaga chrysoparia
  birdlife_habitat(22721692)
  # Passer domesticus
  birdlife_habitat(103818789)
}
# }
```
