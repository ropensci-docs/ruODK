# List all Actors assigned some server-wide Role.

**\[experimental\]**

## Usage

``` r
assignment_actors(
  role_id,
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

- role_id:

  (character or numeric) The Role ID, typically the integer ID of the
  Role. A Role system name can also be supplied if the Role has one.

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

A tibble with one row for each Actor assigned the Role as per the ODK
Central API docs. Column names are renamed from ODK's `camelCase` to
`snake_case`.

## Details

Given a Role, this endpoint lists all Actors that have been assigned
that Role upon the entire system. This endpoint requires ODK Central
v0.5 or later.

## See also

<https://docs.getodk.org/central-api-accounts-and-users/#listing-all-actors-assigned-some-role>

Other user-management:
[`app_user_create()`](https://docs.ropensci.org/ruODK/reference/app_user_create.md),
[`app_user_delete()`](https://docs.ropensci.org/ruODK/reference/app_user_delete.md),
[`app_user_list()`](https://docs.ropensci.org/ruODK/reference/app_user_list.md),
[`assignment_grant()`](https://docs.ropensci.org/ruODK/reference/assignment_grant.md),
[`assignment_list()`](https://docs.ropensci.org/ruODK/reference/assignment_list.md),
[`assignment_revoke()`](https://docs.ropensci.org/ruODK/reference/assignment_revoke.md),
[`form_assignment_list()`](https://docs.ropensci.org/ruODK/reference/form_assignment_list.md),
[`project_assignment_list()`](https://docs.ropensci.org/ruODK/reference/project_assignment_list.md),
[`role_detail()`](https://docs.ropensci.org/ruODK/reference/role_detail.md),
[`role_list()`](https://docs.ropensci.org/ruODK/reference/role_list.md),
[`user_create()`](https://docs.ropensci.org/ruODK/reference/user_create.md),
[`user_delete()`](https://docs.ropensci.org/ruODK/reference/user_delete.md),
[`user_detail()`](https://docs.ropensci.org/ruODK/reference/user_detail.md),
[`user_list()`](https://docs.ropensci.org/ruODK/reference/user_list.md),
[`user_preference_project_delete()`](https://docs.ropensci.org/ruODK/reference/user_preference_project_delete.md),
[`user_preference_project_set()`](https://docs.ropensci.org/ruODK/reference/user_preference_project_set.md),
[`user_preference_site_delete()`](https://docs.ropensci.org/ruODK/reference/user_preference_site_delete.md),
[`user_preference_site_set()`](https://docs.ropensci.org/ruODK/reference/user_preference_site_set.md),
[`user_reset_password()`](https://docs.ropensci.org/ruODK/reference/user_reset_password.md),
[`user_update()`](https://docs.ropensci.org/ruODK/reference/user_update.md),
[`user_update_password()`](https://docs.ropensci.org/ruODK/reference/user_update_password.md)

## Examples

``` r
if (FALSE) { # \dontrun{
# See vignette("setup") for setup and authentication options
# ruODK::ru_setup(svc = "....svc", un = "me@email.com", pw = "...")

aa <- assignment_actors(role_id = "admin")

aa |> knitr::kable()
} # }
```
