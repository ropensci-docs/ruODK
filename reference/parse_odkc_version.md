# Parse a given ODK Central version string or number into a `semver`.

**\[stable\]**

## Usage

``` r
parse_odkc_version(v, env_var = "ODKC_VERSION")
```

## Arguments

- v:

  A string (e.g. "ODKC_VERSION=") or number (e.g. 0.8, 1.5) of a
  complete or partial semver, or a semver of class "svlist".

- env_var:

  A string indicating which environment variable was targeted. This is
  used in the warning to advise which environment variable to update. If
  set to an empty string, the warning message is suppressed. Default:
  "ODKC_VERSION".

## Value

semver::svlist The version as semver of major, minor, and patch.

## Details

Past versions of ruODK advised to set ODKC_VERSION to a floating point
number indicating major and minor versions, e.g. `ODKC_VERSION=0.7` or
`ODKC_VERSION=1.5`.

ODK Central has since switched to semantic versioning, e.g.
`ODKC_VERSION=ODKC_VERSION=`.

To preserve backwards compatibility, ruODK handles both formats
gracefully, but emits a helpful warning to update the version string if
the older format is detected, or the version string is missing the minor
or patch version.

## See also

Other ru_settings:
[`odata_svc_parse()`](https://docs.ropensci.org/ruODK/reference/odata_svc_parse.md),
[`ru_settings()`](https://docs.ropensci.org/ruODK/reference/ru_settings.md),
[`ru_setup()`](https://docs.ropensci.org/ruODK/reference/ru_setup.md),
[`semver_gt()`](https://docs.ropensci.org/ruODK/reference/semver_gt.md),
[`semver_lt()`](https://docs.ropensci.org/ruODK/reference/semver_lt.md),
[`yell_if_error()`](https://docs.ropensci.org/ruODK/reference/yell_if_error.md),
[`yell_if_missing()`](https://docs.ropensci.org/ruODK/reference/yell_if_missing.md)

## Examples

``` r
parse_odkc_version("1.2.3")
#> [1] Maj: 1 Min: 2 Pat: 3
#> 

# Warn: too short
parse_odkc_version("1")
#> [1] Maj: 1 Min: 0 Pat: 0
#> 
parse_odkc_version("1.2")
#> [1] Maj: 1 Min: 2 Pat: 0
#> 

# Warn: too long
parse_odkc_version("1.2.3.4")
#> [1] Maj: 1 Min: 2 Pat: 3
#> 

# Warn: otherwise invalid
parse_odkc_version("1.2.")
#> [1] Maj: 1 Min: 2 Pat: 0
#> 
parse_odkc_version(".2.3")
#> [1] Maj: 0 Min: 2 Pat: 3
#> 
```
