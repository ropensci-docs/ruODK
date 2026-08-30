# Split all geopoints of a submission tibble into their components.

**\[stable\]**

## Usage

``` r
handle_ru_geopoints(data, form_schema, wkt = FALSE, verbose = get_ru_verbose())
```

## Arguments

- data:

  Submissions rectangled into a tibble. E.g. the output of

      ruODK::odata_submission_get(parse = FALSE) %>%
      ruODK::odata_submission_rectangle()

- form_schema:

  The `form_schema` for the submissions. E.g. the output of
  [`ruODK::form_schema()`](https://docs.ropensci.org/ruODK/reference/form_schema.md).

- wkt:

  Whether geofields are GeoJSON (if FALSE) or WKT strings (if TRUE),
  default: FALSE.

- verbose:

  Whether to display debug messages or not.

  Read
  [`vignette("setup", package = "ruODK")`](https://docs.ropensci.org/ruODK/articles/setup.md)
  to learn how `ruODK`'s verbosity can be set globally or per function.

## Value

The submissions tibble with all geopoints retained in their original
format, plus columns of their coordinate components as provided by
[`split_geopoint`](https://docs.ropensci.org/ruODK/reference/split_geopoint.md).

## Details

For a given tibble of submissions, find all columns which are listed in
the form schema as type `geopoint`, and extract their components.
Extracted components are longitude (X), latitude (Y), altitude (Z, where
given), and accuracy (M, where given).

The original column is retained to allow parsing into other spatially
enabled formats.

## See also

Other utilities:
[`attachment_get()`](https://docs.ropensci.org/ruODK/reference/attachment_get.md),
[`attachment_link()`](https://docs.ropensci.org/ruODK/reference/attachment_link.md),
[`attachment_url()`](https://docs.ropensci.org/ruODK/reference/attachment_url.md),
[`drop_null_coords()`](https://docs.ropensci.org/ruODK/reference/drop_null_coords.md),
[`form_schema_parse()`](https://docs.ropensci.org/ruODK/reference/form_schema_parse.md),
[`get_one_attachment()`](https://docs.ropensci.org/ruODK/reference/get_one_attachment.md),
[`get_one_submission()`](https://docs.ropensci.org/ruODK/reference/get_one_submission.md),
[`get_one_submission_att_list()`](https://docs.ropensci.org/ruODK/reference/get_one_submission_att_list.md),
[`get_one_submission_audit()`](https://docs.ropensci.org/ruODK/reference/get_one_submission_audit.md),
[`handle_ru_attachments()`](https://docs.ropensci.org/ruODK/reference/handle_ru_attachments.md),
[`handle_ru_datetimes()`](https://docs.ropensci.org/ruODK/reference/handle_ru_datetimes.md),
[`handle_ru_geoshapes()`](https://docs.ropensci.org/ruODK/reference/handle_ru_geoshapes.md),
[`handle_ru_geotraces()`](https://docs.ropensci.org/ruODK/reference/handle_ru_geotraces.md),
[`isodt_to_local()`](https://docs.ropensci.org/ruODK/reference/isodt_to_local.md),
[`odata_submission_rectangle()`](https://docs.ropensci.org/ruODK/reference/odata_submission_rectangle.md),
[`predict_ruodk_name()`](https://docs.ropensci.org/ruODK/reference/predict_ruodk_name.md),
[`prepend_uuid()`](https://docs.ropensci.org/ruODK/reference/prepend_uuid.md),
[`split_geopoint()`](https://docs.ropensci.org/ruODK/reference/split_geopoint.md),
[`split_geoshape()`](https://docs.ropensci.org/ruODK/reference/split_geoshape.md),
[`split_geotrace()`](https://docs.ropensci.org/ruODK/reference/split_geotrace.md),
[`strip_uuid()`](https://docs.ropensci.org/ruODK/reference/strip_uuid.md),
[`tidyeval`](https://docs.ropensci.org/ruODK/reference/tidyeval.md),
[`unnest_all()`](https://docs.ropensci.org/ruODK/reference/unnest_all.md)

## Examples

``` r
library(magrittr)
data("geo_fs")
data("geo_gj_raw")
data("geo_wkt_raw")

# GeoJSON
geo_gj_parsed <- geo_gj_raw %>%
  ruODK::odata_submission_rectangle(form_schema = geo_fs) %>%
  ruODK::handle_ru_geopoints(form_schema = geo_fs, wkt = FALSE)

dplyr::glimpse(geo_gj_parsed)
#> Rows: 1
#> Columns: 41
#> $ meta_instance_id                      <chr> "uuid:2d3dbc0c-70f5-4c99-a812-a8…
#> $ device_id                             <chr> "collect:OHnydk6INUIfDHNl"
#> $ start_time                            <chr> "2023-12-04T16:35:36.206+08:00"
#> $ username                              <lgl> NA
#> $ subscriber_id                         <lgl> NA
#> $ point_location_point_gps_longitude    <dbl> 115.7745
#> $ point_location_point_gps_latitude     <dbl> -31.89503
#> $ point_location_point_gps_altitude     <dbl> 6.6
#> $ point_location_point_gps_accuracy     <dbl> 16.555
#> $ point_location_point_gps              <list> ["Point", [115.7745, -31.89503, …
#> $ point_location_point_map_longitude    <dbl> 115.7745
#> $ point_location_point_map_latitude     <dbl> -31.89503
#> $ point_location_point_map_altitude     <dbl> 6.6
#> $ point_location_point_map_accuracy     <dbl> 15.996
#> $ point_location_point_map              <list> ["Point", [115.7745, -31.89503, …
#> $ point_location_point_manual_longitude <dbl> 115.7745
#> $ point_location_point_manual_latitude  <dbl> -31.8967
#> $ point_location_point_manual_altitude  <int> 0
#> $ point_location_point_manual_accuracy  <int> 0
#> $ point_location_point_manual           <list> ["Point", [115.7745, -31.8967, 0…
#> $ path_location_path_gps                <list> ["LineString", [[115.7756, -31.8…
#> $ path_location_path_map                <list> ["LineString", [[115.7733, -31.8…
#> $ path_location_path_manual             <list> ["LineString", [[115.7726, -31.8…
#> $ shape_location_shape_gps              <list> ["Polygon", [[[115.7658, -31.871…
#> $ shape_location_shape_map              <list> ["Polygon", [[[115.7745, -31.895…
#> $ shape_location_shape_manual           <list> ["Polygon", [[[115.797, -31.920…
#> $ end_time                              <chr> "2023-12-04T16:38:49.702+08:00"
#> $ id                                    <chr> "uuid:2d3dbc0c-70f5-4c99-a812-a8…
#> $ system_submission_date                <chr> "2023-12-04T08:38:52.712Z"
#> $ system_updated_at                     <chr> "2024-03-05T05:28:51.126Z"
#> $ system_submitter_id                   <chr> "12"
#> $ system_submitter_name                 <chr> "ruodk"
#> $ system_attachments_present            <int> 0
#> $ system_attachments_expected           <int> 0
#> $ system_status                         <lgl> NA
#> $ system_review_state                   <chr> "approved"
#> $ system_device_id                      <chr> "collect:OHnydk6INUIfDHNl"
#> $ system_edits                          <int> 0
#> $ system_form_version                   <chr> ""
#> $ system_deleted_at                     <lgl> NA
#> $ odata_context                         <chr> "https://ruodk.getodk.cloud/v1/p…

# WKT
geo_wkt_parsed <- geo_wkt_raw %>%
  ruODK::odata_submission_rectangle(form_schema = geo_fs) %>%
  ruODK::handle_ru_geopoints(form_schema = geo_fs, wkt = TRUE)

dplyr::glimpse(geo_wkt_parsed)
#> Rows: 1
#> Columns: 38
#> $ meta_instance_id                      <chr> "uuid:2d3dbc0c-70f5-4c99-a812-a8…
#> $ device_id                             <chr> "collect:OHnydk6INUIfDHNl"
#> $ start_time                            <chr> "2023-12-04T16:35:36.206+08:00"
#> $ username                              <lgl> NA
#> $ subscriber_id                         <lgl> NA
#> $ point_location_point_gps              <chr> "POINT (115.7745212 -31.8950326 …
#> $ point_location_point_gps_longitude    <dbl> 115.7745
#> $ point_location_point_gps_latitude     <dbl> -31.89503
#> $ point_location_point_gps_altitude     <dbl> 6.6
#> $ point_location_point_map              <chr> "POINT (115.7745049 -31.89503 6.…
#> $ point_location_point_map_longitude    <dbl> 115.7745
#> $ point_location_point_map_latitude     <dbl> -31.89503
#> $ point_location_point_map_altitude     <dbl> 6.6
#> $ point_location_point_manual           <chr> "POINT (115.77449776232241 -31.8…
#> $ point_location_point_manual_longitude <dbl> 115.7745
#> $ point_location_point_manual_latitude  <dbl> -31.8967
#> $ point_location_point_manual_altitude  <int> 0
#> $ path_location_path_gps                <chr> "LINESTRING (115.77564273029566 …
#> $ path_location_path_map                <chr> "LINESTRING (115.77329177409409 …
#> $ path_location_path_manual             <chr> "LINESTRING (115.77255014330147 …
#> $ shape_location_shape_gps              <chr> "POLYGON ((115.76582819223404 -3…
#> $ shape_location_shape_map              <chr> "POLYGON ((115.7744988 -31.89504…
#> $ shape_location_shape_manual           <chr> "POLYGON ((115.79702932387592 -3…
#> $ end_time                              <chr> "2023-12-04T16:38:49.702+08:00"
#> $ id                                    <chr> "uuid:2d3dbc0c-70f5-4c99-a812-a8…
#> $ system_submission_date                <chr> "2023-12-04T08:38:52.712Z"
#> $ system_updated_at                     <chr> "2024-03-05T05:28:51.126Z"
#> $ system_submitter_id                   <chr> "12"
#> $ system_submitter_name                 <chr> "ruodk"
#> $ system_attachments_present            <int> 0
#> $ system_attachments_expected           <int> 0
#> $ system_status                         <lgl> NA
#> $ system_review_state                   <chr> "approved"
#> $ system_device_id                      <chr> "collect:OHnydk6INUIfDHNl"
#> $ system_edits                          <int> 0
#> $ system_form_version                   <chr> ""
#> $ system_deleted_at                     <lgl> NA
#> $ odata_context                         <chr> "https://ruodk.getodk.cloud/v1/p…
```
