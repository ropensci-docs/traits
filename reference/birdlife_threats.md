# Get bird threat information from BirdLife/IUCN

Get bird threat information from BirdLife/IUCN

## Usage

``` r
birdlife_threats(id)
```

## Arguments

- id:

  A single IUCN species ID

## Value

a `data.frame` with the species ID and two levels of threat
descriptions, plus stresses, timing, scope, severity, and impact
associated with each stressor.

## See also

Other birdlife:
[`birdlife_habitat()`](https://docs.ropensci.org/traits/reference/birdlife_habitat.md)

## Author

David J. Harris <harry491@gmail.com>

## Examples

``` r
# \donttest{
if (interactive()) {
  # Setophaga chrysoparia
  birdlife_threats(22721692)
  # Aburria aburri
  birdlife_threats(22678440)
}
# }
```
