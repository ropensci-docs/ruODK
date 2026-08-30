# Retrieve URL, project ID, and form ID from an ODK Central OData service URL.

**\[stable\]**

## Usage

``` r
odata_svc_parse(svc)
```

## Arguments

- svc:

  (character) The OData service URL of a form as provided by the ODK
  Central form submissions tab. Example:
  "https://URL/v1/projects/PID/forms/FID.svc"

## Value

A named list with three components (all of type character):

- `url` The ODK Central base URL.

- `pid` The project ID.

- `fid` The form ID.

## See also

Other ru_settings:
[`parse_odkc_version()`](https://docs.ropensci.org/ruODK/reference/parse_odkc_version.md),
[`ru_settings()`](https://docs.ropensci.org/ruODK/reference/ru_settings.md),
[`ru_setup()`](https://docs.ropensci.org/ruODK/reference/ru_setup.md),
[`semver_gt()`](https://docs.ropensci.org/ruODK/reference/semver_gt.md),
[`semver_lt()`](https://docs.ropensci.org/ruODK/reference/semver_lt.md),
[`yell_if_error()`](https://docs.ropensci.org/ruODK/reference/yell_if_error.md),
[`yell_if_missing()`](https://docs.ropensci.org/ruODK/reference/yell_if_missing.md)
