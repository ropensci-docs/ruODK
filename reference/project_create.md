# Create a new project.

**\[experimental\]**

## Usage

``` r
project_create(
  name,
  url = get_default_url(),
  un = get_default_un(),
  pw = get_default_pw()
)
```

## Arguments

- name:

  The desired name of the project. Can contain whitespace.

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

## Value

A tibble with one row per project and all project metadata as columns as
per ODK Central API docs.

## See also

<https://docs.getodk.org/central-api-project-management/#creating-a-project>

Other project-management:
[`project_detail()`](https://docs.ropensci.org/ruODK/reference/project_detail.md),
[`project_list()`](https://docs.ropensci.org/ruODK/reference/project_list.md)

## Examples

``` r
if (FALSE) { # \dontrun{
# See vignette("setup") for setup and authentication options
# ruODK::ru_setup(svc = "....svc", un = "me@email.com", pw = "...")

p <- project_create("Test Project")
knitr::kable(p)

# project_create returns a tibble
class(p)
# > "tbl_df" "tbl" "data.frame"

# columns are project metadata
names(p)
# > "id" "name" "archived"
} # }
```
