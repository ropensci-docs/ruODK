# Add a property to an Entity List.

**\[experimental\]**

## Usage

``` r
entitylist_property_create(
  pid = get_default_pid(),
  did = "",
  property = "",
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

- property:

  (character) The desired name of the Property.

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

A list with a single element `success` (`TRUE`) as per the ODK Central
API docs.

## Details

Creates a new Property with a specified name in the Dataset. The name of
a Property is case-sensitive in that it will keep the capitalization
provided (e.g. "Firstname"). But Central will not allow another Property
with the same name but different capitalization to be created (e.g.
"FIRSTNAME" when "Firstname" already exists). Property names follow the
same rules as form field names (valid XML identifiers) and cannot use
the reserved names of name or label, or begin with the reserved prefix
`__`.

## See also

<https://docs.getodk.org/central-api-dataset-management/#adding-properties>

Other entity-management:
[`entity_audits()`](https://docs.ropensci.org/ruODK/reference/entity_audits.md),
[`entity_bulk_delete()`](https://docs.ropensci.org/ruODK/reference/entity_bulk_delete.md),
[`entity_bulk_restore()`](https://docs.ropensci.org/ruODK/reference/entity_bulk_restore.md),
[`entity_changes()`](https://docs.ropensci.org/ruODK/reference/entity_changes.md),
[`entity_create()`](https://docs.ropensci.org/ruODK/reference/entity_create.md),
[`entity_creators()`](https://docs.ropensci.org/ruODK/reference/entity_creators.md),
[`entity_delete()`](https://docs.ropensci.org/ruODK/reference/entity_delete.md),
[`entity_detail()`](https://docs.ropensci.org/ruODK/reference/entity_detail.md),
[`entity_geodata()`](https://docs.ropensci.org/ruODK/reference/entity_geodata.md),
[`entity_geojson()`](https://docs.ropensci.org/ruODK/reference/entity_geojson.md),
[`entity_list()`](https://docs.ropensci.org/ruODK/reference/entity_list.md),
[`entity_restore()`](https://docs.ropensci.org/ruODK/reference/entity_restore.md),
[`entity_update()`](https://docs.ropensci.org/ruODK/reference/entity_update.md),
[`entity_versions()`](https://docs.ropensci.org/ruODK/reference/entity_versions.md),
[`entitylist_create()`](https://docs.ropensci.org/ruODK/reference/entitylist_create.md),
[`entitylist_delete()`](https://docs.ropensci.org/ruODK/reference/entitylist_delete.md),
[`entitylist_detail()`](https://docs.ropensci.org/ruODK/reference/entitylist_detail.md),
[`entitylist_download()`](https://docs.ropensci.org/ruODK/reference/entitylist_download.md),
[`entitylist_list()`](https://docs.ropensci.org/ruODK/reference/entitylist_list.md),
[`entitylist_property_delete()`](https://docs.ropensci.org/ruODK/reference/entitylist_property_delete.md),
[`entitylist_trash_download()`](https://docs.ropensci.org/ruODK/reference/entitylist_trash_download.md),
[`entitylist_update()`](https://docs.ropensci.org/ruODK/reference/entitylist_update.md),
[`odata_entitylist_data_get()`](https://docs.ropensci.org/ruODK/reference/odata_entitylist_data_get.md),
[`odata_entitylist_metadata_get()`](https://docs.ropensci.org/ruODK/reference/odata_entitylist_metadata_get.md),
[`odata_entitylist_service_get()`](https://docs.ropensci.org/ruODK/reference/odata_entitylist_service_get.md)

## Examples

``` r
if (FALSE) { # \dontrun{
# See vignette("setup") for setup and authentication options
# ruODK::ru_setup(svc = "....svc", un = "me@email.com", pw = "...")

entitylist_property_create(did = "trees", property = "circumference")
# > $success
# > [1] TRUE
} # }
```
