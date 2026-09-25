# Perform one HTTP request against ODK Central.

**\[experimental\]**

## Usage

``` r
ru_http_request(
  verb,
  url,
  path = NULL,
  query = NULL,
  accept = "application/json",
  headers = NULL,
  un = NULL,
  pw = NULL,
  body = NULL,
  encode = NULL,
  dest = NULL,
  overwrite = TRUE,
  terminate_on = NULL,
  retries = get_retries()
)
```

## Arguments

- verb:

  (character) The HTTP verb, e.g. `"GET"`, `"POST"`.

- url:

  (character) The base URL of the ODK Central server, or the complete
  request URL if `path` is `NULL`.

- path:

  (character) The request path, e.g. `"v1/projects"`. If `NULL`, `url`
  is used as the complete request URL. Default: `NULL`.

- query:

  (list) Optional query string parameters. Default: `NULL` (no query
  string).

- accept:

  (character) The `Accept` header value. Default: `"application/json"`.
  Set to `NULL` to send no `Accept` header.

- headers:

  (character) Optional extra headers as a named character vector, e.g.
  `c("X-Extended-Metadata" = "true")`. Default: `NULL` (no extra
  headers).

- un:

  (character) The ODK Central username for basic authentication.
  Default: `NULL` (no authentication).

- pw:

  (character) The ODK Central password for basic authentication.
  Default: `NULL` (no authentication).

- body:

  The request body. Default: `NULL` (no body).

- encode:

  (character) The body encoding: `"json"` sends JSON, anything else
  sends raw bytes. Default: `NULL` (no body).

- dest:

  (character) A local file path to stream a download to. Default: `NULL`
  (no streaming, the response is kept in memory).

- overwrite:

  (lgl) Whether to overwrite `dest` if it exists. Only used with `dest`.
  Default: `TRUE`.

- terminate_on:

  (numeric) HTTP status codes that stop retries immediately. Default:
  `NULL` (only non-transient statuses stop retries).

- retries:

  The number of attempts to retrieve a web resource.

  This parameter is given to
  [`RETRY`](https://httr.r-lib.org/reference/RETRY.html)`(times = retries)`.

  Default: 3.

## Value

The `httr` response object, unmodified.

## Details

This is the centralised request helper for ruODK. It builds an `httr2`
request from plain data (verb, path, query, headers, credentials, body)
and returns the `httr2` response unchanged, so
[`yell_if_error()`](https://docs.ropensci.org/ruODK/reference/yell_if_error.md)
and the `httr2::resp_body_*()` parsers keep working downstream. The full
URL keeps the legacy query semantics on purpose: query values that
callers pre-encode (for example
[`entitylist_download()`](https://docs.ropensci.org/ruODK/reference/entitylist_download.md)'s
`$filter`) must not be encoded twice.

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
[`tidyeval`](https://docs.ropensci.org/ruODK/reference/tidyeval.md),
[`unnest_all()`](https://docs.ropensci.org/ruODK/reference/unnest_all.md)

## Examples

``` r
if (FALSE) { # \dontrun{
# See vignette("setup") for setup and authentication options
# ruODK::ru_setup(svc = "....svc", un = "me@email.com", pw = "...")

resp <- ruODK:::ru_http_request(
  "GET",
  url = get_test_url(),
  path = "v1/projects",
  un = get_test_un(),
  pw = get_test_pw()
)

httr2::resp_status(resp)
} # }
```
