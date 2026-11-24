# List Role-specific Form Assignments within a Project.

**\[experimental\]**

## Usage

``` r
form_assignment_role_list(
  pid = get_default_pid(),
  role_id,
  url = get_default_url(),
  un = get_default_un(),
  pw = get_default_pw(),
  retries = get_retries(),
  odkc_version = get_default_odkc_version()
)
```

## Arguments

- pid:

  The numeric ID of the project, e.g.: 2.

  Default:
  [`get_default_pid`](https://docs.ropensci.org/ruODK/reference/ru_settings.md).

  Set default `pid` through `ru_setup(pid="...")`.

  See `vignette("Setup", package = "ruODK")`.

- role_id:

  (numeric) The numeric ID of the Role.

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

## Value

A tibble with one row for each Form Assignment of the Role as per the
ODK Central API docs.

## Details

Like the Form Assignments summary, but filtered by some Role. Returned
results include an `xmlFormId` field to specify which Form each
Assignment is attached to. This endpoint requires ODK Central v0.7 or
later.

## See also

<https://docs.getodk.org/central-api-project-management/#seeing-role-specific-form-assignments-within-a-project>

Other project-management:
[`project_assignment_actors()`](https://docs.ropensci.org/ruODK/reference/project_assignment_actors.md),
[`project_assignment_grant()`](https://docs.ropensci.org/ruODK/reference/project_assignment_grant.md),
[`project_assignment_revoke()`](https://docs.ropensci.org/ruODK/reference/project_assignment_revoke.md),
[`project_create()`](https://docs.ropensci.org/ruODK/reference/project_create.md),
[`project_delete()`](https://docs.ropensci.org/ruODK/reference/project_delete.md),
[`project_detail()`](https://docs.ropensci.org/ruODK/reference/project_detail.md),
[`project_enable_encryption()`](https://docs.ropensci.org/ruODK/reference/project_enable_encryption.md),
[`project_list()`](https://docs.ropensci.org/ruODK/reference/project_list.md),
[`project_replace()`](https://docs.ropensci.org/ruODK/reference/project_replace.md),
[`project_update()`](https://docs.ropensci.org/ruODK/reference/project_update.md)

## Examples

``` r
if (FALSE) { # \dontrun{
# See vignette("setup") for setup and authentication options
# ruODK::ru_setup(svc = "....svc", un = "me@email.com", pw = "...")

fa <- form_assignment_role_list(role_id = 2)

fa |> knitr::kable()
} # }
```
