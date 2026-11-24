# Build test data for ruODK's test suite.

Internal helpers that build random UUIDs, minimal valid XForms form
definitions, and matching Submission XML. Not part of the public API.

## Usage

``` r
ru_uuid()

ru_test_form_xml(
  fid,
  version = "1",
  photo = FALSE,
  itemset = NULL,
  geo = FALSE
)

ru_test_submission_xml(
  fid,
  iid,
  deprecated_id = NULL,
  photo = FALSE,
  name = "Jo",
  geo = NULL
)
```

## Arguments

- fid:

  The form ID to use in the form definition.

- version:

  The form version to use in the form definition.

- photo:

  Whether the form holds a binary photo upload field.

- itemset:

  The filename of a CSV choice list to reference as a secondary file
  instance, or `NULL` for none. The instance ID is the filename without
  extension.

- geo:

  The value of the geopoint field, or `NULL` for none.

- iid:

  The Submission `instanceID`.

- deprecated_id:

  An optional replaced version's `instanceID`.

- name:

  The value of the name field.

## Value

`ru_uuid()` returns a random UUID with `uuid:` prefix.
`ru_test_form_xml()` and `ru_test_submission_xml()` return XML as a
single string.
