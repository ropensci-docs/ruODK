# Update one Entity.

**\[experimental\]**

## Usage

``` r
entity_update(
  pid = get_default_pid(),
  did = "",
  eid = "",
  label = "",
  data = list(),
  base_version = NULL,
  force = is.null(base_version),
  resolve = FALSE,
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

- label:

  (character) The Entity label which must be a non-empty string.
  Default: `""`.

- data:

  (list) A named list of Entity properties to update. See details.
  Default: [`list()`](https://rdrr.io/r/base/list.html).

- base_version:

  If given, must be the current version of the Entity on the server.
  Optional.

- force:

  (lgl) Whether to force an update. Defaults to be `FALSE` if a
  `base_version` is specified, else defaults to `TRUE`. Using
  `force=TRUE` and specifying a `base_version` will emit a warning.

- resolve:

  (lgl)

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

A nested list identical to the return value of `entity_detail`. See
<https://docs.getodk.org/central-api-entity-management/#updating-an-entity>
for the full schema. Top level list elements are renamed from ODK's
`camelCase` to `snake_case`. Nested list elements have the original
`camelCase`.

## Details

This endpoint is used to update the label or the properties (passed as
JSON in the request body) of an Entity. You only need to include the
properties you wish to update. To unset the value of any property, you
can set it to empty string (""). The label must be a non-empty string.
Setting a property to null will throw an error. Attempting to update a
property that doesn't exist in the Dataset will throw an error.

### Specifying a base version

You must either provide a `base_version` or use `force=TRUE` query
parameter. You cannot cause a new Entity conflict via the API, which is
why when specifying `base_version`, it must match the current version of
the Entity on the server. This acts as a check to ensure you are not
trying to update based on stale data. If you wish to update the Entity
regardless of the current state, then you can use the force flag.

### Resolving a conflict

You can also use this endpoint to resolve an Entity conflict by passing
`resolve=true`, in which case providing `data` is optional. When not
providing new data, only the conflict status from the Entity will be
cleared and no new version will be created. When providing data, the
conflict will be cleared and an updated version of the Entity will be
added.

## See also

<https://docs.getodk.org/central-api-entity-management/#updating-an-entity>

Other entity-management:
[`entity_audits()`](https://docs.ropensci.org/ruODK/reference/entity_audits.md),
[`entity_changes()`](https://docs.ropensci.org/ruODK/reference/entity_changes.md),
[`entity_create()`](https://docs.ropensci.org/ruODK/reference/entity_create.md),
[`entity_delete()`](https://docs.ropensci.org/ruODK/reference/entity_delete.md),
[`entity_detail()`](https://docs.ropensci.org/ruODK/reference/entity_detail.md),
[`entity_list()`](https://docs.ropensci.org/ruODK/reference/entity_list.md),
[`entity_versions()`](https://docs.ropensci.org/ruODK/reference/entity_versions.md),
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

e_label <- ed$current_version$label

# This example updates one field which exists in the example form.
# Your own Entity will have different fields to update.
e_data <- list(
  details = paste0(
    ed$current_version$data$details, ". Updated on ", Sys.time()
  )
)

# Update the Entity (implicitly forced update)
eu <- entity_update(
  did = did,
  eid = en$uuid[1],
  label = e_label,
  data = e_data
)
eu
} # }
```
