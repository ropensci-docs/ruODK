# Set Actor Property values on a Public Access Link.

**\[experimental\]**

## Usage

``` r
public_link_update(
  pid = get_default_pid(),
  fid = get_default_fid(),
  link_id,
  properties = list(),
  url = get_default_url(),
  un = get_default_un(),
  pw = get_default_pw(),
  retries = get_retries()
)
```

## Arguments

- pid:

  The numeric ID of the project, e.g.: 2.

  Default:
  [`get_default_pid`](https://docs.ropensci.org/ruODK/reference/ru_settings.md).

  Set default `pid` through `ru_setup(pid="...")`.

  See `vignette("Setup", package = "ruODK")`.

- fid:

  The alphanumeric form ID, e.g. "build_Spotlighting-0-8_1559885147".

  Default:
  [`get_default_fid`](https://docs.ropensci.org/ruODK/reference/ru_settings.md).

  Set default `fid` through `ru_setup(fid="...")`.

  See `vignette("Setup", package = "ruODK")`.

- link_id:

  The numeric ID of the Link.

- properties:

  (list) A named list mapping Actor Property names to string values.

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

## Value

A list with the updated Link's metadata as per the ODK Central API docs,
including a `properties` object with all currently set property values.

## Details

Sets pre-registered Actor Property values on a Public Access Link. The
body holds a `properties` object mapping property names to string
values. Unsetting a property needs a JSON null, which this function
cannot send. Only set properties with this function. This endpoint
requires the `public_link.update` permission.

## See also

<https://docs.getodk.org/central-api-form-management/#setting-actor-property-values-on-a-link>

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
[`form_list()`](https://docs.ropensci.org/ruODK/reference/form_list.md),
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
[`public_link_list()`](https://docs.ropensci.org/ruODK/reference/public_link_list.md)

## Examples

``` r
if (FALSE) { # \dontrun{
# See vignette("setup") for setup and authentication options
# ruODK::ru_setup(svc = "....svc", un = "me@email.com", pw = "...")

fl <- form_list()
fid <- fl$fid[[1]]

pl <- public_link_list(fid = fid)

public_link_update(
  fid = fid,
  link_id = pl$id[[1]],
  properties = list("region" = "North")
)
} # }
```
