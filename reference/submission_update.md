# Update Submission data.

**\[experimental\]**

## Usage

``` r
submission_update(
  iid,
  pid = get_default_pid(),
  fid = get_default_fid(),
  xml = NULL,
  url = get_default_url(),
  un = get_default_un(),
  pw = get_default_pw(),
  retries = get_retries()
)
```

## Arguments

- iid:

  The `instance_id`, a UUID, as returned by
  [`submission_list`](https://docs.ropensci.org/ruODK/reference/submission_list.md).

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

- xml:

  (character) The complete new Submission XML as a single string,
  including the `deprecatedID` metadata node.

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

A list with the updated Submission's metadata as per the ODK Central API
docs. Top level list elements are renamed from ODK's `camelCase` to
`snake_case`.

## Details

You can use this endpoint to submit updates to an existing Submission.
The `instanceID` submitted with the initial version of the Submission is
used permanently to reference that Submission logically, which is to say
the initial Submission and all its subsequent versions. Each subsequent
version also provides its own `instanceID`.

To perform an update, provide in the Submission XML an additional
`deprecatedID` metadata node with the `instanceID` of the particular and
current Submission version you are replacing. If the `deprecatedID` you
give is anything other than the identifier of the current version of the
Submission at the time the server receives it, Central answers 409.
`deprecatedID` must contain the current `instanceID`.
[`submission_get()`](https://docs.ropensci.org/ruODK/reference/submission_get.md)
returns the current `instanceID`. The new version must have a new
`instanceID`.

The XML data you send replaces the existing data entirely. All of the
data must be present in the updated XML.

When you create a new Submission version, any uploaded media files
attached to the current version that match expected attachment names in
the new version are automatically copied over to the new version.

This endpoint requires ODK Central v1.2 or later.

## See also

<https://docs.getodk.org/central-api-submission-management/#updating-submission-data>

Other submission-management:
[`attachment_delete()`](https://docs.ropensci.org/ruODK/reference/attachment_delete.md),
[`attachment_list()`](https://docs.ropensci.org/ruODK/reference/attachment_list.md),
[`attachment_upload()`](https://docs.ropensci.org/ruODK/reference/attachment_upload.md),
[`encryption_key_list()`](https://docs.ropensci.org/ruODK/reference/encryption_key_list.md),
[`submission_audit_get()`](https://docs.ropensci.org/ruODK/reference/submission_audit_get.md),
[`submission_changes()`](https://docs.ropensci.org/ruODK/reference/submission_changes.md),
[`submission_comment_create()`](https://docs.ropensci.org/ruODK/reference/submission_comment_create.md),
[`submission_comment_list()`](https://docs.ropensci.org/ruODK/reference/submission_comment_list.md),
[`submission_create()`](https://docs.ropensci.org/ruODK/reference/submission_create.md),
[`submission_csv()`](https://docs.ropensci.org/ruODK/reference/submission_csv.md),
[`submission_delete()`](https://docs.ropensci.org/ruODK/reference/submission_delete.md),
[`submission_detail()`](https://docs.ropensci.org/ruODK/reference/submission_detail.md),
[`submission_draft_attachment_delete()`](https://docs.ropensci.org/ruODK/reference/submission_draft_attachment_delete.md),
[`submission_draft_attachment_download()`](https://docs.ropensci.org/ruODK/reference/submission_draft_attachment_download.md),
[`submission_draft_attachment_list()`](https://docs.ropensci.org/ruODK/reference/submission_draft_attachment_list.md),
[`submission_draft_attachment_upload()`](https://docs.ropensci.org/ruODK/reference/submission_draft_attachment_upload.md),
[`submission_draft_create()`](https://docs.ropensci.org/ruODK/reference/submission_draft_create.md),
[`submission_draft_export()`](https://docs.ropensci.org/ruODK/reference/submission_draft_export.md),
[`submission_draft_get()`](https://docs.ropensci.org/ruODK/reference/submission_draft_get.md),
[`submission_draft_keys()`](https://docs.ropensci.org/ruODK/reference/submission_draft_keys.md),
[`submission_draft_list()`](https://docs.ropensci.org/ruODK/reference/submission_draft_list.md),
[`submission_edit()`](https://docs.ropensci.org/ruODK/reference/submission_edit.md),
[`submission_export()`](https://docs.ropensci.org/ruODK/reference/submission_export.md),
[`submission_geodata()`](https://docs.ropensci.org/ruODK/reference/submission_geodata.md),
[`submission_geojson()`](https://docs.ropensci.org/ruODK/reference/submission_geojson.md),
[`submission_get()`](https://docs.ropensci.org/ruODK/reference/submission_get.md),
[`submission_list()`](https://docs.ropensci.org/ruODK/reference/submission_list.md),
[`submission_restore()`](https://docs.ropensci.org/ruODK/reference/submission_restore.md),
[`submission_review()`](https://docs.ropensci.org/ruODK/reference/submission_review.md),
[`submission_submitters()`](https://docs.ropensci.org/ruODK/reference/submission_submitters.md),
[`submission_version_attachment_delete()`](https://docs.ropensci.org/ruODK/reference/submission_version_attachment_delete.md),
[`submission_version_attachment_download()`](https://docs.ropensci.org/ruODK/reference/submission_version_attachment_download.md),
[`submission_version_attachment_list()`](https://docs.ropensci.org/ruODK/reference/submission_version_attachment_list.md),
[`submission_version_detail()`](https://docs.ropensci.org/ruODK/reference/submission_version_detail.md),
[`submission_version_geojson()`](https://docs.ropensci.org/ruODK/reference/submission_version_geojson.md),
[`submission_version_xml()`](https://docs.ropensci.org/ruODK/reference/submission_version_xml.md),
[`submission_versions()`](https://docs.ropensci.org/ruODK/reference/submission_versions.md)

## Examples

``` r
if (FALSE) { # \dontrun{
# See vignette("setup") for setup and authentication options
# ruODK::ru_setup(svc = "....svc", un = "me@email.com", pw = "...")

sl <- submission_list()
iid <- sl$instance_id[[1]]

xml <- paste0(
  '<data id="simple" version="1">',
  "<meta>",
  "<instanceID>uuid:85cb9aff-005e-4edd-9739-dc9c1a829c45</instanceID>",
  "<deprecatedID>", iid, "</deprecatedID>",
  "</meta>",
  "<name>Jo updated</name>",
  "</data>"
)

s <- submission_update(iid = iid, xml = xml)

s$current_version$instanceId
# > "uuid:85cb9aff-005e-4edd-9739-dc9c1a829c45"
} # }
```
