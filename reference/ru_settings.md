# Get or set `ruODK` settings.

**\[stable\]**

## Usage

``` r
ru_settings()

get_default_pid()

get_default_fid()

get_default_url()

get_default_un()

get_default_pw()

get_default_pp()

get_default_tz()

get_default_orders()

get_test_url()

get_test_un()

get_test_pw()

get_test_pid()

get_test_fid()

get_test_fid_zip()

get_test_fid_att()

get_test_fid_gap()

get_test_fid_wkt()

get_test_pp()

get_ru_verbose()

get_default_odkc_version()

get_test_odkc_version()

get_retries()
```

## Value

`ru_settings` prints your default ODK Central project ID, form ID, url,
username, and password, corresponding optional test server as well as
verbosity and HTTP request settings.
[`ru_setup`](https://docs.ropensci.org/ruODK/reference/ru_setup.md) sets
your production and test settings, while `get_(default/test)_*` get each
of those respective settings.

## See also

[`ru_setup`](https://docs.ropensci.org/ruODK/reference/ru_setup.md),
`get_default_pid`, `get_default_fid`, `get_default_url`,
`get_default_un`, `get_default_pw`, `get_default_pp`, `get_default_tz`,
`get_default_odkc_version`, `get_retries`, `get_test_pid`,
`get_test_fid`, `get_test_fid_zip`, `get_test_fid_att`,
`get_test_fid_gap`, `get_test_fid_wkt`, `get_test_url`, `get_test_un`,
`get_test_pw`, `get_test_pp`, `get_test_odkc_version`, `get_ru_verbose`.

Other ru_settings:
[`odata_svc_parse()`](https://docs.ropensci.org/ruODK/reference/odata_svc_parse.md),
[`parse_odkc_version()`](https://docs.ropensci.org/ruODK/reference/parse_odkc_version.md),
[`ru_setup()`](https://docs.ropensci.org/ruODK/reference/ru_setup.md),
[`semver_gt()`](https://docs.ropensci.org/ruODK/reference/semver_gt.md),
[`semver_lt()`](https://docs.ropensci.org/ruODK/reference/semver_lt.md),
[`yell_if_error()`](https://docs.ropensci.org/ruODK/reference/yell_if_error.md),
[`yell_if_missing()`](https://docs.ropensci.org/ruODK/reference/yell_if_missing.md)

## Examples

``` r
ru_settings()
#> <ruODK settings>
#>   Default ODK Central Project ID:  
#>   Default ODK Central Form ID:  
#>   Default ODK Central URL:  
#>   Default ODK Central Username:  
#>   Default ODK Central Password: run ruODK::get_default_pw() to show 
#>   Default ODK Central Passphrase: run ruODK::get_default_pp() to show 
#>   Default Time Zone: UTC 
#>   Default ODK Central Version: 2023.4.0 
#>   Default HTTP GET retries: 3 
#>   Verbose messages: FALSE 
#>   Test ODK Central Project ID:  
#>   Test ODK Central Form ID:  
#>   Test ODK Central Form ID (ZIP tests):  
#>   Test ODK Central Form ID (Attachment tests):  
#>   Test ODK Central Form ID (Parsing tests):  
#>   Test ODK Central Form ID (WKT tests):  
#>   Test ODK Central URL:  
#>   Test ODK Central Username:  
#>   Test ODK Central Password: run ruODK::get_test_pw() to show 
#>   Test ODK Central Passphrase: run ruODK::get_test_pp() to show 
#>   Test ODK Central Version: 2023.4.0 
```
