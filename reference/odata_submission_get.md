# Retrieve and rectangle form submissions, parse dates, geopoints, download and link attachments.

**\[stable\]**

## Usage

``` r
odata_submission_get(
  table = "Submissions",
  skip = NULL,
  top = NULL,
  count = FALSE,
  wkt = FALSE,
  expand = FALSE,
  filter = NULL,
  parse = TRUE,
  download = TRUE,
  names_sep = "_",
  clean_names = TRUE,
  orders = get_default_orders(),
  local_dir = "media",
  pid = get_default_pid(),
  fid = get_default_fid(),
  url = get_default_url(),
  un = get_default_un(),
  pw = get_default_pw(),
  odkc_version = get_default_odkc_version(),
  tz = get_default_tz(),
  retries = get_retries(),
  verbose = get_ru_verbose()
)
```

## Arguments

- table:

  The submission EntityType, or in plain words, the table name. Default:
  `Submissions` (the main table). Change to `Submissions.GROUP_NAME` for
  repeating form groups. The group name can be found through
  [`odata_service_get`](https://docs.ropensci.org/ruODK/reference/odata_service_get.md).

- skip:

  The number of rows to be omitted from the results. Example: 10,
  default: `NA` (none skipped).

- top:

  The number of rows to return. Example: 100, default: `NA` (all
  returned).

- count:

  If TRUE, an `@odata.count` property will be returned in the response
  from ODK Central. Default: `FALSE`.

- wkt:

  If TRUE, geospatial data will be returned as WKT (Well Known Text)
  strings. Default: `FALSE`, returns GeoJSON structures. Note that
  accuracy is only returned through GeoJSON.

- expand:

  If TRUE, all subtables will be expanded and included with column names
  containing the number of the repeat, the group name, and the field
  name. This parameter is supported from ODK Central v1.2 onwards and
  will be ignored on earlier versions of ODK Central. The version is
  inferred from the parameter `odkc_version`. Default: FALSE.

- filter:

  If provided, will filter responses to those matching the query. For an
  `odkc_version` below 1.1, this parameter will be discarded. As of ODK
  Central v1.5, the fields `system/submitterId`,
  `system/submissionDate`, `__system/updatedAt` and
  `__system/reviewState` are available to reference. The operators `lt`,
  `lte`, `eq`, `neq`, `gte`, `gt`, `not`, `and`, and `or` are supported,
  and the built-in functions `now`, `year`, `month`, `day`, `hour`,
  `minute`, `second.` `ruODK` does not validate the query string given
  to `filter`. It is highly recommended to refer to the ODK Central API
  documentation as well as the [OData spec on
  filters](https://docs.oasis-open.org/odata/odata/v4.01/odata-v4.01-part1-protocol.html#_Toc31358948).
  for filter options and capabilities.

- parse:

  Whether to parse submission data based on form schema. Dates and
  datetimes will be parsed into local time. Attachments will be
  downloaded, and the field updated to the local file path. Point
  locations will be split into components; GeoJSON (`wkt=FALSE`) will be
  split into latitude, longitude, altitude and accuracy (with anonymous
  field names), while WKT will be split into longitude, latitude,and
  altitude (missing accuracy) prefixed by the original field name. See
  details for the handling of geotraces and geoshapes. Default: TRUE.

- download:

  Whether to download attachments to `local_dir` or not. If in the
  future ODK Central supports hot-linking attachments, this parameter
  will replace attachment file names with their fully qualified
  attachment URL. Default: TRUE.

- names_sep:

  Used internally in `tidyr::unnest_wider(names_sep=names_sep)` when
  unnesting form groups. By default, nested form fields are prefixed
  with the group name and separated by `names_sep`. To omit the group
  name as prefix, use `names_sep=NULL`. Default: "\_"

- clean_names:

  Whether to run
  [`janitor::clean_names()`](https://sfirke.github.io/janitor/reference/clean_names.html)
  after unnesting form groups. Set `clean_names=FALSE` to preserve any
  non-standard `names_sep`. Default: TRUE.

- orders:

  (vector of character) Orders of datetime elements for lubridate.
  Default:
  `c("YmdHMS", "YmdHMSz", "Ymd HMS", "Ymd HMSz", "Ymd", "ymd")`.

- local_dir:

  The local folder to save the downloaded files to, default: `"media"`.

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

- tz:

  A timezone to convert dates and times to.

  Read
  [`vignette("setup", package = "ruODK")`](https://docs.ropensci.org/ruODK/articles/setup.md)
  to learn how `ruODK`'s timezone can be set globally or per function.

- retries:

  The number of attempts to retrieve a web resource.

  This parameter is given to
  [`RETRY`](https://httr.r-lib.org/reference/RETRY.html)`(times = retries)`.

  Default: 3.

- verbose:

  Whether to display debug messages or not.

  Read
  [`vignette("setup", package = "ruODK")`](https://docs.ropensci.org/ruODK/articles/setup.md)
  to learn how `ruODK`'s verbosity can be set globally or per function.

## Value

A list of lists.

- `value` contains the submissions as list of lists.

- `@odata.context` is the URL of the metadata.

- `@odata.count` is the total number of rows in the table.

## Details

`odata_submission_get` downloads submissions from (default) the main
form group (submission table) including any non-repeating form groups,
or from any other table as specified by parameter `table`.

With parameter `parse=TRUE` (default), submission data is parsed into a
tibble. Any fields of type `dateTime` or `date` are parsed into dates,
with an optional parameter `tz` to specify the local timezone.

A parameter `local_dir` (default: `media`) specifies a local directory
for downloaded attachment files. Already existing, previously downloaded
attachments will be retained.

With parameter `wkt=TRUE`, spatial fields will be returned as WKT,
rather than GeoJSON. In addition, fields of type `geopoint` will be
split into latitude, longitude, and altitude, prefixed with the original
field name. E.g. a field `start_location` of type `geopoint` will be
split into `start_location_latitude`, `start_location_longitude`, and
`start_location_altitude`. The field name prefix will allow multiple
fields of type `geopoint` to be split into their components without
naming conflicts.

Geotraces (lines) and gepshapes (polygons) will be retained in their
original format, plus columns of their first point's coordinate
components as provided by
[`split_geotrace`](https://docs.ropensci.org/ruODK/reference/split_geotrace.md)
and
[`split_geoshape`](https://docs.ropensci.org/ruODK/reference/split_geoshape.md),
respectively.

Entirely unpopulated form fields, as well as notes and form groups, will
be excluded from the resulting tibble. Submitting at least one complete
form instance will prevent the accidental exclusion of an otherwise
mostly empty form field.

The only remaining manual step is to optionally join any sub-tables to
the master table.

The parameter `verbose` enables diagnostic messages along the download
and parsing process.

With parameter `parse=FALSE`, submission data is presented as nested
list, which is the R equivalent of the JSON structure returned from the
API. From there,
[`odata_submission_rectangle`](https://docs.ropensci.org/ruODK/reference/odata_submission_rectangle.md)
can rectangle the data into a tibble, and subsequent lines of
[`handle_ru_datetimes`](https://docs.ropensci.org/ruODK/reference/handle_ru_datetimes.md),
[`handle_ru_attachments`](https://docs.ropensci.org/ruODK/reference/handle_ru_attachments.md),
[`handle_ru_geopoints`](https://docs.ropensci.org/ruODK/reference/handle_ru_geopoints.md),
[`handle_ru_geotraces`](https://docs.ropensci.org/ruODK/reference/handle_ru_geotraces.md),
and
[`handle_ru_geoshapes`](https://docs.ropensci.org/ruODK/reference/handle_ru_geoshapes.md)
parse dates, download and link file attachments, and extract coordinates
from geofields. `ruODK` offers this manual and explicit pathway as an
option to investigate and narrow down unexpected or unwanted behaviour.

## See also

<https://docs.getodk.org/central-api-odata-endpoints/#odata-form-service>

<https://docs.getodk.org/central-api-odata-endpoints/#data-document>

Other odata-api:
[`odata_metadata_get()`](https://docs.ropensci.org/ruODK/reference/odata_metadata_get.md),
[`odata_service_get()`](https://docs.ropensci.org/ruODK/reference/odata_service_get.md)

## Examples

``` r
if (FALSE) { # \dontrun{
# See vignette("setup") for setup and authentication options
# ruODK::ru_setup(svc = "....svc", un = "me@email.com", pw = "...")

form_tables <- ruODK::odata_service_get()
data <- odata_submission_get() # default: main data table
data <- odata_submission_get(table = form_tables$url[1]) # same, explicitly
data_sub1 <- odata_submission_get(table = form_tables$url[2]) # sub-table 1
data_sub2 <- odata_submission_get(table = form_tables$url[3]) # sub-table 2

# Skip one row, return the next 1 rows (top), include total row count
data <- odata_submission_get(
  table = form_tables$url[1],
  skip = 1,
  top = 1,
  count = TRUE
)

# Filter submissions
data <- odata_submission_get(
  table = form_tables$url[1],
  filter = "year(__system/submissionDate) lt year(now())"
)
data <- odata_submission_get(
  table = form_tables$url[1],
  filter = "year(__system/submissionDate) lt 2020"
)

# To include all of the month of January, you need to filter by either
# filter = "__system/submissionDate le 2020-01-31T23:59:59.999Z"
# or
# filter = "__system/submissionDate lt 2020-02-01".
# Instead of timezone UTC ("Z"), you can also filter by any other timezone.
} # }
```
