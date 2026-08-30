# Download an Entity List as CSV.

**\[maturing\]**

## Usage

``` r
entitylist_download(
  pid = get_default_pid(),
  did = "",
  url = get_default_url(),
  un = get_default_un(),
  pw = get_default_pw(),
  local_dir = here::here(),
  filter = NULL,
  etag = NULL,
  overwrite = TRUE,
  retries = get_retries(),
  odkc_version = get_default_odkc_version(),
  orders = get_default_orders(),
  tz = get_default_tz(),
  verbose = get_ru_verbose()
)
```

## Arguments

- pid:

  The numeric ID of the project, e.g.: 2.

  Default:
  [`get_default_pid`](https://docs.ropensci.org/ruODK/reference/ru_settings.md).

  Set default `pid` through `ru_setup(pid="...")`.

  See `vignette("Setup", package = "ruODK")`.

- did:

  (chr) The name of the Entity List, internally called Dataset. The
  function will error if this parameter is not given. Default: "".

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

- local_dir:

  The local folder to save the downloaded files to, default:
  [`here::here`](https://here.r-lib.org/reference/here.html). If the
  folder does not exist it will be created.

- filter:

  (str) A valid filter string. Default: NULL (no filtering, all Entities
  returned).

- etag:

  (str) The etag value from a previous call to `entitylist_download()`.
  The value must be stripped of the `W/\"` and `\"`, which is the format
  of the etag returned by `entitylist_download()`. If provided, only new
  entities will be returned. If the same `local_dir` is chosen and
  `overwrite` is set to `TRUE`, the downloaded CSV will also be
  overwritten, losing the previously downloaded Entities. Default: NULL
  (no filtering, all Entities returned).

- overwrite:

  Whether to overwrite previously downloaded file, default: FALSE

- retries:

  The number of attempts to retrieve a web resource.

  This parameter is given to
  [`RETRY`](https://httr.r-lib.org/reference/RETRY.html)`(times = retries)`.

  Default: 3.

- odkc_version:

  The ODK Central version as a semantic version string
  (year.minor.patch), e.g. "2023.5.1". The version is shown on ODK
  Central's version page `/version.txt`. Discard the "v". `ruODK` uses
  this parameter to adjust for breaking changes in ODK Central.

  Default:
  [`get_default_odkc_version`](https://docs.ropensci.org/ruODK/reference/ru_settings.md)
  or "2023.5.1" if unset.

  Set default `get_default_odkc_version` through
  `ru_setup(odkc_version="2023.5.1")`.

  See `vignette("Setup", package = "ruODK")`.

- orders:

  (vector of character) Orders of datetime elements for lubridate.

  Default:
  `c("YmdHMS", "YmdHMSz", "Ymd HMS", "Ymd HMSz", "Ymd", "ymd")`.

- tz:

  A timezone to convert dates and times to.

  Read
  [`vignette("setup", package = "ruODK")`](https://docs.ropensci.org/ruODK/articles/setup.md)
  to learn how `ruODK`'s timezone can be set globally or per function.

- verbose:

  Whether to display debug messages or not.

  Read
  [`vignette("setup", package = "ruODK")`](https://docs.ropensci.org/ruODK/articles/setup.md)
  to learn how `ruODK`'s verbosity can be set globally or per function.

## Value

A list of four items:

- entities (tbl_df) The Entity List as tibble

- http_status (int) The HTTP status code of the response. 200 if OK, 304
  if a given etag finds no new entities created.

- etag (str) The ETag to use in subsequent calls to
  `entitylist_download()`

- downloaded_to (fs_path) The path to the downloaded CSV file

- downloaded_on (POSIXct) The time of download in the local timezone

## Details

### CSV file

The downloaded CSV file is named after the entity list name. The
download location defaults to the current workdir, but can be modified
to a different folder path which will be created if it doesn't exist.

Entity Lists can be used as Attachments in other Forms, but they can
also be downloaded directly as a CSV file.

The CSV format closely matches the OData Dataset (Entity List) Service
format, with columns for system properties such as `__id` (the Entity
UUID), `__createdAt`, `__creatorName`, etc., the Entity Label, and the
Dataset (Entity List) or Entity Properties themselves. If any Property
for an given Entity is blank (e.g. it was not captured by that Form or
was left blank), that field of the CSV is blank.

### Filter

The ODK Central `$filter` query string parameter can be used to filter
on system-level properties, similar to how filtering in the OData
Dataset (Entity List) Service works. Of the [OData filter
specs](https://docs.oasis-open.org/odata/odata/v4.01/odata-v4.01-part1-protocol.html#_Toc31358948)
ODK Central implements a [growing set of
features](https://docs.getodk.org/central-api-odata-endpoints/#data-document)
. `ruODK` provides the parameter `filter` (str) which, if set, will be
passed on to the ODK Central endpoint as is.

### Resuming downloads through ETag

The ODK Central endpoint supports the [`ETag`
header](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/ETag)
, which can be used to avoid downloading the same content more than
once. When an API consumer calls this endpoint, the endpoint returns a
value in the `ETag` header. If you pass that value in the
[`If-None-Match`
header](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/If-None-Match)
of a subsequent request, then if the Entity List has not been changed
since the previous request, you will receive 304 Not Modified response;
otherwise you'll get the new data. `ruODK` provides the parameter `etag`
which can be set from the output of a previous call to
`entitylist_download()`. `ruODK` strips the `W/\"` and `\"` from the
returned etag and expects the stripped etag as parameter.

## See also

<https://docs.getodk.org/central-api-dataset-management/#datasets>

Other entity-management:
[`entity_audits()`](https://docs.ropensci.org/ruODK/reference/entity_audits.md),
[`entity_changes()`](https://docs.ropensci.org/ruODK/reference/entity_changes.md),
[`entity_create()`](https://docs.ropensci.org/ruODK/reference/entity_create.md),
[`entity_delete()`](https://docs.ropensci.org/ruODK/reference/entity_delete.md),
[`entity_detail()`](https://docs.ropensci.org/ruODK/reference/entity_detail.md),
[`entity_list()`](https://docs.ropensci.org/ruODK/reference/entity_list.md),
[`entity_update()`](https://docs.ropensci.org/ruODK/reference/entity_update.md),
[`entity_versions()`](https://docs.ropensci.org/ruODK/reference/entity_versions.md),
[`entitylist_detail()`](https://docs.ropensci.org/ruODK/reference/entitylist_detail.md),
[`entitylist_list()`](https://docs.ropensci.org/ruODK/reference/entitylist_list.md),
[`entitylist_update()`](https://docs.ropensci.org/ruODK/reference/entitylist_update.md),
[`odata_entitylist_data_get()`](https://docs.ropensci.org/ruODK/reference/odata_entitylist_data_get.md),
[`odata_entitylist_metadata_get()`](https://docs.ropensci.org/ruODK/reference/odata_entitylist_metadata_get.md),
[`odata_entitylist_service_get()`](https://docs.ropensci.org/ruODK/reference/odata_entitylist_service_get.md)

## Examples

``` r
if (FALSE) { # \dontrun{
# See vignette("setup") for setup and authentication options
# ruODK::ru_setup(svc = "....svc", un = "me@email.com", pw = "...")

ds <- entitylist_list(pid = get_default_pid())

ds1 <- entitylist_download(pid = get_default_pid(), did = ds$name[1])
# ds1$entities
# ds1$etag
# ds1$downloaded_to
# ds1$downloaded_on

ds2 <- entitylist_download(
  pid = get_default_pid(),
  did = ds$name[1],
  etag = ds1$etag
)
# ds2$http_status == 304

newest_entity_date <- as.Date(max(ds1$entities$`__createdAt`))
ds3 <- entitylist_download(
  pid = get_default_pid(),
  did = ds$name[1],
  filter = glue::glue("__createdAt le {newest_entity_date}")
)
} # }
```
