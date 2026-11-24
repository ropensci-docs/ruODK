# Prepare a Form definition for upload.

Internal helper that turns an XML string or a local `.xml`, `.xls` or
`.xlsx` file into the body, content type and extra headers of a Form
upload request. Not part of the public API.

## Usage

``` r
ru_form_upload(xml = NULL, file = NULL, xls_form_id_fallback = NULL)
```

## Arguments

- xml:

  An XForms XML definition as a single string, or `NULL`.

- file:

  A path to a local form definition file, or `NULL`.

- xls_form_id_fallback:

  A form ID for spreadsheets that do not specify one, or `NULL`.

## Value

A list with `body`, `content_type` and `extra_headers`.
