# Warn about failed web requests and give helpful troubleshooting tips.

**\[stable\]**

## Usage

``` r
yell_if_error(response, url, un, pw, pid = NULL, fid = NULL)
```

## Arguments

- response:

  A httr response object

- url:

  A URL (character)

- un:

  A username (character)

- pw:

  A password (character)

- pid:

  A project ID (numeric, optional)

- fid:

  A form ID (character, optional)

## Value

The response object

## Details

A wrapper around
[`httr::stop_for_status`](https://httr.r-lib.org/reference/stop_for_status.html)
with a more helpful error message. Examples: see tests for
[`project_list`](https://docs.ropensci.org/ruODK/reference/project_list.md).
This function is used internally but may be useful for debugging and
[`ruODK`](https://docs.ropensci.org/ruODK/reference/ruODK-package.md)
development.

## See also

Other ru_settings:
[`odata_svc_parse()`](https://docs.ropensci.org/ruODK/reference/odata_svc_parse.md),
[`parse_odkc_version()`](https://docs.ropensci.org/ruODK/reference/parse_odkc_version.md),
[`ru_settings()`](https://docs.ropensci.org/ruODK/reference/ru_settings.md),
[`ru_setup()`](https://docs.ropensci.org/ruODK/reference/ru_setup.md),
[`semver_gt()`](https://docs.ropensci.org/ruODK/reference/semver_gt.md),
[`semver_lt()`](https://docs.ropensci.org/ruODK/reference/semver_lt.md),
[`yell_if_missing()`](https://docs.ropensci.org/ruODK/reference/yell_if_missing.md)
