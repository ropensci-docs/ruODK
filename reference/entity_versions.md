# List versions of one Entity.

**\[maturing\]**

## Usage

``` r
entity_versions(
  pid = get_default_pid(),
  did = "",
  eid = "",
  conflict = FALSE,
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

- eid:

  (chr) The UUID of an Entity, which can be retrieved by
  [`entity_list()`](https://docs.ropensci.org/ruODK/reference/entity_list.md).
  The function will error if this parameter is not given. Default: "".

- conflict:

  (lgl) Whether to return all versions (`FALSE`) or whether to returns
  the subset of past versions of an Entity that are relevant to the
  Entity's current conflict (`TRUE`). This includes the latest version,
  the base version, the previous server version, and any other versions
  since the last time the Entity was in a conflict-free state. If the
  Entity is not in conflict, zero versions are returned. Default:
  `FALSE` (return all versions)

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

A tibble with one row per version. List columns contain unstructured
data. See
<https://docs.getodk.org/central-api-entity-management/#listing-versions>
for the full schema. Top level list elements are renamed from ODK's
`camelCase` to `snake_case`. Nested list elements have the original
`camelCase`.

## Details

This returns the Entity metadata and data for every version of this
Entity in ascending creation order.

The ODK Central endpoint supports retrieving extended metadata which
this function always returns.

There is an optional query flag `relevantToConflict` that returns the
subset of past versions of an Entity that are relevant to the Entity's
current conflict. This includes the latest version, the base version,
the previous server version, and any other versions since the last time
the Entity was in a conflict-free state. If the Entity is not in
conflict, zero versions are returned.

## See also

<https://docs.getodk.org/central-api-entity-management/#listing-versions>

Other entity-management:
[`entity_audits()`](https://docs.ropensci.org/ruODK/reference/entity_audits.md),
[`entity_changes()`](https://docs.ropensci.org/ruODK/reference/entity_changes.md),
[`entity_create()`](https://docs.ropensci.org/ruODK/reference/entity_create.md),
[`entity_delete()`](https://docs.ropensci.org/ruODK/reference/entity_delete.md),
[`entity_detail()`](https://docs.ropensci.org/ruODK/reference/entity_detail.md),
[`entity_list()`](https://docs.ropensci.org/ruODK/reference/entity_list.md),
[`entity_update()`](https://docs.ropensci.org/ruODK/reference/entity_update.md),
[`entitylist_detail()`](https://docs.ropensci.org/ruODK/reference/entitylist_detail.md),
[`entitylist_download()`](https://docs.ropensci.org/ruODK/reference/entitylist_download.md),
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

el <- entitylist_list()

# Entity List name (dataset ID, did)
did <- el$name[1]

# All Entities of Entity List
en <- entity_list(did = did)

ed <- entity_detail(did = did, eid = en$uuid[1])

# The current version of the first Entity
ev <- en$current_version_version[1]
} # }
```
