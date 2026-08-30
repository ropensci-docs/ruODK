# Get the Data Document from the OData Dataset Service.

**\[experimental\]**

## Usage

``` r
odata_entitylist_data_get(
  pid = get_default_pid(),
  did = "",
  query = NULL,
  url = get_default_url(),
  un = get_default_un(),
  pw = get_default_pw(),
  retries = get_retries(),
  odkc_version = get_default_odkc_version(),
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

- did:

  (chr) The name of the Entity List, internally called Dataset. The
  function will error if this parameter is not given. Default: "".

- query:

  An optional named list of query parameters, e.g.

      list(
        "$filter" = "__system/createdAt le 2024-11-05",
        "$orderby" = "__system/creatorId ASC, __system/conflict DESC",
        "$top" = "100",
        "$skip" = "3",
        "$count" = "true"
      )

  No validation is conducted by `ruODK` on the query list prior to
  passing it to ODK Central. If omitted, no filter query is sent. Note
  that the behaviour of this parameter differs from the implementation
  of
  [`odata_submission_get()`](https://docs.ropensci.org/ruODK/reference/odata_submission_get.md)
  in that `query` here accepts a list of all possible OData query
  parameters and
  [`odata_submission_get()`](https://docs.ropensci.org/ruODK/reference/odata_submission_get.md)
  offers individual function parameters matching supported OData query
  parameters. Default: `NULL`

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

## Value

An S3 class `odata_entitylist_data_get` with two list items:

- `context` The URL for the OData metadata document

- `value` A tibble of EntitySets available in this EntityList, with
  names cleaned by
  [`janitor::clean_names()`](https://sfirke.github.io/janitor/reference/clean_names.html)
  and unnested list columns (`__system`).

## Details

All the Entities in a Dataset.

The `$top` and `$skip` querystring parameters, specified by OData, apply
limit and offset operations to the data, respectively.

The `$count` parameter, also an OData standard, will annotate the
response data with the total row count, regardless of the scoping
requested by `$top` and `$skip`. If `$top` parameter is provided in the
request then the response will include `@odata.nextLink` that you can
use as is to fetch the next set of data. As of ODK Central v2023.4,
`@odata.nextLink` contains a `$skiptoken` (an opaque cursor) to better
paginate around deleted Entities.

The `$filter` querystring parameter can be used to filter certain data
fields in the system-level schema, but not the Dataset properties. The
operators `lt`, `le`, `eq`, `ne`, `ge`, `gt`, `not`, `and`, and `or` and
the built-in functions `now`, `year`, `month`, `day`, `hour`, `minute`,
`second` are supported.

The fields you can query against are as follows:

Entity Metadata: `OData Field Name` Entity Creator Actor ID:
`__system/creatorId` Entity Timestamp: `__system/createdAt` Entity
Update Timestamp: `__system/updatedAt` Entity Conflict:
`__system/conflict`

Note that `createdAt` and `updatedAt` are time components. This means
that any comparisons you make need to account for the full time of the
entity. It might seem like `$filter=__system/createdAt le 2020-01-31`
would return all results on or before 31 Jan 2020, but in fact only
entities made before midnight of that day would be accepted. To include
all of the month of January, you need to filter by either
`$filter=__system/createdAt le 2020-01-31T23:59:59.999Z` or
`$filter=__system/createdAt lt 2020-02-01`. Remember also that you can
query by a specific timezone.

Please see the OData documentation on `$filter`
[operations](http://docs.oasis-open.org/odata/odata/v4.01/cs01/part1-protocol/odata-v4.01-cs01-part1-protocol.html#sec_BuiltinFilterOperations)
and
[functions](http://docs.oasis-open.org/odata/odata/v4.01/cs01/part1-protocol/odata-v4.01-cs01-part1-protocol.html#sec_BuiltinQueryFunctions)
for more information.

The `$select` query parameter will return just the fields you specify
and is supported on `__id`, `__system`, `__system/creatorId`,
`__system/createdAt` and `__system/updatedAt`, as well as on user
defined properties.

The `$orderby` query parameter will return Entities sorted by different
fields, which come from the same list used by `$filter`, as noted above.
The order can be specified as ASC (ascending) or DESC (descending),
which are case-insensitive. Multiple sort expressions can be used
together, separated by commas, e.g.
`$orderby=__system/creatorId ASC, __system/conflict DESC`.

As the vast majority of clients only support the JSON OData format, that
is the only format ODK Central offers.

## See also

<https://docs.getodk.org/central-api-odata-endpoints/#id3>

<http://docs.oasis-open.org/odata/odata/v4.01/odata-v4.01-part1-protocol.html#_Toc31358948>

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
[`entitylist_download()`](https://docs.ropensci.org/ruODK/reference/entitylist_download.md),
[`entitylist_list()`](https://docs.ropensci.org/ruODK/reference/entitylist_list.md),
[`entitylist_update()`](https://docs.ropensci.org/ruODK/reference/entitylist_update.md),
[`odata_entitylist_metadata_get()`](https://docs.ropensci.org/ruODK/reference/odata_entitylist_metadata_get.md),
[`odata_entitylist_service_get()`](https://docs.ropensci.org/ruODK/reference/odata_entitylist_service_get.md)

## Examples

``` r
if (FALSE) { # \dontrun{
# See vignette("setup") for setup and authentication options
# ruODK::ru_setup(svc = "....svc", un = "me@email.com", pw = "...")

ds <- entitylist_list(pid = get_default_pid())

ds1 <- odata_entitylist_data_get(pid = get_default_pid(), did = ds$name[1])

ds1
ds1$context
ds1$value

qry <- list(
  "$filter" = "__system/createdAt le 2024-11-05",
  "$orderby" = "__system/creatorId ASC, __system/conflict DESC",
  "$top" = "100",
  "$skip" = "3",
  "$count" = "true"
)
ds2 <- odata_entitylist_data_get(
  pid = get_default_pid(),
  did = ds$name[1],
  query = qry
)

ds2
} # }
```
