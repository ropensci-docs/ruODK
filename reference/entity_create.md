# Creates exactly one Entity in the Dataset.

**\[experimental\]**

## Usage

``` r
entity_create(
  pid = get_default_pid(),
  did = "",
  label = "",
  uuid = "",
  notes = "",
  data = list(),
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

- label:

  (character) The Entity label which must be a non-empty string. If the
  label is given, a single entity is created using `data`, `notes`, and
  `uuid` if given. If the label is kept at the default (or omitted),
  multiple entities are created using `data` and `notes` and ignoring
  `uuid`. Default: `""`.

- uuid:

  (character) A single UUID to assign to the entity. Default: `""`. With
  the default, Central will create and assign a UUID. This parameter is
  only used when creating a single entity (`label` non-empty) and
  ignored when creating multiple entities (`label` empty).

- notes:

  (character) Metadata about the request which can be retrieved using
  the entity audit log. Default: `""`.

- data:

  (list) A named list of Entity properties to create a single Entity, or
  a nested list with an array of Entity data to create multiple
  Entities. The nested lists representing individual entities must be
  valid as in they must contain a label, valid data for the respective
  entity properties, and can contain an optional UUID. See details and
  the ODK documentation for the exact format. Default:
  [`list()`](https://rdrr.io/r/base/list.html).

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
<https://docs.getodk.org/central-api-entity-management/#creating-entities>
for the full schema. Top level list elements are renamed from ODK's
`camelCase` to `snake_case`. Nested list elements have the original
`camelCase`.

## Details

### Creating a single Entity

For creating a single Entity, include

- An optional `uuid`. If skipped, Central will create a UUID for the
  Entity.

- The Entity `label` must be non-empty.

- A named list `data` representing the Entity's fields. The value type
  of all properties is string.

`uuid = "..."` `label = "John Doe"`
`data = list("firstName" = "John", "age" = "22")`

This translates to JSON

`{ "label": "John Doe", "data": { "firstName": "John", "age": "22" } }`

### Creating multiple Entities

For creating multiple Entities in bulk, the request body takes an array
entities containing a list of Entity objects as described above. The
bulk entity version also takes a source property with a required name
field and optional size, for example to capture the file name and size
of a bulk upload source (in MB).

    data=list(
        "entities" = c(
          list("label" = "Entity 1", "data" = list("field1" = "value1")),
          list("label" = "Entity 2", "data" = list("field1" = "value2"))
        ),
        "source" = list("name" = "file.csv", "size" = 100)
      )

This translates to JSON

`{ "entities": [...], "source": {"name": "file.csv", "size": 100} }`

You can provide `notes` to store the metadata about the request. The
metadata is included in the POST request as header `X-Action-Notes` and
can retrieved using Entity Audit Log.

## See also

<https://docs.getodk.org/central-api-entity-management/#creating-entities>

Other entity-management:
[`entity_audits()`](https://docs.ropensci.org/ruODK/reference/entity_audits.md),
[`entity_changes()`](https://docs.ropensci.org/ruODK/reference/entity_changes.md),
[`entity_delete()`](https://docs.ropensci.org/ruODK/reference/entity_delete.md),
[`entity_detail()`](https://docs.ropensci.org/ruODK/reference/entity_detail.md),
[`entity_list()`](https://docs.ropensci.org/ruODK/reference/entity_list.md),
[`entity_update()`](https://docs.ropensci.org/ruODK/reference/entity_update.md),
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

# Create a single entity
ec <- entity_create(
  did = did,
  label = "Entity label",
  notes = "Metadata about the created entity",
  data = list("field1" = "value1", "field2" = "value1")
)
ec

# Create multiple entities, example: test form "problems"
label <- c(
  glue::glue(
    "Entity {nrow(en) + 1} created by ruODK package test on {Sys.time()}"
  ),
  glue::glue(
    "Entity {nrow(en) + 2} created by ruODK package test on {Sys.time()}"
  )
)
notes <- glue::glue("Two entities created by ruODK package test on {Sys.time()}")
status <- c("needs_followup", "needs_followup")
details <- c("ruODK package test", "ruODK package test")
geometry <- c("-33.2 115.0 0.0 0.0", "-33.2 115.0 0.0 0.0")
data <- data.frame(status, details, geometry, stringsAsFactors = FALSE)
request_data <- list(
  "entities" = data.frame(label, data = I(data), stringsAsFactors = FALSE),
  "source" = list("name" = "file.csv", "size" = 100)
)

# Compare request_data to the schema expected by Central
# https://docs.getodk.org/central-api-entity-management/#creating-entities
# jsonlite::toJSON(request_data, pretty = TRUE, auto_unbox = TRUE)

ec <- entity_create(
  did = did,
  notes = notes,
  data = request_data
)
} # }
```
