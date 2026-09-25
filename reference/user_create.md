# Create a new User.

**\[experimental\]**

## Usage

``` r
user_create(
  email,
  password = NULL,
  url = get_default_url(),
  un = get_default_un(),
  pw = get_default_pw(),
  retries = get_retries()
)
```

## Arguments

- email:

  (character) The email address of the User account to create.

- password:

  (character) If provided, the User account is created with this
  password. Default: `NULL` (the User sets the password later).

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

A tibble with one row holding the new User's metadata as columns.

## Details

All that is required to create a new User is an email address. That
email address will receive a message instructing the new User on how to
claim the new account and set a password. Optionally, a password may
also be supplied as a part of this request. If it is, the account is
immediately usable with the given credentials. Users are not able to do
anything upon creation besides log in and change their own profile
information. To allow Users to perform useful actions, assign them one
or more Roles.

## See also

<https://docs.getodk.org/central-api-accounts-and-users/#creating-a-new-user>

Other user-management:
[`app_user_create()`](https://docs.ropensci.org/ruODK/reference/app_user_create.md),
[`app_user_delete()`](https://docs.ropensci.org/ruODK/reference/app_user_delete.md),
[`app_user_list()`](https://docs.ropensci.org/ruODK/reference/app_user_list.md),
[`assignment_actors()`](https://docs.ropensci.org/ruODK/reference/assignment_actors.md),
[`assignment_grant()`](https://docs.ropensci.org/ruODK/reference/assignment_grant.md),
[`assignment_list()`](https://docs.ropensci.org/ruODK/reference/assignment_list.md),
[`assignment_revoke()`](https://docs.ropensci.org/ruODK/reference/assignment_revoke.md),
[`form_assignment_list()`](https://docs.ropensci.org/ruODK/reference/form_assignment_list.md),
[`project_assignment_list()`](https://docs.ropensci.org/ruODK/reference/project_assignment_list.md),
[`role_detail()`](https://docs.ropensci.org/ruODK/reference/role_detail.md),
[`role_list()`](https://docs.ropensci.org/ruODK/reference/role_list.md),
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

u <- user_create(email = "new.user@example.com")

u |> knitr::kable()
} # }
```
