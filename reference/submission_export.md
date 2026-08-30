# Export all form submissions including repeats and attachments to CSV.

**\[maturing\]**

## Usage

``` r
submission_export(
  local_dir = here::here(),
  overwrite = TRUE,
  media = TRUE,
  repeats = TRUE,
  deleted_fields = FALSE,
  pid = get_default_pid(),
  fid = get_default_fid(),
  url = get_default_url(),
  un = get_default_un(),
  pw = get_default_pw(),
  pp = get_default_pp(),
  retries = get_retries(),
  odkc_version = get_default_odkc_version(),
  verbose = get_ru_verbose()
)
```

## Arguments

- local_dir:

  The local folder to save the downloaded files to, default:
  [`here::here`](https://here.r-lib.org/reference/here.html).

- overwrite:

  Whether to overwrite previously downloaded zip files, default: FALSE

- media:

  Whether to include media attachments, default: TRUE. This feature only
  has effect on ODK Central v1.1 and higher. Setting this feature to
  FALSE with an odkc_version \< 1.1 and will display a verbose noop
  message, but still return all media attachments.

- repeats:

  Whether to include repeat data (if TRUE), or whether to return the
  root table only (FALSE). Default: TRUE. Requesting `repeats=FALSE`
  will also omit any media, and override the parameter `media`. Setting
  this feature to FALSE with an odkc_version \< 1.1 and will display a
  verbose noop message, but still include all repeat data.

- deleted_fields:

  Whether to restore all fields previously deleted from this form for
  this export (TRUE). All known fields and data for those fields will be
  merged and exported. default: FALSE

- pid:

  The numeric ID of the project, e.g.: 2.

  Default:
  [`get_default_pid`](https://docs.ropensci.org/ruODK/reference/ru_settings.md).

  Set default `pid` through `ru_setup(pid="...")`.

  See `vignette("Setup", package = "ruODK")`.

- fid:

  The alphanumeric form ID, e.g. "build_Spotlighting-0-8_1559885147".

  Default:
  [`get_default_fid`](https://docs.ropensci.org/ruODK/reference/ru_settings.md).

  Set default `fid` through `ru_setup(fid="...")`.

  See `vignette("Setup", package = "ruODK")`.

- url:

  The ODK Central base URL without trailing slash.

  Default:
  [`get_default_url`](https://docs.ropensci.org/ruODK/reference/ru_settings.md).

  Set default `url` through `ru_setup(url="...")`.

  See `vignette("Setup", package = "ruODK")`.

- un:

  The ODK Central username (an email address). Default:
  [`get_default_un`](https://docs.ropensci.org/ruODK/reference/ru_settings.md).
  Set default `un` through `ru_setup(un="...")`. See
  `vignette("Setup", package = "ruODK")`.

- pw:

  The ODK Central password. Default:
  [`get_default_pw`](https://docs.ropensci.org/ruODK/reference/ru_settings.md).
  Set default `pw` through `ru_setup(pw="...")`. See
  `vignette("Setup", package = "ruODK")`.

- pp:

  The passphrase for an encrypted form.

  Default: NULL.

  Passphrases can be stored e.g. as environment variables.

  See `vignette("Setup", package = "ruODK")`.

- retries:

  The number of attempts to retrieve a web resource.

  This parameter is given to
  [`RETRY`](https://httr.r-lib.org/reference/RETRY.html)`(times = retries)`.

  Default: 3.

- odkc_version:

  The ODK Central version as a semantic version string
  (year.minor.patch), e.g. "2023.5.1". The version is shown on ODK
  Central's version page `/version.txt`. Discard the "v". `ruODK` uses
  this parameter to adjust for breaking changes in ODK Central.

  Default:
  [`get_default_odkc_version`](https://docs.ropensci.org/ruODK/reference/ru_settings.md)
  or "2023.5.1" if unset.

  Set default `get_default_odkc_version` through
  `ru_setup(odkc_version="2023.5.1")`.

  See `vignette("Setup", package = "ruODK")`.

- verbose:

  Whether to display debug messages or not.

  Read
  [`vignette("setup", package = "ruODK")`](https://docs.ropensci.org/ruODK/articles/setup.md)
  to learn how `ruODK`'s verbosity can be set globally or per function.

## Value

The absolute path to the exported ZIP file named after the form ID. The
exported ZIP file will have the extension `.zip` unless only the root
table was requested (with `repeats=FALSE`), in which case the exported
file will have the extension `.csv`. In contrast to ODK Central, which
exports to `submissions.csv(.zip)`, the exported ZIP file is named after
the form to avoid accidentally overwriting the ZIP export from another
form.

## Details

This function exports all the Submission data associated with a Form as
one zip file containing one or more CSV files, as well as all multimedia
attachments associated with the included Submissions.

For an incremental download of a subset of submissions, use
[`submission_list`](https://docs.ropensci.org/ruODK/reference/submission_list.md)
or
[`odata_submission_get`](https://docs.ropensci.org/ruODK/reference/odata_submission_get.md)
with filter queries.

### Contents

The inclusion of subtables (from repeating form groups) can be toggled
through `repeats`, whereas the inclusion of media attachments can be
toggled through `media`.

### Download location

The file will be downloaded to the project root unless specified
otherwise (via `local_dir`). Subsequently, the zip file can be
extracted. Attachment filenames (e.g. "12345.jpg") should be prepended
with `media` (resulting in e.g. `media/12345.jpg`) in order to represent
the relative path to the actual attachment file (as extracted from the
zip file).

### Encryption

ODK Central supports two modes of encryption - learn about them
[here](https://docs.getodk.org/central-api-encryption/). `ruODK`
supports project managed encryption, however the support is limited to
exactly one encryption key. The supplied passphrase will be used against
the first returned encryption key. Remaining encryption keys are ignored
by `ruODK`.

If an incorrect passphrase is given, the request is terminated
immediately. It has been reported that multiple requests with incorrect
passphrases can crash ODK Central.

## See also

<https://docs.getodk.org/central-api-submission-management/#exporting-form-submissions-to-csv>

Other submission-management:
[`attachment_list()`](https://docs.ropensci.org/ruODK/reference/attachment_list.md),
[`encryption_key_list()`](https://docs.ropensci.org/ruODK/reference/encryption_key_list.md),
[`submission_audit_get()`](https://docs.ropensci.org/ruODK/reference/submission_audit_get.md),
[`submission_detail()`](https://docs.ropensci.org/ruODK/reference/submission_detail.md),
[`submission_get()`](https://docs.ropensci.org/ruODK/reference/submission_get.md),
[`submission_list()`](https://docs.ropensci.org/ruODK/reference/submission_list.md)

## Examples

``` r
if (FALSE) { # \dontrun{
# See vignette("setup") for setup and authentication options
# ruODK::ru_setup(svc = "....svc", un = "me@email.com", pw = "...")

se <- submission_export()

# Unzip and inspect the loot
t <- tempdir()
f <- unzip(se, exdir = t)
fs::dir_ls(t)
fid <- get_test_fid()
sub <- fs::path(t, glue::glue("{fid}.csv")) %>% readr::read_csv()
sub %>% knitr::kable(.)
} # }
```
