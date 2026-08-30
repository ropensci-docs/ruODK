# Abort on missing ODK Central credentials (url, username, password).

**\[stable\]**

## Usage

``` r
yell_if_missing(
  url,
  un,
  pw,
  pid = NULL,
  fid = NULL,
  iid = NULL,
  did = NULL,
  eid = NULL
)
```

## Arguments

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

- iid:

  A submission instance ID (character, optional)

- did:

  An Entity List (dataset) name (character, optional)

- eid:

  An Entity UUID (character, optional)

## Details

This is a helper function to pat down
[`ruODK`](https://docs.ropensci.org/ruODK/reference/ruODK-package.md)
functions for missing credentials and stop with a loud but informative
yell.

## See also

Other ru_settings:
[`odata_svc_parse()`](https://docs.ropensci.org/ruODK/reference/odata_svc_parse.md),
[`parse_odkc_version()`](https://docs.ropensci.org/ruODK/reference/parse_odkc_version.md),
[`ru_settings()`](https://docs.ropensci.org/ruODK/reference/ru_settings.md),
[`ru_setup()`](https://docs.ropensci.org/ruODK/reference/ru_setup.md),
[`semver_gt()`](https://docs.ropensci.org/ruODK/reference/semver_gt.md),
[`semver_lt()`](https://docs.ropensci.org/ruODK/reference/semver_lt.md),
[`yell_if_error()`](https://docs.ropensci.org/ruODK/reference/yell_if_error.md)

## Examples

``` r
testthat::expect_error(yell_if_missing("", "username", "password"))
testthat::expect_error(yell_if_missing("url", "", "password"))
testthat::expect_error(yell_if_missing("url", "username", ""))
testthat::expect_error(yell_if_missing(NULL, "", ""))
testthat::expect_error(yell_if_missing("", "", ""))
testthat::expect_error(yell_if_missing("", "", "", ""))
testthat::expect_error(yell_if_missing("", "", "", "", ""))
testthat::expect_error(yell_if_missing("", "", "", "", "", ""))
testthat::expect_error(yell_if_missing("", "", "", "", "", "", ""))
testthat::expect_error(yell_if_missing("", "", "", "", "", "", "", ""))
```
