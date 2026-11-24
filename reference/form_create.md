# Create a new Form.

**\[experimental\]**

## Usage

``` r
form_create(
  pid = get_default_pid(),
  xml = NULL,
  file = NULL,
  publish = FALSE,
  ignore_warnings = FALSE,
  xls_form_id_fallback = NULL,
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

- xml:

  (character) The XForms XML definition as a single string. Exactly one
  of `xml` and `file` must be given. Default: `NULL`.

- file:

  (character) Path to a local `.xml`, `.xls` or `.xlsx` file holding the
  Form definition. Exactly one of `xml` and `file` must be given.
  Default: `NULL`.

- publish:

  (lgl) If `TRUE`, the Form skips the Draft state and is published
  immediately. Default: `FALSE`.

- ignore_warnings:

  (lgl) If `TRUE`, the Form is created even if the XLSForm conversion
  results in warnings. Conversion errors always fail the request. Only
  used for `.xls`/`.xlsx` uploads. Default: `FALSE`.

- xls_form_id_fallback:

  (character) The form ID to use if an uploaded spreadsheet does not
  specify one. Sent as the `X-XlsForm-FormId-Fallback` header. Only used
  for `.xls`/`.xlsx` uploads. Default: `NULL` (no header sent).

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

A list with the new Form's metadata as per the ODK Central API docs. Top
level list elements are renamed from ODK's `camelCase` to `snake_case`.

## Details

When creating a Form, the only required data is the actual XForms XML or
XLSForm itself.

Forms will by default be created in Draft state, accessible under
`/projects/.../forms/.../draft`. The Form itself will not have a public
XML definition, and will not appear for download onto mobile devices.
You will need to publish the Form to finalize it for data collection. To
disable this behaviour, and force the new Form to be immediately ready,
pass `publish = TRUE`.

The API will check the XML's structure in order to extract the
information it needs about it, but ODK Central does not run
comprehensive validation on the full contents of the XML. ODK Validate
finds problems in the Form before upload. Publish the Draft after the
Form passes validation.

## See also

<https://docs.getodk.org/central-api-form-management/#creating-a-new-form>

Other form-management:
[`form_assignment_actors()`](https://docs.ropensci.org/ruODK/reference/form_assignment_actors.md),
[`form_assignment_grant()`](https://docs.ropensci.org/ruODK/reference/form_assignment_grant.md),
[`form_assignment_revoke()`](https://docs.ropensci.org/ruODK/reference/form_assignment_revoke.md),
[`form_attachment_download()`](https://docs.ropensci.org/ruODK/reference/form_attachment_download.md),
[`form_attachment_list()`](https://docs.ropensci.org/ruODK/reference/form_attachment_list.md),
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
[`public_link_list()`](https://docs.ropensci.org/ruODK/reference/public_link_list.md),
[`public_link_update()`](https://docs.ropensci.org/ruODK/reference/public_link_update.md)

## Examples

``` r
if (FALSE) { # \dontrun{
# See vignette("setup") for setup and authentication options
# ruODK::ru_setup(svc = "....svc", un = "me@email.com", pw = "...")

xml <- paste0(
  '<h:html xmlns="http://www.w3.org/2002/xforms" ',
  'xmlns:h="http://www.w3.org/1999/xhtml">',
  "<h:head><h:title>Simple</h:title><model><instance>",
  '<data id="simple"><meta><instanceID/></meta><name/></data>',
  "</instance>",
  '<bind nodeset="/data/meta/instanceID" type="string" readonly="true()" ',
  'calculate="concat(\'uuid:\', uuid())"/>',
  '<bind nodeset="/data/name" type="string"/>',
  "</model></h:head>",
  '<h:body><input ref="/data/name"><label>Name</label></input></h:body>',
  "</h:html>"
)

f <- form_create(xml = xml, publish = TRUE)

f$xml_form_id
# > "simple"
} # }
```
