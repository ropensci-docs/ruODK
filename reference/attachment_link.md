# Prefix attachment columns from CSV export with a local attachment file path.

**\[stable\]**

## Usage

``` r
attachment_link(data_tbl, form_schema, att_path = "media")
```

## Arguments

- data_tbl:

  The downloaded submissions from
  [`submission_export`](https://docs.ropensci.org/ruODK/reference/submission_export.md)
  read into a `tibble` by
  [`readr::read_csv`](https://readr.tidyverse.org/reference/read_delim.html).

- form_schema:

  The `form_schema` for the submissions. E.g. the output of
  [`ruODK::form_schema()`](https://docs.ropensci.org/ruODK/reference/form_schema.md).

- att_path:

  A local path, default: "media" (as per .csv.zip export). Selected
  columns of the dataframe (containing attchment filenames) are prefixed
  with `att_path`, thus turning them into relative paths.

## Value

The dataframe with attachment columns modified to contain relative paths
to the downloaded attachment files.

## See also

Other utilities:
[`attachment_get()`](https://docs.ropensci.org/ruODK/reference/attachment_get.md),
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
[`tidyeval`](https://docs.ropensci.org/ruODK/reference/tidyeval.md),
[`unnest_all()`](https://docs.ropensci.org/ruODK/reference/unnest_all.md)

## Examples

``` r
if (FALSE) { # \dontrun{
t <- tempdir()
# See vignette("setup") for setup and authentication options
# ruODK::ru_setup(svc = "....svc", un = "me@email.com", pw = "...")

# Predict filenames (with knowledge of form)
fid <- get_default_fid()
fid_csv <- fs::path(t, glue::glue("{fid}.csv"))
fid_csv_tae <- fs::path(t, glue::glue("{fid}-taxon_encounter.csv"))
fs <- form_schema()

# Download the zip file
se <- ruODK::submission_export(
  local_dir = t,
  overwrite = FALSE,
  verbose = TRUE
)

# Unpack the zip file
f <- unzip(se, exdir = t)
fs::dir_ls(t)

# Prepend attachments with media/ to turn into relative file paths
data_quadrat <- fid_csv %>%
  readr::read_csv(na = c("", "NA", "na")) %>%
  janitor::clean_names() %>%
  handle_ru_datetimes(fs) %>%
  attachment_link(fs)
} # }
```
