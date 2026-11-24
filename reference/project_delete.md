# Delete a Project.

**\[experimental\]**

## Usage

``` r
project_delete(
  pid = get_default_pid(),
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

A list with a single element `success` (`TRUE`) as per the ODK Central
API docs.

## Details

Deleting a Project removes it from the management interface and makes it
permanently inaccessible. Do not do this unless you are certain you will
never need any of its data again.

## See also

<https://docs.getodk.org/central-api-project-management/#deleting-a-project>

Other project-management:
[`form_assignment_role_list()`](https://docs.ropensci.org/ruODK/reference/form_assignment_role_list.md),
[`project_assignment_actors()`](https://docs.ropensci.org/ruODK/reference/project_assignment_actors.md),
[`project_assignment_grant()`](https://docs.ropensci.org/ruODK/reference/project_assignment_grant.md),
[`project_assignment_revoke()`](https://docs.ropensci.org/ruODK/reference/project_assignment_revoke.md),
[`project_create()`](https://docs.ropensci.org/ruODK/reference/project_create.md),
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

p <- project_create("Temporary Project")

project_delete(p$id)
# > $success
# > [1] TRUE
} # }
```
