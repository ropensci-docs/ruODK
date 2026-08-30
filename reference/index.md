# Package index

## OData API

Top-level functions to retrieve and parse data via the OData API. These
functions alone are enough to retrieve all submissions with their nested
tables and attachments and parse their datatypes. See
[`vignette("odata-api")`](https://docs.ropensci.org/ruODK/articles/odata-api.md)
for a walkthrough.

- [`odata_metadata_get()`](https://docs.ropensci.org/ruODK/reference/odata_metadata_get.md)
  **\[stable\]** : Retrieve metadata from an OData URL ending in .svc as
  list of lists.
- [`odata_service_get()`](https://docs.ropensci.org/ruODK/reference/odata_service_get.md)
  **\[stable\]** : Retrieve service metadata from an OData URL ending in
  .svc as tibble.
- [`odata_submission_get()`](https://docs.ropensci.org/ruODK/reference/odata_submission_get.md)
  **\[stable\]** : Retrieve and rectangle form submissions, parse dates,
  geopoints, download and link attachments.

## Projects

Functions to manage projects.

- [`project_create()`](https://docs.ropensci.org/ruODK/reference/project_create.md)
  **\[experimental\]** : Create a new project.
- [`project_detail()`](https://docs.ropensci.org/ruODK/reference/project_detail.md)
  : List all details of one project.
- [`project_list()`](https://docs.ropensci.org/ruODK/reference/project_list.md)
  : List all projects.

## Entities

An Entity List is a named collection of Entities that have the same
properties. In the ODK Central API and in the related ODK XForms
specification, collections of Entities are referred to as Datasets. The
term “Entity List” is used for this concept in the Central frontend UI,
user documentation, and all other text intended for end users who are
not developers. Accordingly, ruODK uses the term “entitylist\_” for
Entity Lists.

- [`entity_audits()`](https://docs.ropensci.org/ruODK/reference/entity_audits.md)
  **\[maturing\]** : Return server audit logs of one Entity.
- [`entity_changes()`](https://docs.ropensci.org/ruODK/reference/entity_changes.md)
  **\[maturing\]** : List changes to one Entity.
- [`entity_create()`](https://docs.ropensci.org/ruODK/reference/entity_create.md)
  **\[experimental\]** : Creates exactly one Entity in the Dataset.
- [`entity_delete()`](https://docs.ropensci.org/ruODK/reference/entity_delete.md)
  **\[maturing\]** : Delete one Entity.
- [`entity_detail()`](https://docs.ropensci.org/ruODK/reference/entity_detail.md)
  **\[maturing\]** : Show metadata and current data of one Entity.
- [`entity_list()`](https://docs.ropensci.org/ruODK/reference/entity_list.md)
  **\[maturing\]** : List all Entities of a kind.
- [`entity_update()`](https://docs.ropensci.org/ruODK/reference/entity_update.md)
  **\[experimental\]** : Update one Entity.
- [`entity_versions()`](https://docs.ropensci.org/ruODK/reference/entity_versions.md)
  **\[maturing\]** : List versions of one Entity.
- [`entitylist_detail()`](https://docs.ropensci.org/ruODK/reference/entitylist_detail.md)
  **\[maturing\]** : Show Entity List details.
- [`entitylist_download()`](https://docs.ropensci.org/ruODK/reference/entitylist_download.md)
  **\[maturing\]** : Download an Entity List as CSV.
- [`entitylist_list()`](https://docs.ropensci.org/ruODK/reference/entitylist_list.md)
  **\[maturing\]** : List all Entity Lists of one Project.
- [`entitylist_update()`](https://docs.ropensci.org/ruODK/reference/entitylist_update.md)
  **\[maturing\]** : Update Entity List details.
- [`odata_entitylist_data_get()`](https://docs.ropensci.org/ruODK/reference/odata_entitylist_data_get.md)
  **\[experimental\]** : Get the Data Document from the OData Dataset
  Service.
- [`odata_entitylist_metadata_get()`](https://docs.ropensci.org/ruODK/reference/odata_entitylist_metadata_get.md)
  **\[experimental\]** : Get the Metadata Document from the OData
  Dataset Service.
- [`odata_entitylist_service_get()`](https://docs.ropensci.org/ruODK/reference/odata_entitylist_service_get.md)
  **\[experimental\]** : Get the Service Document from the OData Dataset
  Service.

## Forms

Functions to manage forms. Once their implementation is completed, these
functions can be used to manage the life cycle of forms from drafts to
published forms, their retirement, form permissions, as well as form
attachments.

- [`form_detail()`](https://docs.ropensci.org/ruODK/reference/form_detail.md)
  **\[stable\]** : Show details for one form.
- [`form_list()`](https://docs.ropensci.org/ruODK/reference/form_list.md)
  **\[stable\]** : List all forms.
- [`form_schema()`](https://docs.ropensci.org/ruODK/reference/form_schema.md)
  **\[stable\]** : Show the schema of one form.
- [`form_schema_ext()`](https://docs.ropensci.org/ruODK/reference/form_schema_ext.md)
  **\[experimental\]** : Show the extended schema of one form.
- [`form_xml()`](https://docs.ropensci.org/ruODK/reference/form_xml.md)
  **\[stable\]** : Show the XML representation of one form as list.

## Submissions

Functions to manage submissions and their attachments. This family of
functions provides an alternative way to the OData family. Specifically,
submissions include nested tables in each record. See
[`vignette("restful-api")`](https://docs.ropensci.org/ruODK/articles/restful-api.md)
for a walkthrough.

- [`attachment_list()`](https://docs.ropensci.org/ruODK/reference/attachment_list.md)
  : List all attachments for a list of submission instances.
- [`encryption_key_list()`](https://docs.ropensci.org/ruODK/reference/encryption_key_list.md)
  **\[maturing\]** : List all encryption keys for a form.
- [`submission_audit_get()`](https://docs.ropensci.org/ruODK/reference/submission_audit_get.md)
  **\[experimental\]** : Get submission audits for a list of submission
  instance IDs.
- [`submission_detail()`](https://docs.ropensci.org/ruODK/reference/submission_detail.md)
  **\[stable\]** : Show metadata for one submission.
- [`submission_export()`](https://docs.ropensci.org/ruODK/reference/submission_export.md)
  **\[maturing\]** : Export all form submissions including repeats and
  attachments to CSV.
- [`submission_get()`](https://docs.ropensci.org/ruODK/reference/submission_get.md)
  : Get submissions for a list of submission instance IDs.
- [`submission_list()`](https://docs.ropensci.org/ruODK/reference/submission_list.md)
  **\[stable\]** : List all submissions of one form.

## Users

Functions to operate on users, roles, and their permissions.

- [`user_list()`](https://docs.ropensci.org/ruODK/reference/user_list.md)
  **\[maturing\]** : List all users.

## Server

Functions related to server management.

- [`audit_get()`](https://docs.ropensci.org/ruODK/reference/audit_get.md)
  **\[stable\]** : Get server audit log entries.

## Utilities

Functions to assist with retrieval and parsing of submissions and their
attachments. These functions are used from within top-level functions.
The typical workflow does not call these explicitly.

- [`attachment_get()`](https://docs.ropensci.org/ruODK/reference/attachment_get.md)
  **\[stable\]** : Download attachments and return the local path.

- [`attachment_link()`](https://docs.ropensci.org/ruODK/reference/attachment_link.md)
  **\[stable\]** : Prefix attachment columns from CSV export with a
  local attachment file path.

- [`drop_null_coords()`](https://docs.ropensci.org/ruODK/reference/drop_null_coords.md)
  : Drop any NULL coordinates from a GeoJSON geometry.

- [`form_schema_parse()`](https://docs.ropensci.org/ruODK/reference/form_schema_parse.md)
  **\[stable\]** : Parse a form_schema into a tibble of fields with
  name, type, and path.

- [`get_one_attachment()`](https://docs.ropensci.org/ruODK/reference/get_one_attachment.md)
  **\[stable\]** : Download one media attachment.

- [`get_one_submission()`](https://docs.ropensci.org/ruODK/reference/get_one_submission.md)
  : Download one submission.

- [`get_one_submission_att_list()`](https://docs.ropensci.org/ruODK/reference/get_one_submission_att_list.md)
  **\[stable\]** : List all attachments of one submission.

- [`get_one_submission_audit()`](https://docs.ropensci.org/ruODK/reference/get_one_submission_audit.md)
  **\[experimental\]** : Download server audit logs for one submission.

- [`handle_ru_attachments()`](https://docs.ropensci.org/ruODK/reference/handle_ru_attachments.md)
  **\[stable\]** : Download and link submission attachments according to
  a form schema.

- [`handle_ru_datetimes()`](https://docs.ropensci.org/ruODK/reference/handle_ru_datetimes.md)
  **\[stable\]** : Parse datetimes of submission data according to a
  form schema.

- [`handle_ru_geopoints()`](https://docs.ropensci.org/ruODK/reference/handle_ru_geopoints.md)
  **\[stable\]** : Split all geopoints of a submission tibble into their
  components.

- [`handle_ru_geoshapes()`](https://docs.ropensci.org/ruODK/reference/handle_ru_geoshapes.md)
  **\[stable\]** : Split all geoshapes of a submission tibble into their
  components.

- [`handle_ru_geotraces()`](https://docs.ropensci.org/ruODK/reference/handle_ru_geotraces.md)
  **\[stable\]** : Split all geotraces of a submission tibble into their
  components.

- [`odata_submission_rectangle()`](https://docs.ropensci.org/ruODK/reference/odata_submission_rectangle.md)
  **\[stable\]** :

  Rectangle the output of `odata_submission_get(parse=FALSE)` into a
  tidy tibble and unnest all levels.

- [`split_geopoint()`](https://docs.ropensci.org/ruODK/reference/split_geopoint.md)
  **\[stable\]** : Annotate a dataframe containing a geopoint column
  with lon, lat, alt.

- [`split_geoshape()`](https://docs.ropensci.org/ruODK/reference/split_geoshape.md)
  **\[stable\]** : Annotate a dataframe containing a geoshape column
  with lon, lat, alt of the geotrace's first point.

- [`split_geotrace()`](https://docs.ropensci.org/ruODK/reference/split_geotrace.md)
  **\[stable\]** : Annotate a dataframe containing a geotrace column
  with lon, lat, alt of the geotrace's first point.

## Messaging

Custom handlers for messages, warnings, and errors.

- [`ru_msg_abort()`](https://docs.ropensci.org/ruODK/reference/ru_msg_abort.md)
  **\[stable\]** : rlang::abort() with a red error message with a cross
  symbol.
- [`ru_msg_info()`](https://docs.ropensci.org/ruODK/reference/ru_msg_info.md)
  **\[stable\]** : Print a blue info message with an info symbol.
- [`ru_msg_noop()`](https://docs.ropensci.org/ruODK/reference/ru_msg_noop.md)
  **\[stable\]** : Print a green noop message with a filled circle
  symbol.
- [`ru_msg_success()`](https://docs.ropensci.org/ruODK/reference/ru_msg_success.md)
  **\[stable\]** : Print a green success message with a tick symbol.
- [`ru_msg_warn()`](https://docs.ropensci.org/ruODK/reference/ru_msg_warn.md)
  **\[stable\]** : rlang::warn() with a yellow warning message with a
  warning symbol.

## Settings

Functions to manage ruODK settings.

- [`odata_svc_parse()`](https://docs.ropensci.org/ruODK/reference/odata_svc_parse.md)
  **\[stable\]** : Retrieve URL, project ID, and form ID from an ODK
  Central OData service URL.

- [`parse_odkc_version()`](https://docs.ropensci.org/ruODK/reference/parse_odkc_version.md)
  **\[stable\]** :

  Parse a given ODK Central version string or number into a `semver`.

- [`ru_settings()`](https://docs.ropensci.org/ruODK/reference/ru_settings.md)
  [`get_default_pid()`](https://docs.ropensci.org/ruODK/reference/ru_settings.md)
  [`get_default_fid()`](https://docs.ropensci.org/ruODK/reference/ru_settings.md)
  [`get_default_url()`](https://docs.ropensci.org/ruODK/reference/ru_settings.md)
  [`get_default_un()`](https://docs.ropensci.org/ruODK/reference/ru_settings.md)
  [`get_default_pw()`](https://docs.ropensci.org/ruODK/reference/ru_settings.md)
  [`get_default_pp()`](https://docs.ropensci.org/ruODK/reference/ru_settings.md)
  [`get_default_tz()`](https://docs.ropensci.org/ruODK/reference/ru_settings.md)
  [`get_default_orders()`](https://docs.ropensci.org/ruODK/reference/ru_settings.md)
  [`get_test_url()`](https://docs.ropensci.org/ruODK/reference/ru_settings.md)
  [`get_test_un()`](https://docs.ropensci.org/ruODK/reference/ru_settings.md)
  [`get_test_pw()`](https://docs.ropensci.org/ruODK/reference/ru_settings.md)
  [`get_test_pid()`](https://docs.ropensci.org/ruODK/reference/ru_settings.md)
  [`get_test_fid()`](https://docs.ropensci.org/ruODK/reference/ru_settings.md)
  [`get_test_fid_zip()`](https://docs.ropensci.org/ruODK/reference/ru_settings.md)
  [`get_test_fid_att()`](https://docs.ropensci.org/ruODK/reference/ru_settings.md)
  [`get_test_fid_gap()`](https://docs.ropensci.org/ruODK/reference/ru_settings.md)
  [`get_test_fid_wkt()`](https://docs.ropensci.org/ruODK/reference/ru_settings.md)
  [`get_test_pp()`](https://docs.ropensci.org/ruODK/reference/ru_settings.md)
  [`get_ru_verbose()`](https://docs.ropensci.org/ruODK/reference/ru_settings.md)
  [`get_default_odkc_version()`](https://docs.ropensci.org/ruODK/reference/ru_settings.md)
  [`get_test_odkc_version()`](https://docs.ropensci.org/ruODK/reference/ru_settings.md)
  [`get_retries()`](https://docs.ropensci.org/ruODK/reference/ru_settings.md)
  **\[stable\]** :

  Get or set `ruODK` settings.

- [`ru_setup()`](https://docs.ropensci.org/ruODK/reference/ru_setup.md)
  :

  Configure default `ruODK` settings.

- [`semver_gt()`](https://docs.ropensci.org/ruODK/reference/semver_gt.md)
  : Show whether a given semver is greater than a baseline version.

- [`semver_lt()`](https://docs.ropensci.org/ruODK/reference/semver_lt.md)
  : Show whether a given semver is lesser than a baseline version.

## Example data

Datasets included in ruODK, used in unit tests, code examples and
vignettes.

- [`fq_attachments`](https://docs.ropensci.org/ruODK/reference/fq_attachments.md)
  **\[stable\]** : A tibble of submission attachments.
- [`fq_data`](https://docs.ropensci.org/ruODK/reference/fq_data.md)
  **\[stable\]** : Parsed submission data for an ODK Central form.
- [`fq_data_strata`](https://docs.ropensci.org/ruODK/reference/fq_data_strata.md)
  **\[stable\]** : Parsed submission data for a subgroup of an ODK
  Central form.
- [`fq_data_taxa`](https://docs.ropensci.org/ruODK/reference/fq_data_taxa.md)
  **\[stable\]** : Parsed submission data for a subgroup of an ODK
  Central form.
- [`fq_form_detail`](https://docs.ropensci.org/ruODK/reference/fq_form_detail.md)
  **\[stable\]** : A tibble of form metadata.
- [`fq_form_list`](https://docs.ropensci.org/ruODK/reference/fq_form_list.md)
  **\[stable\]** : A tibble of forms.
- [`fq_form_schema`](https://docs.ropensci.org/ruODK/reference/fq_form_schema.md)
  **\[stable\]** : JSON form schema for an ODK Central form.
- [`fq_form_xml`](https://docs.ropensci.org/ruODK/reference/fq_form_xml.md)
  **\[stable\]** : A nested list of a form definition.
- [`fq_meta`](https://docs.ropensci.org/ruODK/reference/fq_meta.md)
  **\[stable\]** : OData metadata document for an ODK Central form.
- [`fq_project_detail`](https://docs.ropensci.org/ruODK/reference/fq_project_detail.md)
  **\[stable\]** : A tibble of project metadata.
- [`fq_project_list`](https://docs.ropensci.org/ruODK/reference/fq_project_list.md)
  **\[stable\]** : A tibble of project metadata.
- [`fq_raw`](https://docs.ropensci.org/ruODK/reference/fq_raw.md)
  **\[stable\]** : OData submission data for an ODK Central form.
- [`fq_raw_strata`](https://docs.ropensci.org/ruODK/reference/fq_raw_strata.md)
  **\[stable\]** : OData submission data for a subgroup of an ODK
  Central form.
- [`fq_raw_taxa`](https://docs.ropensci.org/ruODK/reference/fq_raw_taxa.md)
  **\[stable\]** : OData submission data for a subgroup of an ODK
  Central form.
- [`fq_submission_list`](https://docs.ropensci.org/ruODK/reference/fq_submission_list.md)
  **\[stable\]** : A tibble of submission metadata.
- [`fq_submissions`](https://docs.ropensci.org/ruODK/reference/fq_submissions.md)
  **\[stable\]** : A nested list of submission data.
- [`fq_svc`](https://docs.ropensci.org/ruODK/reference/fq_svc.md)
  **\[stable\]** : OData service document for an ODK Central form.
- [`fq_zip_data`](https://docs.ropensci.org/ruODK/reference/fq_zip_data.md)
  **\[stable\]** : A tibble of the main data table of records from a
  test form.
- [`fq_zip_strata`](https://docs.ropensci.org/ruODK/reference/fq_zip_strata.md)
  **\[stable\]** : A tibble of a repeated sub-group of records from a
  test form.
- [`fq_zip_taxa`](https://docs.ropensci.org/ruODK/reference/fq_zip_taxa.md)
  **\[stable\]** : A tibble of a repeated sub-group of records from a
  test form.
- [`fs_v7`](https://docs.ropensci.org/ruODK/reference/fs_v7.md)
  **\[stable\]** : The parsed XML form_schema of a form from ODK Central
  v0.6.
- [`fs_v7_raw`](https://docs.ropensci.org/ruODK/reference/fs_v7_raw.md)
  **\[stable\]** : The unparsed XML form_schema of a form from ODK
  Central v0.6 as nested list.
- [`geo_fs`](https://docs.ropensci.org/ruODK/reference/geo_fs.md)
  **\[stable\]** : The form_schema of a form containing geofields in
  GeoJSON.
- [`geo_gj`](https://docs.ropensci.org/ruODK/reference/geo_gj.md)
  **\[stable\]** : The parsed submissions of a form containing geofields
  in GeoJSON.
- [`geo_gj88`](https://docs.ropensci.org/ruODK/reference/geo_gj88.md)
  **\[stable\]** : The parsed submissions of a form containing geofields
  in GeoJSON with trailing empty coordinates present.
- [`geo_gj_raw`](https://docs.ropensci.org/ruODK/reference/geo_gj_raw.md)
  **\[stable\]** : The unparsed submissions of a form containing
  geofields in GeoJSON.
- [`geo_wkt`](https://docs.ropensci.org/ruODK/reference/geo_wkt.md)
  **\[stable\]** : The parsed submissions of a form containing geofields
  in WKT.
- [`geo_wkt88`](https://docs.ropensci.org/ruODK/reference/geo_wkt88.md)
  **\[stable\]** : The parsed submissions of a form containing geofields
  in WKT with trailing empty coordinates present.
- [`geo_wkt_raw`](https://docs.ropensci.org/ruODK/reference/geo_wkt_raw.md)
  **\[stable\]** : The unparsed submissions of a form containing
  geofields in WKT.
