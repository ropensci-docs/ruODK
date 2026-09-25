# Enable Project Managed Encryption.

**\[experimental\]**

## Usage

``` r
project_enable_encryption(
  pid = get_default_pid(),
  passphrase,
  hint = NULL,
  url = get_default_url(),
  un = get_default_un(),
  pw = get_default_pw(),
  retries = get_retries(),
  odkc_version = get_default_odkc_version()
)
```

## Arguments

- pid:

  The numeric ID of the project, e.g.: 2.

  Default:
  [`get_default_pid`](https://docs.ropensci.org/ruODK/reference/ru_settings.md).

  Set default `pid` through `ru_setup(pid="...")`.

  See `vignette("Setup", package = "ruODK")`.

- passphrase:

  (character) The encryption passphrase. If this passphrase is lost, the
  data will be irrecoverable.

- hint:

  (character) A reminder about the passphrase. This is primarily useful
  when multiple encryption keys and passphrases are being used, to tell
  them apart. Default: `NULL` (no hint).

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

## Value

A list with a single element `success` (`TRUE`) as per the ODK Central
API docs.

## Details

Project Managed Encryption can be enabled via the API. To do this, POST
with the passphrase and optionally a reminder hint about the passphrase.
If managed encryption is already enabled, a 409 error response will be
returned. Enabling managed encryption will modify all unencrypted Forms
in the Project, and as a result the version of all Forms within the
Project will also be modified. It is therefore best to enable managed
encryption before devices are in the field. Any Forms in the Project
that already have self-supplied encryption keys will be left alone. This
endpoint requires ODK Central v0.6 or later.

## See also

<https://docs.getodk.org/central-api-project-management/#enabling-project-managed-encryption>

Other project-management:
[`form_assignment_role_list()`](https://docs.ropensci.org/ruODK/reference/form_assignment_role_list.md),
[`project_assignment_actors()`](https://docs.ropensci.org/ruODK/reference/project_assignment_actors.md),
[`project_assignment_grant()`](https://docs.ropensci.org/ruODK/reference/project_assignment_grant.md),
[`project_assignment_revoke()`](https://docs.ropensci.org/ruODK/reference/project_assignment_revoke.md),
[`project_create()`](https://docs.ropensci.org/ruODK/reference/project_create.md),
[`project_delete()`](https://docs.ropensci.org/ruODK/reference/project_delete.md),
[`project_detail()`](https://docs.ropensci.org/ruODK/reference/project_detail.md),
[`project_list()`](https://docs.ropensci.org/ruODK/reference/project_list.md),
[`project_replace()`](https://docs.ropensci.org/ruODK/reference/project_replace.md),
[`project_update()`](https://docs.ropensci.org/ruODK/reference/project_update.md)

## Examples

``` r
if (FALSE) { # \dontrun{
# See vignette("setup") for setup and authentication options
# ruODK::ru_setup(svc = "....svc", un = "me@email.com", pw = "...")

p <- project_create(name = "Encrypted Project")

project_enable_encryption(
  pid = p$id,
  passphrase = "super duper secret",
  hint = "it was a secret"
)
# > $success
# > [1] TRUE
} # }
```
