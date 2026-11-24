# Replace a Project.

**\[experimental\]**

## Usage

``` r
project_replace(
  pid = get_default_pid(),
  name,
  description = "",
  archived = FALSE,
  url = get_default_url(),
  un = get_default_un(),
  pw = get_default_pw(),
  retries = get_retries()
)
```

## Arguments

- pid:

  The numeric ID of the project, e.g.: 2.

  Default:
  [`get_default_pid`](https://docs.ropensci.org/ruODK/reference/ru_settings.md).

  Set default `pid` through `ru_setup(pid="...")`.

  See `vignette("Setup", package = "ruODK")`.

- name:

  (character) The desired name of the Project.

- description:

  (character) The desired description of the Project.

- archived:

  (lgl) Archive the Project.

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

## Value

A tibble with one row holding the replaced Project's metadata as
columns, as per the ODK Central API docs.

## Details

This endpoint allows a deep update of Project metadata, Form metadata,
and Form Assignment metadata at once and transactionally using a nested
data format. This function replaces the top-level Project metadata. Each
call sends the complete `name`, `description` and `archived` flag.
Omitted Form detail is left as-is, but this function sends no Form
detail. Form states and assignments need a direct call to the ODK
Central API.

## See also

<https://docs.getodk.org/central-api-project-management/#deep-updating-project-and-form-details>

Other project-management:
[`form_assignment_role_list()`](https://docs.ropensci.org/ruODK/reference/form_assignment_role_list.md),
[`project_assignment_actors()`](https://docs.ropensci.org/ruODK/reference/project_assignment_actors.md),
[`project_assignment_grant()`](https://docs.ropensci.org/ruODK/reference/project_assignment_grant.md),
[`project_assignment_revoke()`](https://docs.ropensci.org/ruODK/reference/project_assignment_revoke.md),
[`project_create()`](https://docs.ropensci.org/ruODK/reference/project_create.md),
[`project_delete()`](https://docs.ropensci.org/ruODK/reference/project_delete.md),
[`project_detail()`](https://docs.ropensci.org/ruODK/reference/project_detail.md),
[`project_enable_encryption()`](https://docs.ropensci.org/ruODK/reference/project_enable_encryption.md),
[`project_list()`](https://docs.ropensci.org/ruODK/reference/project_list.md),
[`project_update()`](https://docs.ropensci.org/ruODK/reference/project_update.md)

## Examples

``` r
if (FALSE) { # \dontrun{
# See vignette("setup") for setup and authentication options
# ruODK::ru_setup(svc = "....svc", un = "me@email.com", pw = "...")

p <- project_create("Test Project")

p <- project_replace(
  pid = p$id,
  name = "Renamed Project",
  description = "A test project.",
  archived = FALSE
)

p$name
# > "Renamed Project"
} # }
```
