# List all projects.

While the API endpoint will return all projects, `project_list` will
fail with incorrect or missing authentication.

## Usage

``` r
project_list(
  url = get_default_url(),
  un = get_default_un(),
  pw = get_default_pw(),
  retries = get_retries(),
  orders = get_default_orders(),
  tz = get_default_tz()
)
```

## Arguments

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

## Value

A tibble with one row per project and all project metadata as columns as
per ODK Central API docs.

## Details

**\[stable\]**

## See also

<https://docs.getodk.org/central-api-project-management/#listing-projects>

Other project-management:
[`project_create()`](https://docs.ropensci.org/ruODK/reference/project_create.md),
[`project_detail()`](https://docs.ropensci.org/ruODK/reference/project_detail.md)

## Examples

``` r
if (FALSE) { # \dontrun{
# See vignette("setup") for setup and authentication options
# ruODK::ru_setup(svc = "....svc", un = "me@email.com", pw = "...")

pl <- project_list()
knitr::kable(pl)

# project_list returns a tibble
class(pl)
# > "tbl_df" "tbl" "data.frame"

# columns are project metadata
names(pl)
# > "id" "name" "forms" "app_users" "created_at" "updated_at"
# > "last_submission" "archived"
} # }
```
