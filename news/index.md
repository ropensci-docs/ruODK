# Changelog

## ruODK 1.5.2

### Minor changes

- `get_one_attachment` now follows redirects, enabling
  `odata_submission_get` to download attachments stored in AWS S3
  buckets ([\#167](https://github.com/ropensci/ruODK/issues/167), thanks
  [@baanbapat](https://github.com/baanbapat)).
- `odata_submission_get` now supports `names_sep` and `clean_names`.
  `odata_submission_get(names_setp="__", clean_names=FALSE)` will
  separate group names by a double underscore.
  `odata_submission_get(names_setp=NULL)` will omit group names unless
  the group is a repeat, in which case the group name is still prefixed
  to avoid duplicate column names in the resulting tibble
  ([\#168](https://github.com/ropensci/ruODK/issues/168), thanks [Nina
  Brooks](https://forum.getodk.org/u/Nina_Brooks1) and [Guenther
  Fink](https://forum.getodk.org/u/Guenther_Fink))

### Maintenance

- Update tested ODK Central version to 2025.2.2 (Sept 2025) and adjust
  tests to expect fields added to the ODK Central API (`entity_list`,
  `form_list`, `submission_list`).
- Refresh all packaged example data to contain the added fields.

## ruODK 1.5.1

### Major changes

- Add support for the OData API endpoints for Entities
  ([\#152](https://github.com/ropensci/ruODK/issues/152))
- Bump minimum versions of dependencies

### Minor changes

- `entity_changes` now returns a tibble instead of nested list.
- `submission_export` gains a new parameter `deleted_fields` to export
  all known fields of a form, including fields that were deleted in the
  latest form version.
  ([\#129](https://github.com/ropensci/ruODK/issues/129),
  [\#161](https://github.com/ropensci/ruODK/issues/161))

## ruODK 1.5.0

### Major changes

- Support Entities and Entity Lists (Datasets)
  ([\#152](https://github.com/ropensci/ruODK/issues/152))
- Add pre-commit hooks and precommit.ci integration
- Add devcontainer

## ruODK 1.4.2

This release migrates the `ruODK` test suite to a new test server
`ruodk.getodk.cloud` which was generously sponsored by GetODK.

This release makes `ruODK` aware of the new ODK Central semantic version
format: Update your ODK Central version in `.Renviron` or in the
credential helper of your choice to the new format
`ODKC_VERSION="2023.5.1"` (with your current version). See the updated
vignette “setup”.

### Major changes

- Handle the new ODK Central semantic versioning
  ([\#150](https://github.com/ropensci/ruODK/issues/150))
- Migrate to new test server
  ([\#149](https://github.com/ropensci/ruODK/issues/149))

## ruODK 1.4.0

This release fixes a few compatibility issues and bumps dependencies to
R (4.1) and imported/suggested packages. Upgrade carefully and revert to
1.3.12 if things go awry.

- Update to new `tidyselect` syntax: Using vectors of names to select
  makes `tidyselect` complain (WARN, soon ERROR). We wrap all
  programmatic selections of variable names in
  [`dplyr::all_of()`](https://tidyselect.r-lib.org/reference/all_of.html)
  where we expect a single variable to be selected, and
  [`dplyr::any_of()`](https://tidyselect.r-lib.org/reference/all_of.html)
  where we select using fuzzy matching
  (e.g. [`dplyr::starts_with()`](https://tidyselect.r-lib.org/reference/starts_with.html)).
  ([\#146](https://github.com/ropensci/ruODK/issues/146))
- Make
  [`ruODK::form_list()`](https://docs.ropensci.org/ruODK/reference/form_list.md)
  robust against `reviewState` missing from outdated Central versions.
  ([\#145](https://github.com/ropensci/ruODK/issues/145), HT
  [@dpagendam](https://github.com/dpagendam) and
  [\#143](https://github.com/ropensci/ruODK/issues/143), HT
  [@collinschwantes](https://github.com/collinschwantes)) There will be
  more such tripwires - please do submit a bug report if you find a
  discrepancy between Central API and ruODK’s parsing.

## ruODK 1.3.12

## ruODK 1.3.11

- Update `project_list`, `submission_list` and \`\` columns to reflect
  Central 1.5 API output.
- Update `submission_list` columns to reflect Central 1.5 API output.

## ruODK 1.3.10

## ruODK 1.3.9

## ruODK 1.3.8

## ruODK 1.3.7

### Minor fixes

- Improve issue template for bug reports
- Upgrade test server to ODK Central 1.4.2
- Refresh packaged data (new Central brings new fields), update tests
- Improve GitHub Action for Docker build

## `ruODK` 1.3.6

### Minor fixes

- `odata_submission_get` supports parameter `expand` to expand all
  repeat repetitions.

## `ruODK` 1.3.5

### Minor fixes

- `split_geopoint` is now robust against all NULL columns.
  `split_geotrace` and `split_geoshape` are possibly affected. \## Data
- Packaged data has been re-created to represent the latest server
  outputs. \## Maintenance
- New Suggest depencency `terra` (through `mapview`)

## `ruODK` 1.3.0

This release supports ODK Central 1.3.0 and represents an over-due
version bump to reflect the supported ODK Central version. The test
server is now updated to ODK Central 1.3.0, and all tests pass.

There are still some newer and as yet unsupported API endpoints in ODK
Central, which serve administrative purposes of the front-end.
Contributions are welcome, get started on [these
issues](https://github.com/ropensci/ruODK/milestone/2) and the
contributing guide. As ruODK focuses on data retrieval, these
administrative endpoints are non-critical to ruODK’s purpose.

### Major fixes

### Minor fixes

### Documentation

### Data

- Packaged data has been re-created to represent the latest server
  outputs. \## Maintenance
- All tests pass, GitHub Actions is as per usual brittle at the
  installation step.

## `ruODK` 1.2.0.0000

We are shaping up to a release targetting the ODK Central 1.2 release.
ODK Central is undergoing some bug fixes and patches, while ruODK’s test
server will be migrated to another instance. The latter is required to
enable tests which create/update/delete entities in ODK Central.

### Major fixes

### Minor fixes

### Documentation

### Data

### Maintenance

- All DEPENDS and SUGGESTS bumped to latest available under R release.
- The minimum supported version is `rversions::r_oldrel()`: 4.0.5
  (2021-03-31).
- ruODK is developed under `rversions::r_release()`: 4.1.1 (2021-08-10).

## `ruODK` 1.2.0

### Major fixes

- ODK Central returns Geoshapes as Multipolygon. `split_geoshape`
  adjusted for `odkce_version` \>= 1.2.
  ([\#131](https://github.com/ropensci/ruODK/issues/131))
- [`readr::parse_datetime`](https://readr.tidyverse.org/reference/parse_datetime.html)
  stopped supporting timezone “Z”.
  ([\#130](https://github.com/ropensci/ruODK/issues/130)) \## Minor
  fixes \## Documentation \## Data
- All data refreshed from test server running ODK Central 1.2. \##
  Maintenance

## `ruODK` 0.10.2

### Major fixes

### Minor fixes

### Documentation

- Update installation instructions with source install from rOpenSci
  R-Universe and troubleshooting
  ([\#128](https://github.com/ropensci/ruODK/issues/128), thanks
  [@yanokwa](https://github.com/yanokwa)) \## Data \## Maintenance

## `ruODK` 0.10.2

### Major fixes

- Fix ODK Central v1.2 time out on NULL query parameters `skip` and
  `top`. ruODK now only supplies non-NULL query parameters and has an
  additional seat-belt to drop any query parameter that is an empty
  string. ([\#126](https://github.com/ropensci/ruODK/issues/126), thanks
  [@yanokwa](https://github.com/yanokwa),
  [@mtyszler](https://github.com/mtyszler),
  [@thaliehln](https://github.com/thaliehln)) \## Minor fixes \##
  Documentation \## Data \## Maintenance

## `ruODK` 0.10.1

### Major fixes

- `submission_export` now terminates immediately if an incorrect
  passphrase is given. ODK Central can exceed memory limits if
  `submission_export` is run repeatedly with an incorrect passphrase.
  ([\#30](https://github.com/ropensci/ruODK/issues/30), thanks
  [@Thaliehln](https://github.com/Thaliehln)) \## Minor fixes
- Add `encryption_key_list` \## Documentation \## Data \## Maintenance

## `ruODK` 0.10.0

### Major fixes

### Minor fixes

- Make `ru_msg_*` conditional to
  [`get_ru_verbose()`](https://docs.ropensci.org/ruODK/reference/ru_settings.md).
  \## Documentation
- Reference re-ordered into topics.
- Re-worded the example preamble on setup.
- Added metadata to pkgdown config.
- Enable Markdown docs. Embedded lifecycle badges should work. R CMD
  Check does not complain which is nice. \## Data \## Maintenance
- Prepare to cover remaining API endpoints.

## `ruODK` 0.9.11

### Major fixes

### Minor fixes

- Add `published_at` to `form_list` and `form_detail`, update examples,
  tests, test fixtures to show that draft forms can be detected by a NA
  `published_at` in ODK Central versions having form drafts, and by NA
  `hash` and `version` in ODK Central versions before form drafts. \##
  Documentation \## Data \## Maintenance

## `ruODK` 0.9.10

This is a “everything so far works” release. There are a few ODK Central
API endpoints waiting to be implemented still.

### Major fixes

### Minor fixes

- Default ODK Central version bumped to current release (1.1) \##
  Documentation
- PDF manual updated
- Welcoming new contributors Marcelo
  ([@mtyszler](https://github.com/mtyszler)) and Hélène
  ([@Thaliehln](https://github.com/Thaliehln)) \## Data \## Maintenance
- Updated Zenodo archive at <https://zenodo.org/record/4609910>
- Updated Docker image at <https://hub.docker.com/u/dbcawa/ruodk>
  (RStudio server with ruODK)

## `ruODK` 0.9.9

### Major fixes

- `submission_export` now supports ODK Central v1.1 features to omit
  media attachments (`media = FALSE`), and to omit repeat data
  (`include_repeats=FALSE`). Calling `submission_export` on an older
  version of ODK Central (as determined through
  [`get_default_odkc_version()`](https://docs.ropensci.org/ruODK/reference/ru_settings.md))
  with these new parameters will emit a (verbose only) “noop” message
  and not act further on them. \## Minor fixes
- Bugfix to `submission_export` on encrypted forms with multiple
  encryption keys. (Thanks [@Thaliehln](https://github.com/Thaliehln)
  [\#117](https://github.com/ropensci/ruODK/issues/117)
  [\#30](https://github.com/ropensci/ruODK/issues/30))

## `ruODK` 0.9.8

### Minor fixes

- Add support for passphrase to the `ru_setup` family
  ([\#116](https://github.com/ropensci/ruODK/issues/116))

## `ruODK` 0.9.7

### Major fixes

- [`odata_submission_get()`](https://docs.ropensci.org/ruODK/reference/odata_submission_get.md)
  bugfix:
  [`handle_ru_attachments()`](https://docs.ropensci.org/ruODK/reference/handle_ru_attachments.md)
  now finds and downloads media attachments from both main submissions
  and nested form groups.
  ([\#114](https://github.com/ropensci/ruODK/issues/114))
- [`odata_submission_get()`](https://docs.ropensci.org/ruODK/reference/odata_submission_get.md)
  bugfix: missing media attachments (due to upload error from ODK
  Collect to ODK Central) are tolerated without interrupting the batch
  download. A diagnostic warning message will be emitted for each failed
  download. ([\#114](https://github.com/ropensci/ruODK/issues/114)) \##
  Minor fixes \## Documentation \## Data \## Maintenance

## `ruODK` 0.9.6

### Major fixes

- Support encryption
  ([\#30](https://github.com/ropensci/ruODK/issues/30)
  [\#110](https://github.com/ropensci/ruODK/issues/110),
  [@Thaliehln](https://github.com/Thaliehln)).
  - Note that `ruODK` only supports one passphrase. When switching
    between multiple encrypted forms, it would make sense to store the
    different passphrases in separate environment variables, and refer
    to these environment variables explicitly in function calls.
  - The updated ruODK::submission_export should now export data from
    both encrypted projects and non-encrypted projects. The HTTP method
    is changed from GET to POST and encryption key ID / passphrase are
    provided via POST body using a JSON format. Encrypted forms can be
    extracted and inspected like non-encrypted forms:

`{r, eval=FALSE} se <- submission_export() t <- tempdir() f <- unzip(se, exdir = t) fs::dir_ls(t) fid <- get_test_fid() sub <- fs::path(t, glue::glue("Locations.csv")) %>% readr::read_csv() sub %>% knitr::kable(.)`

## `ruODK` 0.9.5

### Major fixes

- `form_schema_ext` retrieves choice lists when choice filters are
  present ([\#105](https://github.com/ropensci/ruODK/issues/105),
  [@mtyszler](https://github.com/mtyszler)). \## Minor fixes \##
  Documentation \## Data \## Maintenance

## `ruODK` 0.9.4

### Major fixes

- `form_schema_ext` performance enhancement
  ([\#106](https://github.com/ropensci/ruODK/issues/106), thanks
  [@mtyszler](https://github.com/mtyszler)). \## Maintenance
- Tests use vcr to cache server response
  ([\#104](https://github.com/ropensci/ruODK/issues/104)). Delete the
  local cache `tests/fixtures` to re-generate the vcr cache, or enjoy
  much faster running tests using cached server response.

## `ruODK` 0.9.3

This is a point release to create a new RStudio Server image. \## Minor
fixes \* Form schema now also works on draft forms
([\#103](https://github.com/ropensci/ruODK/issues/103), HT
[@dmenne](https://github.com/dmenne)). \## Maintenance \* Automated code
reviews by \<codefactor.io\>. \* GitHub Actions welcomes Ubuntu 20.04
LTS and MacOS X back to the passing environments.

## `ruODK` 0.9.2

### Major fixes

- [`form_schema_ext()`](https://docs.ropensci.org/ruODK/reference/form_schema_ext.md)
  Shows the extended schema of one form, including (multi-language)
  labels and choice lists.
  ([\#77](https://github.com/ropensci/ruODK/issues/77), thanks
  [@mtyszler](https://github.com/mtyszler) for the PR)
- Development continues in the default branch `main`. \## Minor fixes
- `form_list` now handles draft forms with `NA` hash and version
  ([\#86](https://github.com/ropensci/ruODK/issues/86), thanks
  [@dmenne](https://github.com/dmenne) for the PR).
- Migrate package tests to a new ODK Central instance and update
  contributing guidelines with new settings.
  ([\#14](https://github.com/ropensci/ruODK/issues/14))
- Drop Import of `tidyselect` in favour of using
  [`dplyr::all_of()`](https://tidyselect.r-lib.org/reference/all_of.html).
- All calls to `httr::RETRY(times=)` are configurable via setting
  `retries`. ([\#94](https://github.com/ropensci/ruODK/issues/94)) \##
  Documentation
- Mapview popups in vignette “Spatial” are back after an upstream bugfix
  is in progress (<https://github.com/r-spatial/mapview/issues/312>).

## `ruODK` 0.9.1

### Major fixes

ODK Central versions 0.7 to 0.9 export geotraces and geoshapes via OData
with a trailing empty coordinate. `ruODK` removes any trailing empty
coordinates from both GeoJSON and WKT formats.
([\#88](https://github.com/ropensci/ruODK/issues/88), HT
[@TimonWeitkamp](https://github.com/TimonWeitkamp) for the bug report)

### Documentation

A new vignette “Spatial” demonstrates how to parse spatial data into
native formats, such as `sf`, and gives pointers on what to do next with
them.

## `ruODK` 0.9.0

This is the release on passing [rOpenSci peer
review](https://github.com/ropensci/software-review/issues/335).

Thanks to the rOpenSci editors and reviewers
[@maelle](https://github.com/maelle),
[@karissawhiting](https://github.com/karissawhiting) and
[@jmt2080ad](https://github.com/jmt2080ad), as well as to
[@OdiljonQurbon](https://github.com/OdiljonQurbon),
[@dickoa](https://github.com/dickoa),
[@arestrom](https://github.com/arestrom) and
[@dmenne](https://github.com/dmenne).

A DOI was minted at <https://doi.org/10.5281/zenodo.3953159>.

## `ruODK` 0.6.6

This version addresses ROpenSci reviewer comments from
[@karissawhiting](https://github.com/karissawhiting) and
[@jmt2080ad](https://github.com/jmt2080ad), contributions from
[@dickoa](https://github.com/dickoa), as well as ideas and suggestions
from [@OdiljonQurbon](https://github.com/OdiljonQurbon),
[@arestrom](https://github.com/arestrom) and
[@dmenne](https://github.com/dmenne).

This version supports ODK Central 0.9 while providing backwards
compatibility for ODK Central \<= 0.7.

### Major fixes

- New environment variables `ODKC_(TEST_)VERSION` allow `ruODK` to
  toggle between deprecated/removed and new/added API endpoints,
  e.g. `form_schema`.
  ([\#61](https://github.com/ropensci/ruODK/issues/61))
- Split and rename WKT POINT (ODK geopoint) fields with
  `odata_submission_get(wkt=T)`.
  ([\#31](https://github.com/ropensci/ruODK/issues/31)
  [\#7](https://github.com/ropensci/ruODK/issues/7) HT
  [@OdiljonQurbon](https://github.com/OdiljonQurbon))
- `submission_get` now accepts a vector of (all or selected) submission
  instance IDs (`iid`), similar to
  [`odata_submission_get()`](https://docs.ropensci.org/ruODK/reference/odata_submission_get.md).
  ([\#38](https://github.com/ropensci/ruODK/issues/38))
- All [`httr::GET()`](https://httr.r-lib.org/reference/GET.html) are now
  replaced with `httr::RETRY("GET", ...)`
  ([\#48](https://github.com/ropensci/ruODK/issues/48))
- Refactor `odata_submission_parse()` into
  [`odata_submission_rectangle()`](https://docs.ropensci.org/ruODK/reference/odata_submission_rectangle.md),
  `handle_ru_{geopoints, geotraces, geoshapes, datetimes, attachments}`.
  ([\#54](https://github.com/ropensci/ruODK/issues/54)
  [\#69](https://github.com/ropensci/ruODK/issues/69))
- Maintain backwards compatibility to ODK Central v7 for changed spatial
  output for geotrace and geoshape
  ([\#70](https://github.com/ropensci/ruODK/issues/70))

### Minor fixes

- Drop `. <- NULL` in favour of `utils::globalVariables(".")`.
  ([\#35](https://github.com/ropensci/ruODK/issues/35))
- Print settings now hides passwords but instructs how to show them.
  ([\#37](https://github.com/ropensci/ruODK/issues/37))
- [`ru_setup()`](https://docs.ropensci.org/ruODK/reference/ru_setup.md)
  now prints settings.
  ([\#37](https://github.com/ropensci/ruODK/issues/37))
- `parse_datetime()` renamed to `ru_datetime()` to avoid naming conflict
  with
  [`readr::parse_datetime()`](https://readr.tidyverse.org/reference/parse_datetime.html).
  ([\#43](https://github.com/ropensci/ruODK/issues/43))
- Add a global default for verbosity.
  ([\#51](https://github.com/ropensci/ruODK/issues/51) HT
  [@arestrom](https://github.com/arestrom))
- Add a global default for time zone.
  ([\#53](https://github.com/ropensci/ruODK/issues/53) HT
  [@arestrom](https://github.com/arestrom))
- Use
  [`httr::modify_url`](https://httr.r-lib.org/reference/modify_url.html)
  to build URLs rather than
  [`glue::glue`](https://glue.tidyverse.org/reference/glue.html)
  ([\#66](https://github.com/ropensci/ruODK/issues/66))
- Silenced spurious messages from
  [`tibble::as_tibble()`](https://tibble.tidyverse.org/reference/as_tibble.html)
  which is called from
  [`odata_submission_rectangle()`](https://docs.ropensci.org/ruODK/reference/odata_submission_rectangle.md).
  Use `ru_verbose` to toggle useful diagnostic messages.
  ([\#79](https://github.com/ropensci/ruODK/issues/79) HT
  [@dmenne](https://github.com/dmenne))
- Renamed `master` branch to `main`, updated docs (HT
  [@arestrom](https://github.com/arestrom)
  [\#81](https://github.com/ropensci/ruODK/issues/81))

### Dependencies

- Moved `rlist` to Imports, as it is now used in
  [`odata_submission_get()`](https://docs.ropensci.org/ruODK/reference/odata_submission_get.md).
  ([\#6](https://github.com/ropensci/ruODK/issues/6))
- Dropped `rlist` dependency in favour of `tidyr`/`dplyr`.
  ([\#85](https://github.com/ropensci/ruODK/issues/85))
- Use development versions of `rlang`, `purrr` and `lifecycle` to get
  their latest bug fixes.

### Data

- Use canned data in all vignettes, so they can build without
  authentication. ([\#33](https://github.com/ropensci/ruODK/issues/33))
- Update canned data (and `make-data.R`) to work with CI-built pkgdown
  site. ([\#52](https://github.com/ropensci/ruODK/issues/52))
- Remove nested list `form_schema_raw` which is only generated from
  legacy ODK Central (\< 0.8)
  ([\#61](https://github.com/ropensci/ruODK/issues/61))
- Added ODK Central \< v0.7 form schema for tests.

### Documentation

- Updated workshop companion package
  [urODK](https://github.com/dbca-wa/urODK).
- Rename vignettes to `odata-api` and `restful-api`.
  ([\#34](https://github.com/ropensci/ruODK/issues/34))
- Warn against using plain text credentials in vignette `setup`.
  ([\#34](https://github.com/ropensci/ruODK/issues/34))
- More documentation improvements at
  [\#34](https://github.com/ropensci/ruODK/issues/34).
- Add screencast to the README. HT to asciicast!
  ([\#45](https://github.com/ropensci/ruODK/issues/45))
- Improve logo - more turtles, but questionable photoshopping.
- Add examples where missing.
  ([\#32](https://github.com/ropensci/ruODK/issues/32))
- Build pkgdown site via GH actions.
  ([\#52](https://github.com/ropensci/ruODK/issues/52))
- Minor typographic changes: end every function title with a full stop.
- Broken links and other inconsistencies fixed after contributions from
  the ODK Forum, [@dickoa](https://github.com/dickoa),
  [@arestrom](https://github.com/arestrom),
  [@dmenne](https://github.com/dmenne). Thanks for the first community
  feedback! ([\#76](https://github.com/ropensci/ruODK/issues/76)
  [\#74](https://github.com/ropensci/ruODK/issues/74)
  [\#79](https://github.com/ropensci/ruODK/issues/79)
  [\#80](https://github.com/ropensci/ruODK/issues/80)
  [\#81](https://github.com/ropensci/ruODK/issues/81))

### Docker

- Added Dockerfile to build an RStudio Server image based on
  `rocker/geospatial` with `ruODK` and dependencies installed.
- Build a separate Dockerfile for
  [`urODK`](https://github.com/dbca-wa/urODK) to launch a hosted RStudio
  instance in Binderhub.
  ([\#83](https://github.com/ropensci/ruODK/issues/83))

## `ruODK` 0.6.6

- The big one has landed:
  [`odata_submission_get()`](https://docs.ropensci.org/ruODK/reference/odata_submission_get.md)
  now defaults to parse submissions from nested lists into a tibble,
  parse dates and datetimes, download and link attachments.
  ([\#6](https://github.com/ropensci/ruODK/issues/6))

## `ruODK` 0.6.5

### Documentation

- Use lifecycle badges on functions. Add lifecycle to dependencies,
  version bump `usethis`.
  ([\#29](https://github.com/ropensci/ruODK/issues/29))

### Code

- Refactor list wrangling code to use `map_*(.default=NA)`, removing
  some internal helpers (thanks to
  [@jennybc](https://github.com/jennybc))
- Use dummy imports to silence R CMD check NOTES as per
  [googledrive](https://github.com/tidyverse/googledrive/blob/050a982cba630503702bdde05a77d727baa36d48/R/googledrive-package.R)’s
  example (thanks to [@jennybc](https://github.com/jennybc))
- Drop unused internal helper functions

## `ruODK` 0.6.4

### Data

- Use three new test forms to make package smaller and tests faster. Use
  the main test form for example data, including data from two nested
  tables. Use the main test form in all vignettes and README. Use a
  small form without attachments for tests repeatedly exporting to ZIP.
  Use another small form with only one submission and two attachments
  for tests downloading attachments. The test credentials are unchanged
  ([\#23](https://github.com/ropensci/ruODK/issues/23))

## `ruODK` 0.6.3

### Dependencies

- [tidyr 1.0.0](https://www.tidyverse.org/articles/2019/09/tidyr-1-0-0/)
  is out! Move [tidyr](https://tidyr.tidyverse.org) dependency from
  GitHub master to CRAN version
  ([\#27](https://github.com/ropensci/ruODK/issues/27))
- Add [usethis](https://usethis.r-lib.org) to Suggests, it is used in
  the setup step

### Documentation

- Add [David Henry](https://github.com/schemetrica)’s [Pentaho Kettle
  tutorial](https://forum.opendatakit.org/t/automating-data-delivery-using-the-odata-endpoint-in-odk-central/22010)
  to the software review in the README
  ([\#28](https://github.com/ropensci/ruODK/issues/28))

### DIY for workshops

- Add inaugural RMarkdown template “odata”
  ([\#26](https://github.com/ropensci/ruODK/issues/26))
- Add [binder](https://mybinder.org/) launch button (one click start for
  [\#26](https://github.com/ropensci/ruODK/issues/26))

## `ruODK` 0.6.2

### Code

- Simplifiy
  [`ru_setup()`](https://docs.ropensci.org/ruODK/reference/ru_setup.md)
  to use OData Service URL.
- Change all functions to default to `get_default{pid,fid,url,un,pw}()`,
  partly moving project ID (pid) and form ID (fid) to kwargs. This
  changes all examples, tests, vignettes, READMEs.
- Reduce installed package size by sharing attachment files. Add new
  parameter `separate=FALSE` to `attachment_get` to prevent separating
  attachment files into subfolders named after their submission `uuid`
  ([\#22](https://github.com/ropensci/ruODK/issues/22))

### Documentation

- Add a high level overview diagram to README and `inst/joss/paper.md`
  to illustrate `ruODK`’s intended purpose in the ODK ecosystem
  ([\#19](https://github.com/ropensci/ruODK/issues/19))
- Added link to explain [environment variables and R
  startup](https://whattheyforgot.org/r-startup.html) to vignette
  “setup”. [@maelle](https://github.com/maelle)
- Add comparison of similar software to README
  ([\#25](https://github.com/ropensci/ruODK/issues/25))

## `ruODK` 0.6.1

- ROpenSci submission review
  [milestone](https://github.com/ropensci/ruODK/milestone/3),
  [discussion](https://github.com/ropensci/software-review/issues/335).
- Updates to documentation
  ([\#13](https://github.com/ropensci/ruODK/issues/13)
  [\#15](https://github.com/ropensci/ruODK/issues/15)
  [\#17](https://github.com/ropensci/ruODK/issues/17))
- Group function docs
  ([\#18](https://github.com/ropensci/ruODK/issues/18))
- Update contribution guidelines and add account request issue template:
  How to run `ruODK` tests and build the vignettes
  ([\#15](https://github.com/ropensci/ruODK/issues/15)
  [\#20](https://github.com/ropensci/ruODK/issues/20))
- Add dedicated
  [`ru_setup()`](https://docs.ropensci.org/ruODK/reference/ru_setup.md)
  and
  [`ru_settings()`](https://docs.ropensci.org/ruODK/reference/ru_settings.md).
  Pat down functions for missing credentials and yell loudly but clearly
  about httr errors.
  ([\#16](https://github.com/ropensci/ruODK/issues/16))
- Drop `@importFrom` to reduce duplication. All external functions are
  prefixed with their package name already.
- Add convenience helpers
  [`attachment_link()`](https://docs.ropensci.org/ruODK/reference/attachment_link.md)
  and `parse_datetime()`.
- Use
  [`janitor::clean_names()`](https://sfirke.github.io/janitor/reference/clean_names.html)
  on column names over home-grown helpers.
- Since `submission_detail` is now metadata only, add `submission_get`
  to download submission data.

## `ruODK` 0.6.0

- Version bump and lifecycle bump to indicate that `ruODK` is ready to
  be used against ODK Central 0.6.

## `ruODK` 0.6.0.9000

- Version bump to match ODK Central’s version.
- Updated to match ODK Central’s API at 0.6 (RESTful and OData) (c.f.).
- Add commented out crosslinks to source code and related tests for
  convenience.
- Encryption endpoints (new in 0.6) are not yet supported.
- Audit logs supported, as they are a read-only export.

## `ruODK` 0.3.1

### Preparation for ROpenSci pre-submission

- Check name with
  [`available::available("ruODK")`](https://devguide.ropensci.org/building.html#naming-your-package):
- Name valid: ✔
- Available on CRAN: ✔
- Available on Bioconductor: ✔
- Available on GitHub: ✔
- Rude misinterpretations: none
- In summary: Package name seems to be OK. Well, ODK. OK, ruODK.
- Added metadata via
  [`codemetar::write_codemeta("ruODK")`](https://devguide.ropensci.org/building.html#creating-metadata-for-your-package).
- [Cross-platform](https://devguide.ropensci.org/building.html#platforms):
  Runs on GNU/Linux (TravisCI) and on Windows (AppVeyor)
- [Function
  naming](https://devguide.ropensci.org/building.html#function-and-argument-naming)
  follows `object_verb`.
- `ruODK` uses verb singulars (e.g. `submission_list` to list multiple
  submissions), while ODK Central’s API URLs use verb plurals.
- `ruODK` uses `snake_case`.
- Exception to `object_verb`: Functions operating on the OData endpoints
  are named `odata_object_verb`. Helper functions not related to API
  endpoints are named `verb_object`.
- [Code style](https://devguide.ropensci.org/building.html#code-style)
  done by `styler::style_package()`, see section “Release” in
  `README.md`.
- `ruODK` [has a
  `README.Rmd`](https://devguide.ropensci.org/building.html#readme) and
  has a [website generated by
  `pkgdown`](https://devguide.ropensci.org/building.html#website).
- `ruODK` has documentation [generated by
  `roxygen2`](https://devguide.ropensci.org/building.html#documentation).
- [Test coverage](https://devguide.ropensci.org/building.html#testing)
  100%, but could use more edge cases.
- Tests use a live ODK Central instance, which is kept up to date by
  ODK. This means that ruODK’s test always run against the latest master
  of ODK Central. `ruODK` does not (but maybe should?) use `webmockr`
  and `vcr`.
- Spellchecks with `spelling::spell_check_package()`: added technical
  terms and function names to `inst/WORDLIST`.
- Added citation and section in `README`.
- Added `inst/joss/paper.md` for submission to JOSS.
- Added [examples](https://devguide.ropensci.org/building.html#examples)
  to function docs.

### TODO

- Implement remaining missing functions
  ([ticket](https://github.com/ropensci/ruODK/issues/9)).

## `ruODK` 0.3.0

- Use tidyverse issue template
- Follow `goodpractice`
- Created vignette “Setup”
- Add AppVeyor
- Refactor storage path of attachments to not contain “uuid:” (for
  Windows compat)
- Started on REST API: `project_list`, `project_detail`, `form_list`,
  `form_detail`. Naming scheme is `object_verb`.
- For now, functions related to the OData endpoint are named
  `verb_object`, maybe we should rename them to `odata_object_verb`.
- Refactor URLs - build from project and form IDs

## `ruODK` 0.2.4

- Cleaned up logo, thanks to
  [@issa-tseng](https://github.com/issa-tseng) for suggestions

## `ruODK` 0.2.3

- Added a new form, Flora Quadrat 0.3 to inst/extdata.

## `ruODK` 0.2.2

- Added more test coverage.

## `ruODK` 0.2.1

- Added various `usethis` goodies, test stubs, badges.

## `ruODK` 0.2.0

- Recursively unnests raw data into wide format. Manual post-processing
  is still required to rename (anonymous in ODK and auto-named
  through R) coordinates, and to handle attachments.

## `ruODK` 0.1.0

- Parses metadata, submissions, and handles attachments (retaining
  already downloaded attachments).
- Includes example forms as both `.xml` and `.odbbuild` in
  `inst/extdata`.
- Includes example data as retrieved from ODK Central.
- Includes vignette demonstrating tidying of retrieved data.
- Handles repeating groups.

Roadmap:

- Handle paginated submissions.
- Retain already downloaded submissions.
