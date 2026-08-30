# Prepend a leading "uuid:" to any string, e.g. an md5 hash.

**\[stable\]**

## Usage

``` r
prepend_uuid(md5hash)
```

## Arguments

- md5hash:

  A string, e.g. an md5 hash.

## Value

The string with a prepended "uuid:"

## Details

This is the inverse of the helper function
[`strip_uuid`](https://docs.ropensci.org/ruODK/reference/strip_uuid.md).

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
[`handle_ru_geopoints()`](https://docs.ropensci.org/ruODK/reference/handle_ru_geopoints.md),
[`handle_ru_geoshapes()`](https://docs.ropensci.org/ruODK/reference/handle_ru_geoshapes.md),
[`handle_ru_geotraces()`](https://docs.ropensci.org/ruODK/reference/handle_ru_geotraces.md),
[`isodt_to_local()`](https://docs.ropensci.org/ruODK/reference/isodt_to_local.md),
[`odata_submission_rectangle()`](https://docs.ropensci.org/ruODK/reference/odata_submission_rectangle.md),
[`predict_ruodk_name()`](https://docs.ropensci.org/ruODK/reference/predict_ruodk_name.md),
[`split_geopoint()`](https://docs.ropensci.org/ruODK/reference/split_geopoint.md),
[`split_geoshape()`](https://docs.ropensci.org/ruODK/reference/split_geoshape.md),
[`split_geotrace()`](https://docs.ropensci.org/ruODK/reference/split_geotrace.md),
[`strip_uuid()`](https://docs.ropensci.org/ruODK/reference/strip_uuid.md),
[`tidyeval`](https://docs.ropensci.org/ruODK/reference/tidyeval.md),
[`unnest_all()`](https://docs.ropensci.org/ruODK/reference/unnest_all.md)

## Examples

``` r
if (FALSE) { # \dontrun{
prepend_uuid("1234")
prepend_uuid("d3bcefea-32a8-4dbc-80ca-4ecb0678e2b0")
} # }
```
