# Print an OData EntityList metadata object.

Prints a short summary (complex type, Entity type and container names)
of an object as returned by
[`odata_entitylist_metadata_get`](https://docs.ropensci.org/ruODK/reference/odata_entitylist_metadata_get.md).

## Usage

``` r
# S3 method for class 'odata_entitylist_metadata_get'
print(x, ...)
```

## Arguments

- x:

  An `odata_entitylist_metadata_get` object.

- ...:

  Ignored.

## Value

`NULL`, invisibly. Called for its side effect.

## See also

Other entity-management:
[`entity_audits()`](https://docs.ropensci.org/ruODK/reference/entity_audits.md),
[`entity_bulk_delete()`](https://docs.ropensci.org/ruODK/reference/entity_bulk_delete.md),
[`entity_bulk_restore()`](https://docs.ropensci.org/ruODK/reference/entity_bulk_restore.md),
[`entity_changes()`](https://docs.ropensci.org/ruODK/reference/entity_changes.md),
[`entity_create()`](https://docs.ropensci.org/ruODK/reference/entity_create.md),
[`entity_creators()`](https://docs.ropensci.org/ruODK/reference/entity_creators.md),
[`entity_delete()`](https://docs.ropensci.org/ruODK/reference/entity_delete.md),
[`entity_detail()`](https://docs.ropensci.org/ruODK/reference/entity_detail.md),
[`entity_geodata()`](https://docs.ropensci.org/ruODK/reference/entity_geodata.md),
[`entity_geojson()`](https://docs.ropensci.org/ruODK/reference/entity_geojson.md),
[`entity_list()`](https://docs.ropensci.org/ruODK/reference/entity_list.md),
[`entity_restore()`](https://docs.ropensci.org/ruODK/reference/entity_restore.md),
[`entity_update()`](https://docs.ropensci.org/ruODK/reference/entity_update.md),
[`entity_versions()`](https://docs.ropensci.org/ruODK/reference/entity_versions.md),
[`entitylist_create()`](https://docs.ropensci.org/ruODK/reference/entitylist_create.md),
[`entitylist_delete()`](https://docs.ropensci.org/ruODK/reference/entitylist_delete.md),
[`entitylist_detail()`](https://docs.ropensci.org/ruODK/reference/entitylist_detail.md),
[`entitylist_download()`](https://docs.ropensci.org/ruODK/reference/entitylist_download.md),
[`entitylist_list()`](https://docs.ropensci.org/ruODK/reference/entitylist_list.md),
[`entitylist_property_create()`](https://docs.ropensci.org/ruODK/reference/entitylist_property_create.md),
[`entitylist_property_delete()`](https://docs.ropensci.org/ruODK/reference/entitylist_property_delete.md),
[`entitylist_trash_download()`](https://docs.ropensci.org/ruODK/reference/entitylist_trash_download.md),
[`entitylist_update()`](https://docs.ropensci.org/ruODK/reference/entitylist_update.md),
[`odata_entitylist_data_get()`](https://docs.ropensci.org/ruODK/reference/odata_entitylist_data_get.md),
[`odata_entitylist_metadata_get()`](https://docs.ropensci.org/ruODK/reference/odata_entitylist_metadata_get.md),
[`odata_entitylist_service_get()`](https://docs.ropensci.org/ruODK/reference/odata_entitylist_service_get.md),
[`print.odata_entitylist_data_get()`](https://docs.ropensci.org/ruODK/reference/print.odata_entitylist_data_get.md),
[`print.odata_entitylist_service_get()`](https://docs.ropensci.org/ruODK/reference/print.odata_entitylist_service_get.md)

## Examples

``` r
x <- structure(
  list(
    complex_types = list(trees = TRUE),
    entity_types = list(Entities = TRUE),
    containers = list(trees = TRUE)
  ),
  class = c("odata_entitylist_metadata_get", "list")
)
print(x)
#> <ruODK OData EntityList Metadata>
#>   Complex Types:  [1] "trees"
#>   Entity Types:  [1] "Entities"
#>   Containers:  [1] "trees"
```
