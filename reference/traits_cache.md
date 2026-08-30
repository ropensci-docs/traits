# Caching

Manage cached `traits` package files with hoardr

## Value

A `hoardr` object with methods for managing cached files

## Details

The dafault cache directory is
`paste0(rappdirs::user_cache_dir(), "/R/traits")`, but you can set your
own path using `cache_path_set()`

`cache_delete` only accepts 1 file name, while `cache_delete_all`
doesn't accept any names, but deletes all files. For deleting many
specific files, use `cache_delete` in a
[`lapply()`](https://rdrr.io/r/base/lapply.html) type call

## Useful user functions

- `traits_cache$cache_path_get()` get cache path

- `traits_cache$cache_path_set()` set cache path

- `traits_cache$list()` returns a character vector of full path file
  names

- `traits_cache$files()` returns file objects with metadata

- `traits_cache$details()` returns files with details

- `traits_cache$delete()` delete specific files

- `traits_cache$delete_all()` delete all files, returns nothing

## Examples

``` r
# \donttest{
traits_cache
#> <hoard> 
#>   path: traits
#>   cache path: ~/.cache/R/traits

# list files in cache
traits_cache$list()
#> character(0)

# delete certain database files
# traits_cache$delete("file path")
# traits_cache$list()

# delete all files in cache
# traits_cache$delete_all()
# traits_cache$list()

# set a different cache path from the default
# }
```
