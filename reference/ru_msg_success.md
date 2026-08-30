# Print a green success message with a tick symbol.

**\[stable\]**

## Usage

``` r
ru_msg_success(message, verbose = get_ru_verbose())
```

## Arguments

- message:

  (chr) A message to print

- verbose:

  Whether to display debug messages or not.

  Read
  [`vignette("setup", package = "ruODK")`](https://docs.ropensci.org/ruODK/articles/setup.md)
  to learn how `ruODK`'s verbosity can be set globally or per function.

## See also

Other messaging:
[`ru_msg_abort()`](https://docs.ropensci.org/ruODK/reference/ru_msg_abort.md),
[`ru_msg_info()`](https://docs.ropensci.org/ruODK/reference/ru_msg_info.md),
[`ru_msg_noop()`](https://docs.ropensci.org/ruODK/reference/ru_msg_noop.md),
[`ru_msg_warn()`](https://docs.ropensci.org/ruODK/reference/ru_msg_warn.md)

## Examples

``` r
ru_msg_success("This is a success message.")
#> NULL
```
