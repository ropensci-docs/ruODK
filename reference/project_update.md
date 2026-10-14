# Modify a Project.

**\[experimental\]**

## Usage

``` r
project_update(
  pid = get_default_pid(),
  name = NULL,
  description = NULL,
  archived = NULL,
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

  (character) The desired name of the Project. Default: `NULL`
  (unchanged).

- description:

  (character) The desired description of the Project. Default: `NULL`
  (unchanged).

- archived:

  (lgl) Archive the Project. Default: `NULL` (unchanged).

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

A tibble with one row holding the updated Project's metadata as columns,
as per the ODK Central API docs.

## Details

The Project name may be updated, as well as the Project description and
the archived flag. By default, archived is not set, which is equivalent
to false. If archived is set to true, the Project will be sorted to the
bottom of the list, and in the web management application the Project
will become effectively read-only. API write access is not affected.
Only the properties you supply are changed. Anything you do not supply
remains untouched.

## See also

<https://docs.getodk.org/central-api-project-management/#updating-project-details>

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
[`project_replace()`](https://docs.ropensci.org/ruODK/reference/project_replace.md)

## Examples

``` r
if (FALSE) { # \dontrun{
# See vignette("setup") for setup and authentication options
# ruODK::ru_setup(svc = "....svc", un = "me@email.com", pw = "...")

p <- project_create("Test Project")

p <- project_update(pid = p$id, description = "A test project.")

p$description
# > "A test project."
} # }
```
