# Warn when previous Form versions hold fields missing from the current one.

**\[experimental\]**

## Usage

``` r
warn_on_schema_drift(
  current_schema,
  pid = get_default_pid(),
  fid = get_default_fid(),
  url = get_default_url(),
  un = get_default_un(),
  pw = get_default_pw(),
  odkc_version = get_default_odkc_version(),
  retries = get_retries()
)
```

## Arguments

- current_schema:

  The current form schema as returned by
  [`form_schema`](https://docs.ropensci.org/ruODK/reference/form_schema.md).

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

- retries:

  The number of attempts to retrieve a web resource.

  This parameter is given to
  [`RETRY`](https://httr.r-lib.org/reference/RETRY.html)`(times = retries)`.

  Default: 3.

## Value

`NULL`, invisibly.

## Details

Central's OData feed uses only the current Form definition: fields that
a previous published version held at another path (removed, renamed, or
moved to another group or repeat) do not appear in the download, while
the stored Submission XML keeps their values. This helper compares the
paths of every published Form version against the current schema and
warns about paths that have no current equivalent. To include fields
from all versions, use
[`submission_export`](https://docs.ropensci.org/ruODK/reference/submission_export.md)
with `deleted_fields = TRUE`.

Failures while listing versions or reading a version schema are ignored:
the check must never break a download.

The warning is unconditional: it is not gated by `verbose`, as lost
values must never pass silently.

## See also

Other odata-api:
[`odata_metadata_get()`](https://docs.ropensci.org/ruODK/reference/odata_metadata_get.md),
[`odata_service_get()`](https://docs.ropensci.org/ruODK/reference/odata_service_get.md),
[`odata_submission_get()`](https://docs.ropensci.org/ruODK/reference/odata_submission_get.md)
