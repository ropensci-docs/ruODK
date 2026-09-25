# Delete an App User.

**\[experimental\]**

## Usage

``` r
app_user_delete(
  pid = get_default_pid(),
  id,
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

- id:

  (numeric) The integer ID of the App User.

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

Deleting an App User revokes its access.

## See also

<https://docs.getodk.org/central-api-accounts-and-users/#deleting-an-app-user>

Other user-management:
[`app_user_create()`](https://docs.ropensci.org/ruODK/reference/app_user_create.md),
[`app_user_list()`](https://docs.ropensci.org/ruODK/reference/app_user_list.md),
[`assignment_actors()`](https://docs.ropensci.org/ruODK/reference/assignment_actors.md),
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

au <- app_user_list()

app_user_delete(id = au$id[[1]])
# > $success
# > [1] TRUE
} # }
```
