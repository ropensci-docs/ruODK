# List all forms.

**\[stable\]**

## Usage

``` r
form_list(
  pid = get_default_pid(),
  deleted = FALSE,
  url = get_default_url(),
  un = get_default_un(),
  pw = get_default_pw(),
  retries = get_retries(),
  orders = get_default_orders(),
  tz = get_default_tz()
)
```

## Arguments

- pid:

  The numeric ID of the project, e.g.: 2.

  Default:
  [`get_default_pid`](https://docs.ropensci.org/ruODK/reference/ru_settings.md).

  Set default `pid` through `ru_setup(pid="...")`.

  See `vignette("Setup", package = "ruODK")`.

- deleted:

  (lgl) If `TRUE`, list only deleted Forms with their numeric form IDs,
  which can be used to restore a deleted Form with
  [`form_restore()`](https://docs.ropensci.org/ruODK/reference/form_restore.md).
  Default: `FALSE`.

- url:

  The ODK Central base URL without trailing slash.

  Default:
  [`get_default_url`](https://docs.ropensci.org/ruODK/reference/ru_settings.md).

  Set default `url` through `ru_setup(url="...")`.

  See `vignette("Setup", package = "ruODK")`.

- un:

  The ODK Central username (an email address). Default:
  [`get_default_un`](https://docs.ropensci.org/ruODK/reference/ru_settings.md).
  Set default `un` through `ru_setup(un="...")`. See
  `vignette("Setup", package = "ruODK")`.

- pw:

  The ODK Central password. Default:
  [`get_default_pw`](https://docs.ropensci.org/ruODK/reference/ru_settings.md).
  Set default `pw` through `ru_setup(pw="...")`. See
  `vignette("Setup", package = "ruODK")`.

- retries:

  The number of attempts to retrieve a web resource.

  This parameter is given to
  [`RETRY`](https://httr.r-lib.org/reference/RETRY.html)`(times = retries)`.

  Default: 3.

- orders:

  (vector of character) Orders of datetime elements for lubridate.

  Default:
  `c("YmdHMS", "YmdHMSz", "Ymd HMS", "Ymd HMSz", "Ymd", "ymd")`.

- tz:

  A timezone to convert dates and times to.

  Read
  [`vignette("setup", package = "ruODK")`](https://docs.ropensci.org/ruODK/articles/setup.md)
  to learn how `ruODK`'s timezone can be set globally or per function.

## Value

A tibble with one row per form and all given form metadata as cols.
Column names are sanitized into `snake_case`. Nested columns (review
start and created by) are flattened and prefixed. The column
`xml_form_id` is replicated as `fid` according to `ruODK` naming
standards. With `deleted = TRUE`, the tibble holds one row per deleted
Form with its numeric form ID.

## See also

<https://docs.getodk.org/central-api-form-management/#list-all-forms>

Other form-management:
[`form_assignment_actors()`](https://docs.ropensci.org/ruODK/reference/form_assignment_actors.md),
[`form_assignment_grant()`](https://docs.ropensci.org/ruODK/reference/form_assignment_grant.md),
[`form_assignment_revoke()`](https://docs.ropensci.org/ruODK/reference/form_assignment_revoke.md),
[`form_attachment_download()`](https://docs.ropensci.org/ruODK/reference/form_attachment_download.md),
[`form_attachment_list()`](https://docs.ropensci.org/ruODK/reference/form_attachment_list.md),
[`form_create()`](https://docs.ropensci.org/ruODK/reference/form_create.md),
[`form_dataset_diff()`](https://docs.ropensci.org/ruODK/reference/form_dataset_diff.md),
[`form_delete()`](https://docs.ropensci.org/ruODK/reference/form_delete.md),
[`form_detail()`](https://docs.ropensci.org/ruODK/reference/form_detail.md),
[`form_draft_attachment_delete()`](https://docs.ropensci.org/ruODK/reference/form_draft_attachment_delete.md),
[`form_draft_attachment_download()`](https://docs.ropensci.org/ruODK/reference/form_draft_attachment_download.md),
[`form_draft_attachment_link()`](https://docs.ropensci.org/ruODK/reference/form_draft_attachment_link.md),
[`form_draft_attachment_list()`](https://docs.ropensci.org/ruODK/reference/form_draft_attachment_list.md),
[`form_draft_attachment_upload()`](https://docs.ropensci.org/ruODK/reference/form_draft_attachment_upload.md),
[`form_draft_create()`](https://docs.ropensci.org/ruODK/reference/form_draft_create.md),
[`form_draft_dataset_diff()`](https://docs.ropensci.org/ruODK/reference/form_draft_dataset_diff.md),
[`form_draft_delete()`](https://docs.ropensci.org/ruODK/reference/form_draft_delete.md),
[`form_draft_detail()`](https://docs.ropensci.org/ruODK/reference/form_draft_detail.md),
[`form_draft_publish()`](https://docs.ropensci.org/ruODK/reference/form_draft_publish.md),
[`form_draft_xlsx()`](https://docs.ropensci.org/ruODK/reference/form_draft_xlsx.md),
[`form_draft_xml()`](https://docs.ropensci.org/ruODK/reference/form_draft_xml.md),
[`form_link()`](https://docs.ropensci.org/ruODK/reference/form_link.md),
[`form_restore()`](https://docs.ropensci.org/ruODK/reference/form_restore.md),
[`form_schema()`](https://docs.ropensci.org/ruODK/reference/form_schema.md),
[`form_schema_ext()`](https://docs.ropensci.org/ruODK/reference/form_schema_ext.md),
[`form_update()`](https://docs.ropensci.org/ruODK/reference/form_update.md),
[`form_version_attachment_download()`](https://docs.ropensci.org/ruODK/reference/form_version_attachment_download.md),
[`form_version_attachment_list()`](https://docs.ropensci.org/ruODK/reference/form_version_attachment_list.md),
[`form_version_detail()`](https://docs.ropensci.org/ruODK/reference/form_version_detail.md),
[`form_version_list()`](https://docs.ropensci.org/ruODK/reference/form_version_list.md),
[`form_version_xlsx()`](https://docs.ropensci.org/ruODK/reference/form_version_xlsx.md),
[`form_version_xml()`](https://docs.ropensci.org/ruODK/reference/form_version_xml.md),
[`form_xlsx()`](https://docs.ropensci.org/ruODK/reference/form_xlsx.md),
[`form_xml()`](https://docs.ropensci.org/ruODK/reference/form_xml.md),
[`public_link_create()`](https://docs.ropensci.org/ruODK/reference/public_link_create.md),
[`public_link_delete()`](https://docs.ropensci.org/ruODK/reference/public_link_delete.md),
[`public_link_detail()`](https://docs.ropensci.org/ruODK/reference/public_link_detail.md),
[`public_link_list()`](https://docs.ropensci.org/ruODK/reference/public_link_list.md),
[`public_link_update()`](https://docs.ropensci.org/ruODK/reference/public_link_update.md)

## Examples

``` r
if (FALSE) { # \dontrun{
# See vignette("setup") for setup and authentication options
# ruODK::ru_setup(svc = "....svc", un = "me@email.com", pw = "...")

# With default pid
fl <- form_list()

# With explicit pid
fl <- form_list(pid = 1)

class(fl)
# > c("tbl_df", "tbl", "data.frame")

# Filter out draft forms (published_at=NA)
only_published_forms <- fl %>% dplyr::filter(is.na(published_at))

# Note: older ODK Central versions < 1.1 have published_at = NA for both
# published and draft forms. Drafts have NA for version and hash.
only_published_forms <- fl %>% dplyr::filter(is.na(version) & is.na(hash))
} # }
```
