# Configure default [`ruODK`](https://docs.ropensci.org/ruODK/reference/ruODK-package.md) settings.

Settings are returned invisibly and additionally printed depending on
[`get_ru_verbose`](https://docs.ropensci.org/ruODK/reference/ru_settings.md).

## Usage

``` r
ru_setup(
  svc = NULL,
  pid = NULL,
  fid = NULL,
  url = NULL,
  un = NULL,
  pw = NULL,
  pp = NULL,
  tz = NULL,
  odkc_version = NULL,
  retries = NULL,
  verbose = NULL,
  test_svc = NULL,
  test_pid = NULL,
  test_fid = NULL,
  test_fid_zip = NULL,
  test_fid_att = NULL,
  test_fid_gap = NULL,
  test_fid_wkt = NULL,
  test_url = NULL,
  test_un = NULL,
  test_pw = NULL,
  test_pp = NULL,
  test_odkc_version = NULL
)
```

## Arguments

- svc:

  (optional, character) The OData service URL of a form. This parameter
  will set `pid`, `fid`, and `url`. It is sufficient to supply `svc`,
  `un`, and `pw`.

- pid:

  (optional, character) The ID of an existing project on `url`. This
  will override the project ID from `svc`. A numeric value for `pid`
  will be converted to character.

- fid:

  (optional, character) The alphanumeric ID of an existing form in
  `pid`. This will override the form ID from `svc`.

- url:

  An ODK Central URL, e.g. "https://sandbox.central.getodk.org". This
  will override the ODK Central base URL from `svc`.

- un:

  An ODK Central username which is the email of a "web user" in the
  specified ODK Central instance `url` (optional, character).

- pw:

  The password for user `un` (optional, character).

- pp:

  The passphrase (optional, character) for an encrypted form.

- tz:

  Global default time zone. `ruODK`'s time zone is determined in order
  of precedence:

  - Function parameter: e.g.
    [`odata_submission_get`](https://docs.ropensci.org/ruODK/reference/odata_submission_get.md)`(tz = "Australia/Perth")`

  - `ruODK` setting: `ru_setup(tz = "Australia/Perth")`

  - Environment variable `RU_TIMEZONE` (e.g. set in `.Renviron`)

  - UTC (GMT+00)

- odkc_version:

  The ODK Central version as major/minor version, e.g. 1.1.

- retries:

  The number of attempts to retrieve a web resource.

  This parameter is given to
  [`RETRY`](https://httr.r-lib.org/reference/RETRY.html)`(times = retries)`.

  Default: 3.

- verbose:

  Global default for `ruODK` verbosity. `ruODK` verbosity is determined
  in order of precedence:

  - Function parameter: e.g.
    [`odata_submission_get`](https://docs.ropensci.org/ruODK/reference/odata_submission_get.md)`(verbose = TRUE)`

  - `ruODK` setting: `ru_setup(verbose = TRUE)`

  - Environment variable `RU_VERBOSE` (e.g. set in `.Renviron`)

  - `FALSE`.

- test_svc:

  (optional, character) The OData service URL of a test form. This
  parameter will set `test_pid`, `test_fid`, and `test_url`. It is
  sufficient to supply `test_svc`, `test_un`, and `test_pw` to configure
  testing.

- test_pid:

  (optional, character) The numeric ID of an existing project on
  `test_url`. This will override the project ID from `test_svc`. A
  numeric value for `test_pid` will be converted to character.

- test_fid:

  (optional, character) The alphanumeric ID of an existing form in
  `test_pid`. This will override the form ID from `test_svc`. This form
  is used as default form in all tests, examples, vignettes, data, and
  Rmd templates.

- test_fid_zip:

  (optional, character) The alphanumeric ID of an existing form in
  `test_pid`. This will override the form ID from `test_svc`. Provide
  the form ID of a form with few submissions and without attachments.
  This form is used to test the repeated download of all form
  submissions.

- test_fid_att:

  (optional, character) The alphanumeric ID of an existing form in
  `test_pid`. This will override the form ID from `test_svc`. Provide
  the form ID of a form with few submissions and few attachments. This
  form is used to test downloading and linking attachments.

- test_fid_gap:

  (optional, character) The alphanumeric ID of an existing form in
  `test_pid`. This will override the form ID from `test_svc`. Provide
  the form ID of a form with gaps in the first submission. This form is
  used to test parsing incomplete submissions.

- test_fid_wkt:

  (optional, character) The alphanumeric ID of an existing form in
  `test_pid`. This will override the form ID from `test_svc`. Provide
  the form ID of a form with geopoints, geotraces, and geoshapes.

- test_url:

  (optional, character) A valid ODK Central URL for testing. This will
  override the ODK Central base URL from `svc`.

- test_un:

  (optional, character) A valid ODK Central username (email) privileged
  to view the test project(s) at `test_url`.

- test_pw:

  (optional, character) The valid ODK Central password for `test_un`.

- test_pp:

  (optional, character) The valid passphrase to decrypt the data of
  encrypted project `test_pid` for download, only used for tests.

- test_odkc_version:

  The ODK Central test server's version as major/minor version, e.g.
  1.1.

## Details

**\[stable\]**

`ru_setup` sets ODK Central connection details.
[`ruODK`](https://docs.ropensci.org/ruODK/reference/ruODK-package.md)'s
functions default to use the default project ID, form ID, URL, username,
and password unless specified explicitly.

Any parameters not specified will remain unchanged. It is therefore
possible to set up username and password initially with
`ru_setup(un="XXX", pw="XXX")`, and switch between forms with
`ru_setup(svc="XXX")`, supplying the form's OData service URL. ODK
Central conveniently provides the OData service URL in the form
submission tab, which in turn contains base URL, project ID, and form
ID.

[`ruODK`](https://docs.ropensci.org/ruODK/reference/ruODK-package.md)'s
automated tests require a valid ODK Central URL, and a privileged
username and password of a "web user" on that ODK Central instance, as
well as an existing project and form.

## See also

Other ru_settings:
[`odata_svc_parse()`](https://docs.ropensci.org/ruODK/reference/odata_svc_parse.md),
[`parse_odkc_version()`](https://docs.ropensci.org/ruODK/reference/parse_odkc_version.md),
[`ru_settings()`](https://docs.ropensci.org/ruODK/reference/ru_settings.md),
[`semver_gt()`](https://docs.ropensci.org/ruODK/reference/semver_gt.md),
[`semver_lt()`](https://docs.ropensci.org/ruODK/reference/semver_lt.md),
[`yell_if_error()`](https://docs.ropensci.org/ruODK/reference/yell_if_error.md),
[`yell_if_missing()`](https://docs.ropensci.org/ruODK/reference/yell_if_missing.md)

## Examples

``` r
# `ruODK` users only need default settings to their ODK Central:
ru_setup(url = "https://my-odkc.com", un = "me@email.com", pw = "...")

# `ruODK` contributors and maintainers need specific ODK Central
# instances to run tests and build vignettes, see contributing guide:
ru_setup(
  url = "https://odkcentral.dbca.wa.gov.au",
  un = "me@email.com",
  pw = "...",
  pp = "...",
  test_url = "https://sandbox.central.getodk.org",
  test_un = "me@email.com",
  test_pw = "...",
  test_pp = "...",
  test_pid = 14,
  test_fid = "build_Flora-Quadrat-0-2_1558575936",
  test_fid_zip = "build_Spotlighting-0-6_1558333698",
  test_fid_att = "build_Flora-Quadrat-0-1_1558330379",
  test_fid_gap = "build_Turtle-Track-or-Nest-1-0_1569907666",
  test_fid_wkt = "build_Locations_1589344221",
  retries = 3,
  verbose = TRUE
)
#> <ruODK settings>
#>   Default ODK Central Project ID:  
#>   Default ODK Central Form ID:  
#>   Default ODK Central URL: https://odkcentral.dbca.wa.gov.au 
#>   Default ODK Central Username: me@email.com 
#>   Default ODK Central Password: run ruODK::get_default_pw() to show 
#>   Default ODK Central Passphrase: run ruODK::get_default_pp() to show 
#>   Default Time Zone: UTC 
#>   Default ODK Central Version: 2023.4.0 
#>   Default HTTP GET retries: 3 
#>   Verbose messages: TRUE 
#>   Test ODK Central Project ID: 14 
#>   Test ODK Central Form ID: build_Flora-Quadrat-0-2_1558575936 
#>   Test ODK Central Form ID (ZIP tests): build_Spotlighting-0-6_1558333698 
#>   Test ODK Central Form ID (Attachment tests): build_Flora-Quadrat-0-1_1558330379 
#>   Test ODK Central Form ID (Parsing tests): build_Turtle-Track-or-Nest-1-0_1569907666 
#>   Test ODK Central Form ID (WKT tests): build_Locations_1589344221 
#>   Test ODK Central URL: https://sandbox.central.getodk.org 
#>   Test ODK Central Username: me@email.com 
#>   Test ODK Central Password: run ruODK::get_test_pw() to show 
#>   Test ODK Central Passphrase: run ruODK::get_test_pp() to show 
#>   Test ODK Central Version: 2023.4.0 
```
