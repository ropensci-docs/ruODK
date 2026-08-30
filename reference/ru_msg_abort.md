# rlang::abort() with a red error message with a cross symbol.

**\[stable\]**

## Usage

``` r
ru_msg_abort(message)
```

## Arguments

- message:

  (chr) A message to print

## See also

Other messaging:
[`ru_msg_info()`](https://docs.ropensci.org/ruODK/reference/ru_msg_info.md),
[`ru_msg_noop()`](https://docs.ropensci.org/ruODK/reference/ru_msg_noop.md),
[`ru_msg_success()`](https://docs.ropensci.org/ruODK/reference/ru_msg_success.md),
[`ru_msg_warn()`](https://docs.ropensci.org/ruODK/reference/ru_msg_warn.md)

## Examples

``` r
if (FALSE) { # \dontrun{
ru_msg_abort("This is an error, abort.")
} # }
```
