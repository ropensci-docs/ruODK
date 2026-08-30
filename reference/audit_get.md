# Get server audit log entries.

**\[stable\]**

## Usage

``` r
audit_get(
  action = NULL,
  start = NULL,
  end = NULL,
  limit = NULL,
  offset = NULL,
  url = Sys.getenv("ODKC_URL"),
  un = Sys.getenv("ODKC_UN"),
  pw = Sys.getenv("ODKC_PW"),
  retries = get_retries()
)
```

## Arguments

- action:

  string. The action to filter the logs, e.g. "user.create". See
  <https://docs.getodk.org/central-api-system-endpoints/#getting-audit-log-entries>
  for the full list of available actions.

- start:

  string. The ISO8601 timestamp of the earliest log entry to return.
  E.g. `2000-01-01z` or `2000-12-31T23:59.999z`,
  `2000-01-01T12:12:12+08` or `2000-01-01+08`.

- end:

  string. The ISO8601 timestamp of the last log entry to return.

- limit:

  integer. The max number of log entries to return.

- offset:

  integer. The number of log entries to skip.

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

A tibble containing server audit logs. One row per audited action,
columns are submission attributes:

- actor_id: integer. The ID of the actor, if any, that initiated the
  action.

- action: string. The action that was taken.

- actee_id: uuid, string. The ID of the permissioning object against
  which the action was taken.

- details: list. Additional details about the action that vary according
  to the type of action.

- logged_at: dttm. Time of action on server.

## Details

Parameters to filter the audit logs:
`action=form.create&start=2000-01-01z&end=2000-12-31T23%3A59.999z`

## See also

<https://docs.getodk.org/central-api-system-endpoints/#getting-audit-log-entries>

## Examples

``` r
if (FALSE) { # \dontrun{
# See vignette("setup") for setup and authentication options
# ruODK::ru_setup(svc = "....svc", un = "me@email.com", pw = "...")

logs <- audit_get()

# With search parameters
logs <- audit_get(
  action = "project.update",
  start = "2019-08-01Z",
  end = "2019-08-31Z",
  limit = 100,
  offset = 0
)

# With partial search parameters
logs <- audit_get(
  limit = 100,
  offset = 0
)

logs %>% knitr::kable(.)

# audit_get returns a tibble
class(logs)
# > c("tbl_df", "tbl", "data.frame")

# Audit details
names(logs)
# > "actor_id" "action" "actee_id" "details" "logged_at"
} # }
```
