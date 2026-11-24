# Print ruODK settings.

Prints the default and test settings as returned by
[`ru_settings`](https://docs.ropensci.org/ruODK/reference/ru_settings.md),
without revealing passwords.

## Usage

``` r
# S3 method for class 'ru_settings'
print(x, ...)
```

## Arguments

- x:

  A `ru_settings` object.

- ...:

  Ignored.

## Value

`NULL`, invisibly. Called for its side effect.

## See also

Other ru_settings:
[`odata_svc_parse()`](https://docs.ropensci.org/ruODK/reference/odata_svc_parse.md),
[`parse_odkc_version()`](https://docs.ropensci.org/ruODK/reference/parse_odkc_version.md),
[`ru_settings()`](https://docs.ropensci.org/ruODK/reference/ru_settings.md),
[`ru_setup()`](https://docs.ropensci.org/ruODK/reference/ru_setup.md),
[`semver_gt()`](https://docs.ropensci.org/ruODK/reference/semver_gt.md),
[`semver_lt()`](https://docs.ropensci.org/ruODK/reference/semver_lt.md),
[`yell_if_error()`](https://docs.ropensci.org/ruODK/reference/yell_if_error.md),
[`yell_if_missing()`](https://docs.ropensci.org/ruODK/reference/yell_if_missing.md)

## Examples

``` r
print(ru_settings())
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
