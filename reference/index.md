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

- [`form_assignment_role_list()`](https://docs.ropensci.org/ruODK/reference/form_assignment_role_list.md)
  **\[experimental\]** : List Role-specific Form Assignments within a
  Project.
- [`project_assignment_actors()`](https://docs.ropensci.org/ruODK/reference/project_assignment_actors.md)
  **\[experimental\]** : List all Actors assigned some Project Role.
- [`project_assignment_grant()`](https://docs.ropensci.org/ruODK/reference/project_assignment_grant.md)
  **\[experimental\]** : Assign an Actor to a Project Role.
- [`project_assignment_revoke()`](https://docs.ropensci.org/ruODK/reference/project_assignment_revoke.md)
  **\[experimental\]** : Revoke a Project Role Assignment from an Actor.
- [`project_create()`](https://docs.ropensci.org/ruODK/reference/project_create.md)
  **\[experimental\]** : Create a new project.
- [`project_delete()`](https://docs.ropensci.org/ruODK/reference/project_delete.md)
  **\[experimental\]** : Delete a Project.
- [`project_detail()`](https://docs.ropensci.org/ruODK/reference/project_detail.md)
  : List all details of one project.
- [`project_enable_encryption()`](https://docs.ropensci.org/ruODK/reference/project_enable_encryption.md)
  **\[experimental\]** : Enable Project Managed Encryption.
- [`project_list()`](https://docs.ropensci.org/ruODK/reference/project_list.md)
  : List all projects.
- [`project_replace()`](https://docs.ropensci.org/ruODK/reference/project_replace.md)
  **\[experimental\]** : Replace a Project.
- [`project_update()`](https://docs.ropensci.org/ruODK/reference/project_update.md)
  **\[experimental\]** : Modify a Project.

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
- [`entity_bulk_delete()`](https://docs.ropensci.org/ruODK/reference/entity_bulk_delete.md)
  **\[experimental\]** : Delete multiple Entities at once.
- [`entity_bulk_restore()`](https://docs.ropensci.org/ruODK/reference/entity_bulk_restore.md)
  **\[experimental\]** : Restore multiple deleted Entities at once.
- [`entity_changes()`](https://docs.ropensci.org/ruODK/reference/entity_changes.md)
  **\[maturing\]** : List changes to one Entity.
- [`entity_create()`](https://docs.ropensci.org/ruODK/reference/entity_create.md)
  **\[experimental\]** : Creates exactly one Entity in the Dataset.
- [`entity_creators()`](https://docs.ropensci.org/ruODK/reference/entity_creators.md)
  **\[experimental\]** : List all creators of Entities in one Entity
  List.
- [`entity_delete()`](https://docs.ropensci.org/ruODK/reference/entity_delete.md)
  **\[maturing\]** : Delete one Entity.
- [`entity_detail()`](https://docs.ropensci.org/ruODK/reference/entity_detail.md)
  **\[maturing\]** : Show metadata and current data of one Entity.
- [`entity_geodata()`](https://docs.ropensci.org/ruODK/reference/entity_geodata.md)
  **\[experimental\]** : Get Entity geodata as GeoJSON.
- [`entity_geojson()`](https://docs.ropensci.org/ruODK/reference/entity_geojson.md)
  **\[experimental\]** : Get the GeoJSON of one Entity.
- [`entity_list()`](https://docs.ropensci.org/ruODK/reference/entity_list.md)
  **\[maturing\]** : List all Entities of a kind.
- [`entity_restore()`](https://docs.ropensci.org/ruODK/reference/entity_restore.md)
  **\[experimental\]** : Restore a deleted Entity.
- [`entity_update()`](https://docs.ropensci.org/ruODK/reference/entity_update.md)
  **\[experimental\]** : Update one Entity.
- [`entity_versions()`](https://docs.ropensci.org/ruODK/reference/entity_versions.md)
  **\[maturing\]** : List versions of one Entity.
- [`entitylist_create()`](https://docs.ropensci.org/ruODK/reference/entitylist_create.md)
  **\[experimental\]** : Create an Entity List.
- [`entitylist_delete()`](https://docs.ropensci.org/ruODK/reference/entitylist_delete.md)
  **\[experimental\]** : Delete an Entity List.
- [`entitylist_detail()`](https://docs.ropensci.org/ruODK/reference/entitylist_detail.md)
  **\[maturing\]** : Show Entity List details.
- [`entitylist_download()`](https://docs.ropensci.org/ruODK/reference/entitylist_download.md)
  **\[maturing\]** : Download an Entity List as CSV.
- [`entitylist_list()`](https://docs.ropensci.org/ruODK/reference/entitylist_list.md)
  **\[maturing\]** : List all Entity Lists of one Project.
- [`entitylist_property_create()`](https://docs.ropensci.org/ruODK/reference/entitylist_property_create.md)
  **\[experimental\]** : Add a property to an Entity List.
- [`entitylist_property_delete()`](https://docs.ropensci.org/ruODK/reference/entitylist_property_delete.md)
  **\[experimental\]** : Delete a property from an Entity List.
- [`entitylist_trash_download()`](https://docs.ropensci.org/ruODK/reference/entitylist_trash_download.md)
  **\[experimental\]** : Download Entities of a deleted Entity List.
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

- [`form_assignment_actors()`](https://docs.ropensci.org/ruODK/reference/form_assignment_actors.md)
  **\[experimental\]** : List all Actors assigned some Form Role.
- [`form_assignment_grant()`](https://docs.ropensci.org/ruODK/reference/form_assignment_grant.md)
  **\[experimental\]** : Assign an Actor to a Form Role.
- [`form_assignment_revoke()`](https://docs.ropensci.org/ruODK/reference/form_assignment_revoke.md)
  **\[experimental\]** : Revoke a Form Role Assignment from an Actor.
- [`form_attachment_download()`](https://docs.ropensci.org/ruODK/reference/form_attachment_download.md)
  **\[experimental\]** : Download one Form attachment.
- [`form_attachment_list()`](https://docs.ropensci.org/ruODK/reference/form_attachment_list.md)
  **\[experimental\]** : List all attachments of one Form.
- [`form_create()`](https://docs.ropensci.org/ruODK/reference/form_create.md)
  **\[experimental\]** : Create a new Form.
- [`form_dataset_diff()`](https://docs.ropensci.org/ruODK/reference/form_dataset_diff.md)
  **\[experimental\]** : Show Datasets affected by one Form.
- [`form_delete()`](https://docs.ropensci.org/ruODK/reference/form_delete.md)
  **\[experimental\]** : Delete a Form.
- [`form_detail()`](https://docs.ropensci.org/ruODK/reference/form_detail.md)
  **\[stable\]** : Show details for one form.
- [`form_draft_attachment_delete()`](https://docs.ropensci.org/ruODK/reference/form_draft_attachment_delete.md)
  **\[experimental\]** : Clear a Draft Form attachment.
- [`form_draft_attachment_download()`](https://docs.ropensci.org/ruODK/reference/form_draft_attachment_download.md)
  **\[experimental\]** : Download one Draft Form attachment.
- [`form_draft_attachment_link()`](https://docs.ropensci.org/ruODK/reference/form_draft_attachment_link.md)
  **\[experimental\]** : Link a Dataset to a Draft Form attachment.
- [`form_draft_attachment_list()`](https://docs.ropensci.org/ruODK/reference/form_draft_attachment_list.md)
  **\[experimental\]** : List all expected attachments of a Draft Form.
- [`form_draft_attachment_upload()`](https://docs.ropensci.org/ruODK/reference/form_draft_attachment_upload.md)
  **\[experimental\]** : Upload a Draft Form attachment.
- [`form_draft_create()`](https://docs.ropensci.org/ruODK/reference/form_draft_create.md)
  **\[experimental\]** : Create a Draft Form.
- [`form_draft_dataset_diff()`](https://docs.ropensci.org/ruODK/reference/form_draft_dataset_diff.md)
  **\[experimental\]** : Show Dataset changes of a Draft Form.
- [`form_draft_delete()`](https://docs.ropensci.org/ruODK/reference/form_draft_delete.md)
  **\[experimental\]** : Delete a Draft Form.
- [`form_draft_detail()`](https://docs.ropensci.org/ruODK/reference/form_draft_detail.md)
  **\[experimental\]** : Show details of a Draft Form.
- [`form_draft_publish()`](https://docs.ropensci.org/ruODK/reference/form_draft_publish.md)
  **\[experimental\]** : Publish a Draft Form.
- [`form_draft_xlsx()`](https://docs.ropensci.org/ruODK/reference/form_draft_xlsx.md)
  **\[experimental\]** : Download the XLSForm of a Draft Form.
- [`form_draft_xml()`](https://docs.ropensci.org/ruODK/reference/form_draft_xml.md)
  **\[experimental\]** : Show the XML of a Draft Form.
- [`form_link()`](https://docs.ropensci.org/ruODK/reference/form_link.md)
  **\[experimental\]** : Show Form details by Form Link ID.
- [`form_list()`](https://docs.ropensci.org/ruODK/reference/form_list.md)
  **\[stable\]** : List all forms.
- [`form_restore()`](https://docs.ropensci.org/ruODK/reference/form_restore.md)
  **\[experimental\]** : Restore a deleted Form.
- [`form_schema()`](https://docs.ropensci.org/ruODK/reference/form_schema.md)
  **\[stable\]** : Show the schema of one form.
- [`form_schema_ext()`](https://docs.ropensci.org/ruODK/reference/form_schema_ext.md)
  **\[experimental\]** : Show the extended schema of one form.
- [`form_update()`](https://docs.ropensci.org/ruODK/reference/form_update.md)
  **\[experimental\]** : Modify a Form's state.
- [`form_version_attachment_download()`](https://docs.ropensci.org/ruODK/reference/form_version_attachment_download.md)
  **\[experimental\]** : Download one attachment of a published Form
  version.
- [`form_version_attachment_list()`](https://docs.ropensci.org/ruODK/reference/form_version_attachment_list.md)
  **\[experimental\]** : List expected attachments of one published Form
  version.
- [`form_version_detail()`](https://docs.ropensci.org/ruODK/reference/form_version_detail.md)
  **\[experimental\]** : Show details of one published Form version.
- [`form_version_list()`](https://docs.ropensci.org/ruODK/reference/form_version_list.md)
  **\[experimental\]** : List all published versions of one Form.
- [`form_version_xlsx()`](https://docs.ropensci.org/ruODK/reference/form_version_xlsx.md)
  **\[experimental\]** : Download the XLSForm of one published Form
  version.
- [`form_version_xml()`](https://docs.ropensci.org/ruODK/reference/form_version_xml.md)
  **\[experimental\]** : Show the XML of one published Form version.
- [`form_xlsx()`](https://docs.ropensci.org/ruODK/reference/form_xlsx.md)
  **\[experimental\]** : Download the XLSForm of one Form.
- [`form_xml()`](https://docs.ropensci.org/ruODK/reference/form_xml.md)
  **\[stable\]** : Show the XML representation of one form as list.
- [`public_link_create()`](https://docs.ropensci.org/ruODK/reference/public_link_create.md)
  **\[experimental\]** : Create a Public Access Link for one Form.
- [`public_link_delete()`](https://docs.ropensci.org/ruODK/reference/public_link_delete.md)
  **\[experimental\]** : Delete a Public Access Link.
- [`public_link_detail()`](https://docs.ropensci.org/ruODK/reference/public_link_detail.md)
  **\[experimental\]** : Show details of one Public Access Link.
- [`public_link_list()`](https://docs.ropensci.org/ruODK/reference/public_link_list.md)
  **\[experimental\]** : List all Public Access Links of one Form.
- [`public_link_update()`](https://docs.ropensci.org/ruODK/reference/public_link_update.md)
  **\[experimental\]** : Set Actor Property values on a Public Access
  Link.

## Submissions

Functions to manage submissions and their attachments. This family of
functions provides an alternative way to the OData family. Specifically,
submissions include nested tables in each record. See
[`vignette("restful-api")`](https://docs.ropensci.org/ruODK/articles/restful-api.md)
for a walkthrough.

- [`attachment_delete()`](https://docs.ropensci.org/ruODK/reference/attachment_delete.md)
  **\[experimental\]** : Clear a Submission attachment.
- [`attachment_list()`](https://docs.ropensci.org/ruODK/reference/attachment_list.md)
  : List all attachments for a list of submission instances.
- [`attachment_upload()`](https://docs.ropensci.org/ruODK/reference/attachment_upload.md)
  **\[experimental\]** : Upload a Submission attachment.
- [`encryption_key_list()`](https://docs.ropensci.org/ruODK/reference/encryption_key_list.md)
  **\[maturing\]** : List all encryption keys for a form.
- [`submission_audit_get()`](https://docs.ropensci.org/ruODK/reference/submission_audit_get.md)
  **\[experimental\]** : Get submission audits for a list of submission
  instance IDs.
- [`submission_changes()`](https://docs.ropensci.org/ruODK/reference/submission_changes.md)
  **\[experimental\]** : Show changes between versions of one
  Submission.
- [`submission_comment_create()`](https://docs.ropensci.org/ruODK/reference/submission_comment_create.md)
  **\[experimental\]** : Post a comment to one Submission.
- [`submission_comment_list()`](https://docs.ropensci.org/ruODK/reference/submission_comment_list.md)
  **\[experimental\]** : List all comments of one Submission.
- [`submission_create()`](https://docs.ropensci.org/ruODK/reference/submission_create.md)
  **\[experimental\]** : Create a Submission.
- [`submission_csv()`](https://docs.ropensci.org/ruODK/reference/submission_csv.md)
  **\[experimental\]** : Export the root Submission table to CSV.
- [`submission_delete()`](https://docs.ropensci.org/ruODK/reference/submission_delete.md)
  **\[experimental\]** : Delete a Submission.
- [`submission_detail()`](https://docs.ropensci.org/ruODK/reference/submission_detail.md)
  **\[stable\]** : Show metadata for one submission.
- [`submission_draft_attachment_delete()`](https://docs.ropensci.org/ruODK/reference/submission_draft_attachment_delete.md)
  **\[experimental\]** : Clear an attachment of a Draft Submission.
- [`submission_draft_attachment_download()`](https://docs.ropensci.org/ruODK/reference/submission_draft_attachment_download.md)
  **\[experimental\]** : Download one attachment of a Draft Submission.
- [`submission_draft_attachment_list()`](https://docs.ropensci.org/ruODK/reference/submission_draft_attachment_list.md)
  **\[experimental\]** : List expected attachments of one Draft
  Submission.
- [`submission_draft_attachment_upload()`](https://docs.ropensci.org/ruODK/reference/submission_draft_attachment_upload.md)
  **\[experimental\]** : Upload an attachment of a Draft Submission.
- [`submission_draft_create()`](https://docs.ropensci.org/ruODK/reference/submission_draft_create.md)
  **\[experimental\]** : Create a Submission on a Draft Form.
- [`submission_draft_export()`](https://docs.ropensci.org/ruODK/reference/submission_draft_export.md)
  **\[experimental\]** : Export Draft Submissions to CSV.
- [`submission_draft_get()`](https://docs.ropensci.org/ruODK/reference/submission_draft_get.md)
  **\[experimental\]** : Download one Draft Submission.
- [`submission_draft_keys()`](https://docs.ropensci.org/ruODK/reference/submission_draft_keys.md)
  **\[experimental\]** : List encryption keys of Draft Submissions.
- [`submission_draft_list()`](https://docs.ropensci.org/ruODK/reference/submission_draft_list.md)
  **\[experimental\]** : List all Submissions of a Draft Form.
- [`submission_edit()`](https://docs.ropensci.org/ruODK/reference/submission_edit.md)
  **\[experimental\]** : Edit one Submission field and leave a comment.
- [`submission_export()`](https://docs.ropensci.org/ruODK/reference/submission_export.md)
  **\[maturing\]** : Export all form submissions including repeats and
  attachments to CSV.
- [`submission_geodata()`](https://docs.ropensci.org/ruODK/reference/submission_geodata.md)
  **\[experimental\]** : Get Submissions geodata as GeoJSON.
- [`submission_geojson()`](https://docs.ropensci.org/ruODK/reference/submission_geojson.md)
  **\[experimental\]** : Get the GeoJSON of one Submission.
- [`submission_get()`](https://docs.ropensci.org/ruODK/reference/submission_get.md)
  : Get submissions for a list of submission instance IDs.
- [`submission_list()`](https://docs.ropensci.org/ruODK/reference/submission_list.md)
  **\[stable\]** : List all submissions of one form.
- [`submission_restore()`](https://docs.ropensci.org/ruODK/reference/submission_restore.md)
  **\[experimental\]** : Restore a deleted Submission.
- [`submission_review()`](https://docs.ropensci.org/ruODK/reference/submission_review.md)
  **\[experimental\]** : Review a Submission.
- [`submission_submitters()`](https://docs.ropensci.org/ruODK/reference/submission_submitters.md)
  **\[experimental\]** : List all submitting Actors of one Form.
- [`submission_update()`](https://docs.ropensci.org/ruODK/reference/submission_update.md)
  **\[experimental\]** : Update Submission data.
- [`submission_version_attachment_delete()`](https://docs.ropensci.org/ruODK/reference/submission_version_attachment_delete.md)
  **\[experimental\]** : Clear one attachment of a Submission version.
- [`submission_version_attachment_download()`](https://docs.ropensci.org/ruODK/reference/submission_version_attachment_download.md)
  **\[experimental\]** : Download one attachment of a Submission
  version.
- [`submission_version_attachment_list()`](https://docs.ropensci.org/ruODK/reference/submission_version_attachment_list.md)
  **\[experimental\]** : List expected attachments of one Submission
  version.
- [`submission_version_detail()`](https://docs.ropensci.org/ruODK/reference/submission_version_detail.md)
  **\[experimental\]** : Show details of one Submission version.
- [`submission_version_geojson()`](https://docs.ropensci.org/ruODK/reference/submission_version_geojson.md)
  **\[experimental\]** : Get the GeoJSON of one Submission version.
- [`submission_version_xml()`](https://docs.ropensci.org/ruODK/reference/submission_version_xml.md)
  **\[experimental\]** : Show the XML of one Submission version.
- [`submission_versions()`](https://docs.ropensci.org/ruODK/reference/submission_versions.md)
  **\[experimental\]** : List all versions of one Submission.

## Users

Functions to operate on users, roles, and their permissions.

- [`app_user_create()`](https://docs.ropensci.org/ruODK/reference/app_user_create.md)
  **\[experimental\]** : Create a new App User.
- [`app_user_delete()`](https://docs.ropensci.org/ruODK/reference/app_user_delete.md)
  **\[experimental\]** : Delete an App User.
- [`app_user_list()`](https://docs.ropensci.org/ruODK/reference/app_user_list.md)
  **\[experimental\]** : List all App Users of a Project.
- [`assignment_actors()`](https://docs.ropensci.org/ruODK/reference/assignment_actors.md)
  **\[experimental\]** : List all Actors assigned some server-wide Role.
- [`assignment_grant()`](https://docs.ropensci.org/ruODK/reference/assignment_grant.md)
  **\[experimental\]** : Assign an Actor to a server-wide Role.
- [`assignment_list()`](https://docs.ropensci.org/ruODK/reference/assignment_list.md)
  **\[experimental\]** : List all server-wide Assignments.
- [`assignment_revoke()`](https://docs.ropensci.org/ruODK/reference/assignment_revoke.md)
  **\[experimental\]** : Strip a server-wide Role Assignment from an
  Actor.
- [`form_assignment_list()`](https://docs.ropensci.org/ruODK/reference/form_assignment_list.md)
  **\[experimental\]** : Summarize all Form Assignments of one Project.
- [`project_assignment_list()`](https://docs.ropensci.org/ruODK/reference/project_assignment_list.md)
  **\[experimental\]** : List all Assignments of one Project.
- [`role_detail()`](https://docs.ropensci.org/ruODK/reference/role_detail.md)
  **\[experimental\]** : Show details of one Role.
- [`role_list()`](https://docs.ropensci.org/ruODK/reference/role_list.md)
  **\[experimental\]** : List all Roles.
- [`user_create()`](https://docs.ropensci.org/ruODK/reference/user_create.md)
  **\[experimental\]** : Create a new User.
- [`user_delete()`](https://docs.ropensci.org/ruODK/reference/user_delete.md)
  **\[experimental\]** : Delete a User.
- [`user_detail()`](https://docs.ropensci.org/ruODK/reference/user_detail.md)
  **\[experimental\]** : Show details of one User.
- [`user_list()`](https://docs.ropensci.org/ruODK/reference/user_list.md)
  **\[maturing\]** : List all users.
- [`user_preference_project_delete()`](https://docs.ropensci.org/ruODK/reference/user_preference_project_delete.md)
  **\[experimental\]** : Delete a project preference of the
  authenticated User.
- [`user_preference_project_set()`](https://docs.ropensci.org/ruODK/reference/user_preference_project_set.md)
  **\[experimental\]** : Set a project preference of the authenticated
  User.
- [`user_preference_site_delete()`](https://docs.ropensci.org/ruODK/reference/user_preference_site_delete.md)
  **\[experimental\]** : Delete a sitewide preference of the
  authenticated User.
- [`user_preference_site_set()`](https://docs.ropensci.org/ruODK/reference/user_preference_site_set.md)
  **\[experimental\]** : Set a sitewide preference of the authenticated
  User.
- [`user_reset_password()`](https://docs.ropensci.org/ruODK/reference/user_reset_password.md)
  **\[experimental\]** : Initiate a User password reset.
- [`user_update()`](https://docs.ropensci.org/ruODK/reference/user_update.md)
  **\[experimental\]** : Modify a User.
- [`user_update_password()`](https://docs.ropensci.org/ruODK/reference/user_update_password.md)
  **\[experimental\]** : Directly update a User password.

## Server

Functions related to server management.

- [`audit_get()`](https://docs.ropensci.org/ruODK/reference/audit_get.md)
  **\[stable\]** : Get server audit log entries.
- [`config_public()`](https://docs.ropensci.org/ruODK/reference/config_public.md)
  **\[experimental\]** : Show publicly accessible server configuration.

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
  **\[stable\]** : Abort with an error message.
- [`ru_msg_info()`](https://docs.ropensci.org/ruODK/reference/ru_msg_info.md)
  **\[stable\]** : Print an info message.
- [`ru_msg_noop()`](https://docs.ropensci.org/ruODK/reference/ru_msg_noop.md)
  **\[stable\]** : Print a noop message.
- [`ru_msg_success()`](https://docs.ropensci.org/ruODK/reference/ru_msg_success.md)
  **\[stable\]** : Print a success message.
- [`ru_msg_warn()`](https://docs.ropensci.org/ruODK/reference/ru_msg_warn.md)
  **\[stable\]** : Signal a warning message.

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
