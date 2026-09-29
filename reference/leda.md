# Access LEDA trait data

Access LEDA trait data

## Usage

``` r
leda(trait = "age_first_flowering", ...)
```

## Arguments

- trait:

  (character) Trait to get. See Details.

- ...:

  Curl options passed on to
  [crul::verb-GET](https://docs.ropensci.org/crul/reference/verb-GET.html)

## Value

A data frame with trait data.

## Details

For parameter `trait`, one of age_first_flowering, branching,
buds_seasonality, buds_vertical_dist, canopy_height, dispersal_type,
leaf_distribution, ldmc_geo, leaf_mass, leaf_size, morphology_disperal,
growth_form, life_span, releasing_height, seed_longevity, seed_mass,
seed_number, seed_shape, shoot_growth_form, snp, ssd, tv, or
clonal_growth_organs

The following are not supported as they are too much of a pain to parse:
buoyancy, seed_bank, sla_geo

## Examples

``` r
# \donttest{
if (interactive()) {
  # Age of first flowering
  leda(trait = "age_first_flowering")

  # Seed number
  leda("seed_number")

  # Releasing height
  leda(trait = "releasing_height")

  # Clonal growth organs
  leda(trait = "clonal_growth_organs")

  all <- c("age_first_flowering", "branching", "buds_seasonality",
    "buds_vertical_dist", "canopy_height",
    "dispersal_type", "leaf_distribution", "ldmc_geo", "leaf_mass",
    "leaf_size", "morphology_disperal", "growth_form", "life_span",
    "releasing_height", "seed_longevity", "seed_mass",
    "seed_number", "seed_shape", "shoot_growth_form",
    "snp", "ssd", "tv", "clonal_growth_organs")
  out <- list()
  for (i in seq_along(all)) {
    cat(all[i], sep = "\n")
    out[[i]] <- leda(all[i])
  }
  sapply(out, NROW)
}
# }
```
