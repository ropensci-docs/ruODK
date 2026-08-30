# Recursively unnest_wide all list columns in a tibble.

**\[stable\]**

## Usage

``` r
unnest_all(
  nested_tbl,
  names_repair = "universal",
  names_sep = "_",
  form_schema = NULL,
  verbose = get_ru_verbose()
)
```

## Arguments

- nested_tbl:

  A nested tibble

- names_repair:

  The argument `names_repair` for
  [`tidyr::unnest_wider`](https://tidyr.tidyverse.org/reference/unnest_wider.html),
  default: "universal".

- names_sep:

  The argument `names_sep` for
  [`tidyr::unnest_wider`](https://tidyr.tidyverse.org/reference/unnest_wider.html),
  default: "\_". Un-nested variables inside a list column will be
  prefixed by the list column name, separated by `names_sep`. This
  avoids unsightly repaired names such as `latitude...1`. Set to `NULL`
  to disable prefixing.

- form_schema:

  An optional form_schema, like the output of
  [`form_schema`](https://docs.ropensci.org/ruODK/reference/form_schema.md).
  If a form schema is supplied, location fields will not be unnested.
  While WKT location fields contain plain text and will never be
  unnested, GeoJSON location fields would cause errors during unnesting.

- verbose:

  Whether to display debug messages or not.

  Read
  [`vignette("setup", package = "ruODK")`](https://docs.ropensci.org/ruODK/articles/setup.md)
  to learn how `ruODK`'s verbosity can be set globally or per function.

## Value

The un-nested tibble in wide format

## Details

[`odata_submission_rectangle`](https://docs.ropensci.org/ruODK/reference/odata_submission_rectangle.md)
uses this function internally. Interested users can use this function to
break down `ruODK`'s automated steps into smaller components.

The quite verbose output of
[`tidyr::unnest_wider`](https://tidyr.tidyverse.org/reference/unnest_wider.html)
is captured and hidden from the user.

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
[`prepend_uuid()`](https://docs.ropensci.org/ruODK/reference/prepend_uuid.md),
[`split_geopoint()`](https://docs.ropensci.org/ruODK/reference/split_geopoint.md),
[`split_geoshape()`](https://docs.ropensci.org/ruODK/reference/split_geoshape.md),
[`split_geotrace()`](https://docs.ropensci.org/ruODK/reference/split_geotrace.md),
[`strip_uuid()`](https://docs.ropensci.org/ruODK/reference/strip_uuid.md),
[`tidyeval`](https://docs.ropensci.org/ruODK/reference/tidyeval.md)
