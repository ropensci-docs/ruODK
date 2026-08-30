# Show whether a given semver is lesser than a baseline version.

Show whether a given semver is lesser than a baseline version.

## Usage

``` r
semver_lt(sv = get_default_odkc_version(), to = "1.5.0")
```

## Arguments

- sv:

  The semver to compare as character ("2023.5.1", "1.5.0", "1.5"), or
  numeric (1.5). The value is always parsed with
  `semver::parse_semver()`. Default: get_default_odkc_version().

- to:

  The semver to compare to as string. Although semver can parse complete
  version strings, `to` is still parsed by
  [`parse_odkc_version()`](https://docs.ropensci.org/ruODK/reference/parse_odkc_version.md)
  to ensure it is complete with major, minor, and patch version
  components.

## Value

A boolean indicating whether the given semver `sv` is greater than the
baseline semver `to`.

## See also

Other ru_settings:
[`odata_svc_parse()`](https://docs.ropensci.org/ruODK/reference/odata_svc_parse.md),
[`parse_odkc_version()`](https://docs.ropensci.org/ruODK/reference/parse_odkc_version.md),
[`ru_settings()`](https://docs.ropensci.org/ruODK/reference/ru_settings.md),
[`ru_setup()`](https://docs.ropensci.org/ruODK/reference/ru_setup.md),
[`semver_gt()`](https://docs.ropensci.org/ruODK/reference/semver_gt.md),
[`yell_if_error()`](https://docs.ropensci.org/ruODK/reference/yell_if_error.md),
[`yell_if_missing()`](https://docs.ropensci.org/ruODK/reference/yell_if_missing.md)

## Examples

``` r
get_default_odkc_version() |> semver_lt("0.8.0")
#> [1] FALSE
"2024.1.1" |> semver_lt("2024.1.0")
#> [1] FALSE
"2024.1.1" |> semver_lt("2024.1.1")
#> [1] FALSE
"2024.1.1" |> semver_lt("2024.1.2")
#> [1] TRUE
```
