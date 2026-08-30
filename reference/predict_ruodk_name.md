# Predict a field name after `tidyr::unnest_wider(names_sep="_")` prefixes the form path.

Predict a field name after `tidyr::unnest_wider(names_sep="_")` prefixes
the form path.

## Usage

``` r
predict_ruodk_name(name_str, path_str)
```

## Arguments

- name_str:

  An Xforms field name string.

- path_str:

  A path string, e.g. "Submissions" or "Submissions.group_name".

## Value

The name as built by `tidyr::unnest_wider(names_sep="_")`.

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
[`prepend_uuid()`](https://docs.ropensci.org/ruODK/reference/prepend_uuid.md),
[`split_geopoint()`](https://docs.ropensci.org/ruODK/reference/split_geopoint.md),
[`split_geoshape()`](https://docs.ropensci.org/ruODK/reference/split_geoshape.md),
[`split_geotrace()`](https://docs.ropensci.org/ruODK/reference/split_geotrace.md),
[`strip_uuid()`](https://docs.ropensci.org/ruODK/reference/strip_uuid.md),
[`tidyeval`](https://docs.ropensci.org/ruODK/reference/tidyeval.md),
[`unnest_all()`](https://docs.ropensci.org/ruODK/reference/unnest_all.md)

## Examples

``` r
if (FALSE) { # \dontrun{
predict_ruodk_name("bar", "Submissions.foo")
# > "foo_bar"
predict_ruodk_name("bar", "Submissions")
# > "bar"
predict_ruodk_name("rock", "Submissions.foo_fighters")
# > "foo_fighters_rock"
} # }
```
