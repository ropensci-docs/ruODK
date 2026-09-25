# JSON form schema for an ODK Central form.

**\[stable\]**

## Usage

``` r
fq_form_schema
```

## Format

The output of
[`ruODK::form_schema()`](https://docs.ropensci.org/ruODK/reference/form_schema.md),
a tibble with columns "type", "name" and "path" and one row per form
field.

## Source

See `system.file("extdata", "FloraQuadrat04.xml", package = "ruODK")`
and
[`ruODK::form_schema()`](https://docs.ropensci.org/ruODK/reference/form_schema.md).

## Details

The parsed form schema of an ODK Central form.

This data is kept up to date with the data used in vignettes and package
tests. The data is comprised of test records with nonsensical data. The
forms used to capture this data are development versions of real-world
forms.

This data is used to build vignettes offline and without the need for
credentials to an ODK Central server. The test suite ensures that the
"canned" data is identical to the "live" data.

## See also

Other included:
[`fq_attachments`](https://docs.ropensci.org/ruODK/reference/fq_attachments.md),
[`fq_data`](https://docs.ropensci.org/ruODK/reference/fq_data.md),
[`fq_data_strata`](https://docs.ropensci.org/ruODK/reference/fq_data_strata.md),
[`fq_data_taxa`](https://docs.ropensci.org/ruODK/reference/fq_data_taxa.md),
[`fq_form_detail`](https://docs.ropensci.org/ruODK/reference/fq_form_detail.md),
[`fq_form_list`](https://docs.ropensci.org/ruODK/reference/fq_form_list.md),
[`fq_form_xml`](https://docs.ropensci.org/ruODK/reference/fq_form_xml.md),
[`fq_meta`](https://docs.ropensci.org/ruODK/reference/fq_meta.md),
[`fq_project_detail`](https://docs.ropensci.org/ruODK/reference/fq_project_detail.md),
[`fq_project_list`](https://docs.ropensci.org/ruODK/reference/fq_project_list.md),
[`fq_raw`](https://docs.ropensci.org/ruODK/reference/fq_raw.md),
[`fq_raw_strata`](https://docs.ropensci.org/ruODK/reference/fq_raw_strata.md),
[`fq_raw_taxa`](https://docs.ropensci.org/ruODK/reference/fq_raw_taxa.md),
[`fq_submission_list`](https://docs.ropensci.org/ruODK/reference/fq_submission_list.md),
[`fq_submissions`](https://docs.ropensci.org/ruODK/reference/fq_submissions.md),
[`fq_svc`](https://docs.ropensci.org/ruODK/reference/fq_svc.md),
[`fq_zip_data`](https://docs.ropensci.org/ruODK/reference/fq_zip_data.md),
[`fq_zip_strata`](https://docs.ropensci.org/ruODK/reference/fq_zip_strata.md),
[`fq_zip_taxa`](https://docs.ropensci.org/ruODK/reference/fq_zip_taxa.md),
[`fs_v7`](https://docs.ropensci.org/ruODK/reference/fs_v7.md),
[`fs_v7_raw`](https://docs.ropensci.org/ruODK/reference/fs_v7_raw.md),
[`geo_fs`](https://docs.ropensci.org/ruODK/reference/geo_fs.md),
[`geo_gj`](https://docs.ropensci.org/ruODK/reference/geo_gj.md),
[`geo_gj88`](https://docs.ropensci.org/ruODK/reference/geo_gj88.md),
[`geo_gj_raw`](https://docs.ropensci.org/ruODK/reference/geo_gj_raw.md),
[`geo_wkt`](https://docs.ropensci.org/ruODK/reference/geo_wkt.md),
[`geo_wkt88`](https://docs.ropensci.org/ruODK/reference/geo_wkt88.md),
[`geo_wkt_raw`](https://docs.ropensci.org/ruODK/reference/geo_wkt_raw.md)
