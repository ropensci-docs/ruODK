# Show publicly accessible server configuration.

**\[experimental\]**

## Usage

``` r
config_public(
  url = get_default_url(),
  un = NULL,
  pw = NULL,
  retries = get_retries()
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

  (character) The ODK Central username. Optional: the endpoint needs no
  authentication. Default: `NULL` (anonymous).

- pw:

  (character) The ODK Central password. Optional: the endpoint needs no
  authentication. Default: `NULL` (anonymous).

- retries:

  The number of attempts to retrieve a web resource.

  This parameter is given to
  [`RETRY`](https://httr.r-lib.org/reference/RETRY.html)`(times = retries)`.

  Default: 3.

## Value

A list with the public server configuration as per the ODK Central API
docs.

## Details

This endpoint returns all server configuration that is publicly
accessible in a single object. This endpoint does not require
authentication. The following configurations are publicly accessible:
login-appearance, logo and hero-image. For configuration that stores
binary data (e.g. logo), this endpoint only returns metadata about the
configuration. This endpoint requires ODK Central 2026.1 or later.

## See also

<https://docs.getodk.org/central-api-system-endpoints/#getting-all-public-configuration>

Other server-management:
[`audit_get()`](https://docs.ropensci.org/ruODK/reference/audit_get.md)

## Examples

``` r
if (FALSE) { # \dontrun{
cfg <- config_public(url = "https://my.odkcentral.org")

names(cfg)
} # }
```
