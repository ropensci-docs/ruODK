# List all users.

**\[maturing\]**

## Usage

``` r
user_list(
  qry = NULL,
  url = get_default_url(),
  un = get_default_un(),
  pw = get_default_pw(),
  retries = get_retries(),
  orders = get_default_orders(),
  tz = get_default_tz(),
  verbose = get_ru_verbose()
)
```

## Arguments

- qry:

  A query string to filter users by. The query string is not case
  sensitive and can contain special characters, such as `@`.

  The query string must be at least 5 alphabetic characters long to
  return good enough matches. E.g. `janet` will match a user with
  display name `Janette Doe`. E.g., `@dbca.wa` will match users with an
  email from `dbca.wa.gov.au`, whereas `@dbca.w` or `@dbca` will return
  no matches.

  Default: `NULL`.

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

- orders:

  (vector of character) Orders of datetime elements for lubridate.

  Default:
  `c("YmdHMS", "YmdHMSz", "Ymd HMS", "Ymd HMSz", "Ymd", "ymd")`.

- tz:

  A timezone to convert dates and times to.

  Read
  [`vignette("setup", package = "ruODK")`](https://docs.ropensci.org/ruODK/articles/setup.md)
  to learn how `ruODK`'s timezone can be set globally or per function.

- verbose:

  Whether to display debug messages or not.

  Read
  [`vignette("setup", package = "ruODK")`](https://docs.ropensci.org/ruODK/articles/setup.md)
  to learn how `ruODK`'s verbosity can be set globally or per function.

## Value

A tibble with user details as per the ODK Central API docs.

## Details

Currently, there are no paging or filtering options, so listing Users
will get you every User in the system, every time. Optionally, a q query
string parameter may be provided to filter the returned users by any
given string. The search is performed via a trigram similarity index
over both the Email and Display Name fields, and results are ordered by
match score, best matches first. If a q parameter is given, and it
exactly matches an email address that exists in the system, that user's
details will always be returned, even for actors who cannot user.list.
The request must still authenticate as a valid Actor. This allows
non-Administrators to choose a user for an action (e.g. grant rights)
without allowing full search.

Actors who cannot `user.list` will always receive \[\] with a 200 OK
response. ruODK does not (yet) warn if this is the case, and you (the
requesting Actor) have no permission to `user.list`.

## See also

<https://docs.getodk.org/central-api-accounts-and-users/#listing-all-users>

<https://www.postgresql.org/docs/9.6/pgtrgm.html>

## Examples

``` r
if (FALSE) { # \dontrun{
# See vignette("setup") for setup and authentication options
# ruODK::ru_setup(svc = "....svc", un = "me@email.com", pw = "...")

# All users
ul <- user_list()

# Search users
# Given a user with display name "Janette Doe" and email "@org.com.au"
user_list(qry = "jan") # no results, query string too short
user_list(qry = "jane") # no results, query string too short
user_list(qry = "janet") # returns Janette
user_list(qry = "@org") # no results, query string too short
user_list(qry = "@org.c") # no results, query string too short
user_list(qry = "@org.co") # returns all users matching "@org.co"

# Actor not allowed to user.list
user_list() # If this is empty, you might not have permissions to list users
} # }
```
