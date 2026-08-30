# Get submissions for a list of submission instance IDs.

Uses
[`get_one_submission`](https://docs.ropensci.org/ruODK/reference/get_one_submission.md)
on a list of submission instance IDs (`iid`) as returned from
[`submission_list`](https://docs.ropensci.org/ruODK/reference/submission_list.md)`$instance_id`.
By giving the list of `iid` to download explicitly, that list can be
modified using information not accessible to `ruODK`, e.g. `iid` can be
restricted to "only not already downloaded submissions".

## Usage

``` r
submission_get(
  iid,
  pid = get_default_pid(),
  fid = get_default_fid(),
  url = get_default_url(),
  un = get_default_un(),
  pw = get_default_pw(),
  retries = get_retries()
)
```

## Arguments

- iid:

  A list of submission instance IDs, e.g. from
  [`submission_list`](https://docs.ropensci.org/ruODK/reference/submission_list.md)`$instance_id`.

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

- retries:

  The number of attempts to retrieve a web resource.

  This parameter is given to
  [`RETRY`](https://httr.r-lib.org/reference/RETRY.html)`(times = retries)`.

  Default: 3.

## Value

A nested list of submission data.

## Details

Forms with submission audit enabled will also receive the submission
audit as `audit.csv`. This will overwrite all previous `audit.csv`
files. To get the combined submission audit logs as one single,
concatenated `audit.csv` file, use `submission_export`. Note that the
submission audit is different from the server audit. The submission
audit logs the actions of the enumerator in ODK Collect, whereas the
form audit logs the actions of the project manager in ODK Central.

## See also

<https://docs.getodk.org/central-api-submission-management/#retrieving-submission-xml>

Other submission-management:
[`attachment_list()`](https://docs.ropensci.org/ruODK/reference/attachment_list.md),
[`encryption_key_list()`](https://docs.ropensci.org/ruODK/reference/encryption_key_list.md),
[`submission_audit_get()`](https://docs.ropensci.org/ruODK/reference/submission_audit_get.md),
[`submission_detail()`](https://docs.ropensci.org/ruODK/reference/submission_detail.md),
[`submission_export()`](https://docs.ropensci.org/ruODK/reference/submission_export.md),
[`submission_list()`](https://docs.ropensci.org/ruODK/reference/submission_list.md)

## Examples

``` r
if (FALSE) { # \dontrun{
# Step 1: Setup ruODK with OData Service URL (has url, pid, fid)
ruODK::ru_setup(svc = "...")

# Step 2: List all submissions of form
sl <- submission_list()

# Step 3: Get submissions
subs <- submission_get(sl$instance_id)
} # }
```
