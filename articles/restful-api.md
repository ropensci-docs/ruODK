# Accessing the RESTful API

## Scope

This vignette provides a guided walk-through of the “getting data out”
functions of the RESTful API endpoints which list and view details.

`ruODK` users would mix and match parts of the demonstrated workflows to
build their own data pipelines, e.g.:

- to build a quick analysis from all data, freshly downloaded from a
  smaller project, or
- to build an interactive ETL pipeline to selectively download only new
  submissions for further processing and upload into downstream data
  warehouses.

A typical and more stream-lined workflow is provided in the RMarkdown
template “ODK Central via OData” which is supplied by `ruODK`.

### Three ways to happiness

ODK Central offers no less than three different ways to access data:

- viewing ODK Central data in MS PowerBI, MS Excel, Tableau, or `ruODK`
  through the OData service endpoints, or
- downloading all submissions including attachments as one (possibly
  gigantic) zip archive either through the “Export Submissions” button
  in the ODK Central form submissions page or through `ruODK`, or
- viewing ODK Central data through `ruODK`’s RESTful API functions.

While the `vignette("odata", package="ruODK")` (online
[here](https://docs.ropensci.org/ruODK/articles/odata-api.html))
illustrates the first option, this vignette demonstrates the remaining
two.

Not implemented (yet) are the “managing ODK Central” functions which
create, update, and delete projects, forms, users, roles, and
permissions. We haven’t yet found a strong use case to automate those
functions - ODK Central (driven by humans) does those jobs beautifully
on an expected scale.

## Setup ruODK

See
[`vignette("Setup", package = "ruODK")`](https://docs.ropensci.org/ruODK/articles/setup.html)
for detailed options to configure `ruODK`.

Here, we’ll grab the OData service URL from the form used in this
vignette, plus username and password of a web user of ODK Central with
access to that form.

[`ruODK::ru_setup()`](https://docs.ropensci.org/ruODK/reference/ru_setup.md)
will populate the default url, project ID, and form ID which are used by
`ruODK`’s other functions (unless specified otherwise).

``` r

library(ruODK)
# ruODK::ru_setup(
#   svc = "Form OData Service URL",
#   un = Sys.getenv("ODKC_TEST_UN"),
#   pw = Sys.getenv("ODKC_TEST_PW"),
#   tz = "Australia/Perth",
#   verbose = TRUE
# )
t <- fs::dir_create("media")
```

## Projects

List projects. We see the project ID, a name, the number of forms and
app users, dates of last form submissions plus project management
timestamps (created, updated).

The important bit here is the project ID.

``` r

fq_project_list <- ruODK::project_list()
```

``` r

fq_project_list %>% knitr::kable(.)
```

| id | name | description | archived | key_id | created_at | updated_at | deleted_at | verbs | forms | app_users | datasets | last_submission | last_entity |
|---:|:---|:---|:---|---:|:---|:---|:---|:---|---:|---:|---:|:---|:---|
| 1 | ruODK package tests | Forms and submissions used for [ruODK](https://github.com/ropensci/ruODK/) package tests. | FALSE | NA | 2023-08-04T01:47:13.622Z | 2025-04-14T01:46:12.246Z | NA | analytics.read , assignment.create , assignment.delete , assignment.list , audit.read , backup.run , config.read , config.set , dataset.create , dataset.list , dataset.read , dataset.update , entity.create , entity.delete , entity.list , entity.read , entity.restore , entity.update , field_key.create , field_key.delete , field_key.list , form.create , form.delete , form.list , form.read , form.restore , form.update , project.create , project.delete , project.read , project.update , public_link.create , public_link.delete , public_link.list , public_link.read , public_link.update , role.create , role.delete , role.update , session.end , submission.create , submission.delete , submission.list , submission.read , submission.restore , submission.update , user.create , user.delete , user.list , user.password.invalidate, user.read , user.update | 16 | 2 | 1 | 2025-04-29T06:39:38.806Z | 2025-09-07T08:50:04.963Z |
| 2 | ruODK package tests encrypted | NA | FALSE | 1 | 2023-08-04T01:47:41.258Z | 2024-03-04T07:04:18.715Z | NA | analytics.read , assignment.create , assignment.delete , assignment.list , audit.read , backup.run , config.read , config.set , dataset.create , dataset.list , dataset.read , dataset.update , entity.create , entity.delete , entity.list , entity.read , entity.restore , entity.update , field_key.create , field_key.delete , field_key.list , form.create , form.delete , form.list , form.read , form.restore , form.update , project.create , project.delete , project.read , project.update , public_link.create , public_link.delete , public_link.list , public_link.read , public_link.update , role.create , role.delete , role.update , session.end , submission.create , submission.delete , submission.list , submission.read , submission.restore , submission.update , user.create , user.delete , user.list , user.password.invalidate, user.read , user.update | 1 | 1 | 0 | 2024-03-04T07:06:16.788Z | NA |
| 3 | Sandbox | NA | FALSE | NA | 2023-08-04T01:47:50.572Z | NA | NA | analytics.read , assignment.create , assignment.delete , assignment.list , audit.read , backup.run , config.read , config.set , dataset.create , dataset.list , dataset.read , dataset.update , entity.create , entity.delete , entity.list , entity.read , entity.restore , entity.update , field_key.create , field_key.delete , field_key.list , form.create , form.delete , form.list , form.read , form.restore , form.update , project.create , project.delete , project.read , project.update , public_link.create , public_link.delete , public_link.list , public_link.read , public_link.update , role.create , role.delete , role.update , session.end , submission.create , submission.delete , submission.list , submission.read , submission.restore , submission.update , user.create , user.delete , user.list , user.password.invalidate, user.read , user.update | 1 | 0 | 0 | NA | NA |

Inspect a project using its ID. We receive a tibble with exactly one
row, all the columns of
[`ruODK::project_list`](https://docs.ropensci.org/ruODK/reference/project_list.md)
plus a column `verbs`, which contains all available API actions for a
project.

``` r

fq_project_detail <- ruODK::project_detail()
```

``` r

# Project details (without verbs)
fq_project_detail %>%
  dplyr::select(-"verbs") %>%
  knitr::kable(.)
```

| id | name | forms | app_users | last_submission | created_at | updated_at | archived |
|---:|:---|---:|---:|:---|:---|:---|:---|
| 1 | ruODK package tests | 16 | 2 | 2025-04-29T06:39:38.806Z | 2023-08-04T01:47:13.622Z | 2025-04-14T01:46:12.246Z | FALSE |

``` r


# Available verbs
fq_project_detail$verbs[[1]] %>% unlist(.)
#>  [1] "public_link.read"         "entity.delete"           
#>  [3] "user.delete"              "submission.list"         
#>  [5] "submission.delete"        "audit.read"              
#>  [7] "role.update"              "dataset.read"            
#>  [9] "form.restore"             "session.end"             
#> [11] "submission.restore"       "assignment.create"       
#> [13] "project.read"             "entity.read"             
#> [15] "dataset.list"             "dataset.update"          
#> [17] "form.list"                "public_link.delete"      
#> [19] "entity.create"            "form.read"               
#> [21] "user.read"                "entity.list"             
#> [23] "user.list"                "submission.update"       
#> [25] "user.create"              "dataset.create"          
#> [27] "field_key.list"           "project.delete"          
#> [29] "field_key.delete"         "role.create"             
#> [31] "user.update"              "public_link.update"      
#> [33] "project.update"           "submission.create"       
#> [35] "assignment.list"          "user.password.invalidate"
#> [37] "role.delete"              "submission.read"         
#> [39] "field_key.create"         "form.create"             
#> [41] "config.read"              "public_link.create"      
#> [43] "form.delete"              "project.create"          
#> [45] "entity.restore"           "entity.update"           
#> [47] "form.update"              "backup.run"              
#> [49] "config.set"               "public_link.list"        
#> [51] "assignment.delete"        "analytics.read"
```

Nothing apart from the verbs is new compared to the data returned by
[`ruODK::project_list`](https://docs.ropensci.org/ruODK/reference/project_list.md).

To learn more about the functionality behind the verbs, refer to the
interactive [ODK Central API
documentation](https://docs.getodk.org/central-api/).

To retrieve data from ODK Central, the functions shown below will
suffice.

## Forms

### List forms for a project

To download form submissions, we need to know project ID and form ID.

There are several ways of retrieving the form ID:

- Browsing forms in the ODK Central’s project overviews,
- Stealing the form ID from the OData service endpoint URL as shown on
  ODK Central’s form submission page,
- Listing form metadata for a given project ID with
  [`ruODK::form_list()`](https://docs.ropensci.org/ruODK/reference/form_list.md).

``` r

fq_form_list <- ruODK::form_list()
```

``` r

fq_form_list %>% knitr::kable(.)
```

| project_id | xml_form_id | state | enketo_id | enketo_once_id | created_at | updated_at | webforms_enabled | key_id | version | hash | sha | sha256 | draft_token | published_at | name | submissions | entity_related | review_states_received | review_states_has_issues | review_states_edited | last_submission | excel_content_type | public_links | created_by_id | created_by_type | created_by_display_name | created_by_created_at | created_by_updated_at | created_by_deleted_at | fid |
|---:|:---|:---|:---|:---|:---|:---|:---|:---|:---|:---|:---|:---|:---|:---|:---|---:|:---|---:|---:|---:|:---|:---|---:|---:|:---|:---|:---|:---|:---|:---|
| 1 | address_problem | open | q4bIaXNFWPGBfmhVVmx3rmYm9eHYpIH | 1d4c5916d82c5ee3376b7d2c0ce84ec73f967b18b2b7142e76ebe327eec23e1c | 2024-03-09 13:08:37 | 2025-04-14 09:46:12 | FALSE | NA | 20240308210648\[upgrade\] | 73517dac4561f7759b7606d126a3ac2f | a62ad0183bc538189956c815a6ad4aee66b807e3 | 9ff8ceefc00603ed08c16352ba1889f0553765e6fc0055902756a6ce31a65e71 | NA | 2024-12-23 04:54:59 | Address a problem | 1 | TRUE | 1 | 0 | 0 | 2024-03-09T05:11:55.753Z | application/vnd.openxmlformats-officedocument.spreadsheetml.sheet | 0 | 6 | user | Florian Mayer | 2023-06-30 04:23:51 | 2023-08-10 09:41:29 | NA | address_problem |
| 1 | burn_grading_forest | open | WKA7p8XRttHcS89tVdwuIFHNlAWJHfS | 04f0c916ad25ac1aeaa33316520f7aae2099bbdbd862bd77b1845b1f807e2a26 | 2023-08-09 11:14:17 | 2025-04-14 09:46:12 | FALSE | NA | 2023.1.1 | 5be80a0e66f1238ec7ac9a21237a8867 | c063c0f32f92f4020fcebee694cdde8baf91dfc6 | 1e6ed61493b88328a7458d720d87688ccd6034e7601986fe3ccdb1c06ec72e50 | NA | 2023-08-09 11:26:31 | Burn Grading Forest | 1 | FALSE | 1 | 0 | 0 | 2023-08-09T05:09:55.750Z | application/vnd.openxmlformats-officedocument.spreadsheetml.sheet | 0 | 6 | user | Florian Mayer | 2023-06-30 04:23:51 | 2023-08-10 09:41:29 | NA | burn_grading_forest |
| 1 | burn_grading_heath | open | 7WX4lTXqmeet7CHz8jjwLOc0EEmISkl | 2123c75dd4250401fcfee5abb7ddd24ba92cb5c00d84bcda1304a3454df0ba74 | 2023-08-09 11:17:02 | 2025-04-14 09:46:12 | FALSE | NA | 2023.1.0 | 4f9a8b2d9b3eb1243f158d92567df956 | ee591e640b97b2114a83ae20d90c40f3982f3091 | 8939811d509f09989be67d6b9e2988cc80ffff44b31727e269cce05d71699b23 | NA | 2023-08-09 11:23:56 | Burn Grading Heath | 1 | FALSE | 1 | 0 | 0 | 2023-08-09T05:13:06.566Z | application/vnd.openxmlformats-officedocument.spreadsheetml.sheet | 0 | 6 | user | Florian Mayer | 2023-06-30 04:23:51 | 2023-08-10 09:41:29 | NA | burn_grading_heath |
| 1 | burn_grading_verify | open | iQyzGfu0OspiuOMTlzM4HCbqkLWQRx8 | 20acaacf05e7275ef74ba9ef52d14743c6754c03bc090a2cbf5aace293987a55 | 2023-08-09 11:50:37 | 2025-04-14 09:46:12 | FALSE | NA | 2023.1.3 | f3879cdd1087ea3d950dabb3bd91d96f | b6c0d1ba1043de79fac80d92f563c403e94adffc | 18d3e9210590979a7bfbe34f528410432683cec1b59618fcd69c8f0b50575410 | NA | 2023-08-09 15:34:50 | Burn Grading Verify | 1 | FALSE | 0 | 0 | 0 | 2023-08-09T05:14:09.891Z | application/vnd.openxmlformats-officedocument.spreadsheetml.sheet | 0 | 6 | user | Florian Mayer | 2023-06-30 04:23:51 | 2023-08-10 09:41:29 | NA | burn_grading_verify |
| 1 | Flora-Quadrat-04 | open | t2fdSUXiyPboismgJValMrie7hal5YF | 2609a277d7f47e53c69424514de96ca298d25586e49c990b299cbc189478e7ec | 2023-12-03 15:02:20 | 2025-04-14 09:46:12 | FALSE | NA |  | 434ff9e1e33fc8bb35148c0cc6979708 | 206cf55b28adcd82db91bc5c11012524654c5bd1 | bb3b86a93ab3f6f5a16a6daa693c19a0c04f3deb68e50cf1bacd7c37efd9024a | NA | 2023-12-03 15:02:27 | Flora Quadrat 0.4 | 1 | FALSE | 0 | 0 | 0 | 2023-12-04T08:30:26.154Z | NA | 0 | 6 | user | Florian Mayer | 2023-06-30 04:23:51 | 2023-08-10 09:41:29 | NA | Flora-Quadrat-04 |
| 1 | Flora-Quadrat-04-gap | open | 7UzBNe95jXhdfqqG2JTmEG7mhQHoKQ1 | 040a5a743b5c1f8e78d4021df766b7228a5f481fbf7a959944d52d36299fde2b | 2023-12-03 15:09:55 | 2025-04-14 09:46:12 | FALSE | NA |  | 241c4759564ea039b4404b6892025500 | 61f5d1694e8866f6468ba6a2ff1c286226a66898 | 9504ab3daa2bf99270a7d4046c636a15c1972cdd93df388e936ad78411d619d9 | NA | 2023-12-03 15:10:05 | Flora Quadrat 0.4 (gap) | 1 | FALSE | 1 | 0 | 0 | 2024-03-04T07:08:52.813Z | NA | 0 | 6 | user | Florian Mayer | 2023-06-30 04:23:51 | 2023-08-10 09:41:29 | NA | Flora-Quadrat-04-gap |
| 1 | Flora-Quadrat-04-att | open | 0cuZcMAa1kemse3CFaws0ePH7hR0UPj | abf4f5edfb84342553f98177367167669c77b0155dd951ee4ddcb62e35cb917d | 2023-12-03 15:09:43 | 2025-04-14 09:46:12 | FALSE | NA |  | 2cb6a4b3d7f05ab055f3da89d0958b14 | c130067ce8f7940acf807e74a433fa2ec3545995 | 7b251e39369d48401ff4205ea0faf6b7bd1e04e5b8acb9f7b638b51459a22b94 | NA | 2023-12-03 15:09:46 | Flora Quadrat 0.4 (one att) | 1 | FALSE | 1 | 0 | 0 | 2023-12-03T07:45:07.801Z | NA | 0 | 6 | user | Florian Mayer | 2023-06-30 04:23:51 | 2023-08-10 09:41:29 | NA | Flora-Quadrat-04-att |
| 1 | I8n_label_choices | open | bRT4lNCag0T0ASSJKJ8pHjNTCTFTO4s | dbc21554352efe46948676b230b7c1abf8c5b1fcb25106109ae9dd6288b82fb5 | 2023-12-03 15:03:14 | 2025-04-14 09:46:12 | FALSE | NA |  | 14e3449067ec33efd82067a546c6554d | e190b678274da24e1ceb66f1de6d842550c29a5f | 4a7185f3ef411eb8749dbd9b540b811fffdec0572639425f0f7920ac9e9d09d9 | NA | 2023-12-03 15:03:18 | I8n label and choices | 1 | FALSE | 1 | 0 | 0 | 2023-12-04T08:30:56.757Z | NA | 0 | 6 | user | Florian Mayer | 2023-06-30 04:23:51 | 2023-08-10 09:41:29 | NA | I8n_label_choices |
| 1 | I8n_label_lng | open | 9sPuYNXpeZMnU7heWvoowMztz5Y93gH | 721e3c286e1b279a8885e3a443eb41335fdf310eed95b69a3424167e0c6ab8a5 | 2023-12-03 15:03:31 | 2025-04-14 09:46:12 | FALSE | NA |  | 6932ca6e75078cae86b9eaec119abad0 | 60e1ef208de91be00138f2c911da09dabb34e366 | c57f1a1d5f5f44fc119ceaa1c4db684f8159b3d9783a540e40dce3654299da19 | NA | 2023-12-03 15:03:51 | I8n label lang | 1 | FALSE | 1 | 0 | 0 | 2023-12-04T08:31:29.169Z | NA | 0 | 6 | user | Florian Mayer | 2023-06-30 04:23:51 | 2023-08-10 09:41:29 | NA | I8n_label_lng |
| 1 | I8n_lang_choicefilter | open | orpw5UXdq6Jym3aQg7IPwFnw4oRWYNL | 3072a8269c47b18ab49baa79bff29976e7700c0603daf5c2d99590dda62d63af | 2023-12-03 15:06:32 | 2025-04-14 09:46:12 | FALSE | NA |  | 02cc779cbc7ff0a136de77b7f7b8135d | fee1eb0b77aa5442885e231d4126f32aeb202040 | d842d8e9deb83bbf3475ef5e157286ca311f6cdf2cafebee04638d860489e39d | NA | 2023-12-03 15:06:36 | I8n label lang with choice filter | 1 | FALSE | 1 | 0 | 0 | 2023-12-04T08:32:30.641Z | application/vnd.openxmlformats-officedocument.spreadsheetml.sheet | 0 | 6 | user | Florian Mayer | 2023-06-30 04:23:51 | 2023-08-10 09:41:29 | NA | I8n_lang_choicefilter |
| 1 | I8n_no_lang_choicefilter | open | mByFnZbERATLDRmmksDYBqD1Rqz8Eab | 1f73b6265b220ed01499c97b0e21eed07ed30bffa7a206b54700887aeacb669f | 2023-12-03 15:09:17 | 2025-04-14 09:46:12 | FALSE | NA |  | fc5d8a6c19662445b890a1165bde6810 | a58e58f13df3a56dfbc538b5210fa3f3cfe39bbe | 0e647b8099d3bb84aa548b24a23b2b7f0383ff6a350bdeebf7adbeb8de61bfe7 | NA | 2023-12-03 15:19:38 | I8n label no lang with choice filter | 1 | FALSE | 1 | 0 | 0 | 2023-12-04T08:35:23.748Z | application/vnd.openxmlformats-officedocument.spreadsheetml.sheet | 0 | 6 | user | Florian Mayer | 2023-06-30 04:23:51 | 2023-08-10 09:41:29 | NA | I8n_no_lang_choicefilter |
| 1 | Locations | open | NT1E6p5HlknfdSW2VttaKgjb8DctRqy | bdf9c1c0dc5f1a607ae7d10ac4a4182c996030a2ac286b45c317cad6b23d8acd | 2023-12-03 15:02:45 | 2025-04-14 09:46:12 | FALSE | NA |  | 7365cf1fdad8d6c0ae7351bc05ecc2f2 | 784e30dc8daeb89b2b5680723cf520314843cba4 | d368f86c1e33b5682e10d7b9d7753e7edf6a35086bf6688945a281996cd30094 | NA | 2023-12-03 15:02:48 | Locations | 1 | FALSE | 0 | 0 | 0 | 2023-12-04T08:38:52.712Z | NA | 0 | 6 | user | Florian Mayer | 2023-06-30 04:23:51 | 2023-08-10 09:41:29 | NA | Locations |
| 1 | Locations_draft | open | itxB8ymLuT8YNq7Dx6tO5GUUpNCwq4H | NA | 2023-12-03 15:10:14 | 2025-04-14 09:46:12 | FALSE | NA |  | d1701aad460c192c2fc97eb10241e350 | d7726b5ecf5311e65730e0aa51afa61b93284ce8 | 3c26873d0450f32f5dac86f6a52f5248a2eb97800e78d98adb4c7a2f2d8334bc | itexle5sIMlJkDlfzz3yW8pw2gJ4dwdWbT8F8utpK\$g5hA7klBPyiuuoxw4zddqN | NA | Locations (draft) | 0 | FALSE | 0 | 0 | 0 | NA | NA | 0 | 6 | user | Florian Mayer | 2023-06-30 04:23:51 | 2023-08-10 09:41:29 | NA | Locations_draft |
| 1 | Locations_no_submissions | open | LWKvSaSk7Qa2FHFmNVf4AAuxqSH9zss | 74e225cac7e93d106d30c319d7ed72c0187651526c7756c54baf5ff7376ca116 | 2023-12-03 15:10:32 | 2025-04-14 09:46:12 | FALSE | NA |  | eb7caf4e3994b953999165ddfdb6eb3b | ae23fca247232b723073e5d842944172c77bd110 | 21e7b36f8fca61aae069e4ce7483549a97b915453a37f1436cd32882d23eeb3b | NA | 2023-12-03 15:10:35 | Locations (no submissions) | 0 | FALSE | 0 | 0 | 0 | NA | NA | 0 | 6 | user | Florian Mayer | 2023-06-30 04:23:51 | 2023-08-10 09:41:29 | NA | Locations_no_submissions |
| 1 | tech_specs | open | Pmobc6UPtwiGPYwcxN70n20fARJ4ANi | 150d453ceacc8f3ffb11dc9448ecee0020049b4e74388e57d29a0d1f700ced5e | 2025-04-13 17:17:53 | 2025-04-28 12:26:36 | FALSE | NA | 20250428122609 | 74c09eb8bb70fc553da1c7156bfa3356 | e063c406e3aa93a8a33c76db5acf0cd239a51364 | 65ab370d253f232b9cdebee32ed489b4fcb4c233950c6307be07710549153ad5 | NA | 2025-04-28 12:26:36 | PeopleWA Data Selection | 2 | FALSE | 1 | 0 | 0 | 2025-04-29T06:39:38.806Z | application/vnd.openxmlformats-officedocument.spreadsheetml.sheet | 1 | 6 | user | Florian Mayer | 2023-06-30 04:23:51 | 2023-08-10 09:41:29 | NA | tech_specs |
| 1 | report_problem | open | vibZw22eNVaGk7dfjqaNXCctVU1bHWi | b06f417d61c823479e16c244ea7a482df577cb385477bfa99a3ca75548619071 | 2024-03-09 13:08:06 | 2025-04-14 09:46:12 | FALSE | NA | 20240308210713\[upgrade\] | 59f6466f54efeacdc0c763ab260ddb94 | 208fcdf6ea3525a31a98c888a37fcf4faef1064a | a393b0f512303a68a47f4e50c558930a111f22fcf0958987ddc47f92b00b72f7 | NA | 2024-12-23 04:54:59 | Report a problem | 3 | TRUE | 2 | 0 | 0 | 2025-04-17T07:26:03.634Z | application/vnd.openxmlformats-officedocument.spreadsheetml.sheet | 1 | 6 | user | Florian Mayer | 2023-06-30 04:23:51 | 2023-08-10 09:41:29 | NA | report_problem |

Further to the metadata shown here, a column `xml` contains the entire
XForms definition (originally XML) as nested list.

If the original XML is needed rather than the R equivalent (nested
list), we can use
[`ruODK::form_xml`](https://docs.ropensci.org/ruODK/reference/form_xml.md)
with parameter `parse=FALSE`:

``` r

fq_form_xml <- ruODK::form_xml(parse = FALSE)
```

``` r

if (require(listviewer)) {
  listviewer::jsonedit(fq_form_xml)
} else {
  ru_msg_warn("Install package listviewer to browse the form XML.")
}
#> Loading required package: listviewer
```

### Inspect form schema

The `form_schema` represents all form fields of the XForms definition.

See the [ODK Central API
docs](https://docs.getodk.org/central-api-form-management/#getting-form-schema-fields)
and the examples of `??ruODK::form_schema()` for more detail.

``` r

fq_form_schema <- ruODK::form_schema()
```

``` r

fq_form_schema %>% knitr::kable(.)
```

| path | name | type | binary | selectMultiple | ruodk_name |
|:---|:---|:---|:---|:---|:---|
| /meta | meta | structure | NA | NA | meta |
| /meta/instanceID | instanceID | string | NA | NA | meta_instance_id |
| /encounter_start_datetime | encounter_start_datetime | dateTime | NA | NA | encounter_start_datetime |
| /reporter | reporter | string | NA | NA | reporter |
| /device_id | device_id | string | NA | NA | device_id |
| /location | location | structure | NA | NA | location |
| /location/area_name | area_name | string | NA | NA | location_area_name |
| /location/quadrat_photo | quadrat_photo | binary | TRUE | NA | location_quadrat_photo |
| /location/corner1 | corner1 | geopoint | NA | NA | location_corner1 |
| /habitat | habitat | structure | NA | NA | habitat |
| /habitat/morphological_type | morphological_type | select1 | NA | NA | habitat_morphological_type |
| /habitat/morphological_type_photo | morphological_type_photo | binary | TRUE | NA | habitat_morphological_type_photo |
| /vegetation_stratum | vegetation_stratum | repeat | NA | NA | vegetation_stratum |
| /vegetation_stratum/nvis_level3_broad_floristic_group | nvis_level3_broad_floristic_group | select1 | NA | NA | vegetation_stratum_nvis_level3_broad_floristic_group |
| /vegetation_stratum/max_height_m | max_height_m | decimal | NA | NA | vegetation_stratum_max_height_m |
| /vegetation_stratum/foliage_cover | foliage_cover | select1 | NA | NA | vegetation_stratum_foliage_cover |
| /vegetation_stratum/dominant_species_1 | dominant_species_1 | string | NA | NA | vegetation_stratum_dominant_species_1 |
| /vegetation_stratum/dominant_species_2 | dominant_species_2 | string | NA | NA | vegetation_stratum_dominant_species_2 |
| /vegetation_stratum/dominant_species_3 | dominant_species_3 | string | NA | NA | vegetation_stratum_dominant_species_3 |
| /vegetation_stratum/dominant_species_4 | dominant_species_4 | string | NA | NA | vegetation_stratum_dominant_species_4 |
| /perimeter | perimeter | structure | NA | NA | perimeter |
| /perimeter/corner2 | corner2 | geopoint | NA | NA | perimeter_corner2 |
| /perimeter/corner3 | corner3 | geopoint | NA | NA | perimeter_corner3 |
| /perimeter/corner4 | corner4 | geopoint | NA | NA | perimeter_corner4 |
| /perimeter/mudmap_photo | mudmap_photo | binary | TRUE | NA | perimeter_mudmap_photo |
| /taxon_encounter | taxon_encounter | repeat | NA | NA | taxon_encounter |
| /taxon_encounter/field_name | field_name | string | NA | NA | taxon_encounter_field_name |
| /taxon_encounter/photo_in_situ | photo_in_situ | binary | TRUE | NA | taxon_encounter_photo_in_situ |
| /taxon_encounter/taxon_encounter_location | taxon_encounter_location | geopoint | NA | NA | taxon_encounter_taxon_encounter_location |
| /taxon_encounter/life_form | life_form | select1 | NA | NA | taxon_encounter_life_form |
| /taxon_encounter/voucher_specimen_barcode | voucher_specimen_barcode | barcode | NA | NA | taxon_encounter_voucher_specimen_barcode |
| /taxon_encounter/voucher_specimen_label | voucher_specimen_label | string | NA | NA | taxon_encounter_voucher_specimen_label |
| /encounter_end_datetime | encounter_end_datetime | dateTime | NA | NA | encounter_end_datetime |

### Show details of one form

The details of a form are exactly the same as the output of
[`ruODK::form_list()`](https://docs.ropensci.org/ruODK/reference/form_list.md).

``` r

fq_form_detail <- ruODK::form_detail()
```

``` r

fq_form_detail %>% knitr::kable(.)
```

| name | fid | version | state | submissions | created_at | created_by_id | created_by | updated_at | published_at | last_submission | hash |
|:---|:---|:---|:---|---:|:---|---:|:---|:---|:---|:---|:---|
| Flora Quadrat 0.4 | Flora-Quadrat-04 |  | open | 1 | 2023-12-03T07:02:20.258Z | 6 | Florian Mayer | 2025-04-14T01:46:12.275Z | 2023-12-03T07:02:27.957Z | 2023-12-04T08:30:26.154Z | 434ff9e1e33fc8bb35148c0cc6979708 |

## Submissions

We are getting closer to the actual data! This section shows two of the
options for data access: dump all submissions, or extract a subset.

### Get all submissions for one form

Smaller datasets lend themselves to be exported in one go. ODK Central
offers one giant zip file containing all submissions, any repeating
groups, and any attachments both on the form submission page, and as API
endpoint which is provided as
[`ruODK::submission_export()`](https://docs.ropensci.org/ruODK/reference/submission_export.md).

The default behaviour of
[`ruODK::submission_export()`](https://docs.ropensci.org/ruODK/reference/submission_export.md)
is to write the zip file to the project root
([`here::here()`](https://here.r-lib.org/reference/here.html)), and to
overwrite existing previous downloads. See `?ruODK::submission_export()`
for alternative download and retention options.

In the following chuck, we illustrate common tasks:

- Download the zip file.
- Unpack the zip file.
- Join repeating form group data `data_taxon` to main data
  `data_quadrat` to annotate `data_taxon` with data from `data_quadrat`.
- Sanitise the column names.
- Prepend all attachment filenames
  (e.g. `data_quadrat$location_quadrat_photo`,
  `data_taxon$photo_in_situ`) with `media/`.

``` r

# Predict filenames (with knowledge of form)
fid <- ruODK::get_test_fid()
fid_csv <- fs::path(t, glue::glue("{fid}.csv"))
fid_csv_veg <- fs::path(t, glue::glue("{fid}-vegetation_stratum.csv"))
fid_csv_tae <- fs::path(t, glue::glue("{fid}-taxon_encounter.csv"))

# Download the zip file
se <- ruODK::submission_export(local_dir = t, overwrite = FALSE, verbose = TRUE)

# Unpack the zip file
f <- unzip(se, exdir = t)
fs::dir_ls(t)

# Prepend attachments with media/ to turn into relative file paths
fq_zip_data <- fid_csv %>%
  readr::read_csv(na = c("", "NA", "na")) %>% # form uses "na" for NA
  janitor::clean_names(.) %>%
  dplyr::mutate(id = meta_instance_id) %>%
  ruODK::handle_ru_datetimes(fq_form_schema) %>%
  ruODK::handle_ru_geopoints(fq_form_schema) %>%
  ruODK::attachment_link(fq_form_schema)

fq_zip_strata <- fid_csv_veg %>%
  readr::read_csv(na = c("", "NA", "na")) %>%
  janitor::clean_names(.) %>%
  dplyr::mutate(id = parent_key) %>%
  # ruODK::handle_ru_datetimes(fq_form_schema) parent_key%>% # no dates
  # ruODK::handle_ru_geopoints(fq_form_schema) %>%  # no geopoints
  # ruODK::ruODK::attachment_link(fq_form_schema) %>% # no att.
  dplyr::left_join(fq_zip_data, by = c("parent_key" = "meta_instance_id"))

fq_zip_taxa <- fid_csv_tae %>%
  readr::read_csv(na = c("", "NA", "na")) %>%
  janitor::clean_names(.) %>%
  dplyr::mutate(id = parent_key) %>%
  # ruODK::handle_ru_datetimes(fq_form_schema) %>%
  # ruODK::handle_ru_geopoints(fq_form_schema) %>%
  # ruODK::ruODK::attachment_link(fq_form_schema) %>%
  dplyr::left_join(fq_zip_data, by = c("parent_key" = "meta_instance_id"))
```

``` r

head(fq_zip_data)
#> # A tibble: 1 × 38
#>   submission_date     meta_instance_id encounter_start_date…¹ reporter device_id
#>   <dttm>              <chr>            <dttm>                 <lgl>    <chr>    
#> 1 2023-12-04 08:30:26 uuid:46d3939a-8… 2023-12-04 16:20:19    NA       collect:…
#> # ℹ abbreviated name: ¹​encounter_start_datetime
#> # ℹ 33 more variables: location_area_name <chr>, location_quadrat_photo <chr>,
#> #   location_corner1_latitude <dbl>, location_corner1_longitude <dbl>,
#> #   location_corner1_altitude <dbl>, location_corner1_accuracy <dbl>,
#> #   habitat_morphological_type <chr>, habitat_morphological_type_photo <chr>,
#> #   perimeter_corner2_latitude <dbl>, perimeter_corner2_longitude <dbl>,
#> #   perimeter_corner2_altitude <dbl>, perimeter_corner2_accuracy <dbl>, …
head(fq_zip_strata)
#> # A tibble: 2 × 47
#>   nvis_level3_broad_floristic_gr…¹ max_height_m foliage_cover dominant_species_1
#>   <chr>                                   <dbl> <chr>         <chr>             
#> 1 w3.0_shrub                                  1 70-30         Test species 1    
#> 2 w1.1_trees_rainforest                       5 10-5          Test species 5    
#> # ℹ abbreviated name: ¹​nvis_level3_broad_floristic_group
#> # ℹ 43 more variables: dominant_species_2 <chr>, dominant_species_3 <chr>,
#> #   dominant_species_4 <chr>, parent_key <chr>, key.x <chr>, id.x <chr>,
#> #   submission_date <dttm>, encounter_start_datetime <dttm>, reporter <lgl>,
#> #   device_id <chr>, location_area_name <chr>, location_quadrat_photo <chr>,
#> #   location_corner1_latitude <dbl>, location_corner1_longitude <dbl>,
#> #   location_corner1_altitude <dbl>, location_corner1_accuracy <dbl>, …
head(fq_zip_taxa)
#> # A tibble: 2 × 49
#>   field_name     photo_in_situ     taxon_encounter_loca…¹ taxon_encounter_loca…²
#>   <chr>          <chr>                              <dbl>                  <dbl>
#> 1 Test species 1 1701678535420.jpg                  -31.9                   116.
#> 2 Test species 6 1701678592627.jpg                  -31.9                   116.
#> # ℹ abbreviated names: ¹​taxon_encounter_location_latitude,
#> #   ²​taxon_encounter_location_longitude
#> # ℹ 45 more variables: taxon_encounter_location_altitude <dbl>,
#> #   taxon_encounter_location_accuracy <dbl>, life_form <chr>,
#> #   voucher_specimen_barcode <lgl>, voucher_specimen_label <dbl>,
#> #   parent_key <chr>, key.x <chr>, id.x <chr>, submission_date <dttm>,
#> #   encounter_start_datetime <dttm>, reporter <lgl>, device_id <chr>, …
# Further: create map with popups, see vignette "odata"
```

### List submissions for one form

Not always is it appropriate to download all submissions and all
attachments at once.

If forms feed into downstream data warehouses, the typical ETL workflow
is to

- List all submissions from ODK Central
- Select the subset of new submissions to download, e.g.
  - Submissions younger than the oldest submission date in the data
    warehouse.
  - Submissions whose `instance_id` is not already present in the data
    warehouse.
- Download only the selected submissions.
- Download attachments of only the selected submissions.

``` r

fq_submission_list <- ruODK::submission_list()
```

``` r

fq_submission_list %>% knitr::kable(.)
```

| instance_id | submitter_id | device_id | created_at | updated_at | review_state | user_agent | deleted_at | submitter_id_2 | submitter_type | submitter_display_name | submitter_created_at | submitter_updated_at | submitter_deleted_at | current_version |
|:---|---:|:---|:---|:---|:---|:---|:---|---:|:---|:---|:---|:---|:---|:---|
| uuid:46d3939a-8bc5-4084-9154-d043bc4d3239 | 12 | collect:OHnydk6INUIfDHNl | 2023-12-04 16:30:26 | 2024-03-05 13:29:54 | approved | org.odk.collect.android/v2023.3.1 Dalvik/2.1.0 (Linux; U; Android 10; vivo 1937 Build/QP1A.190711.020) | NA | 12 | field_key | ruodk | 2023-08-09 11:51:12 | NA | NA | 12 , 2023-12-04T08:30:26.154Z , uuid:46d3939a-8bc5-4084-9154-d043bc4d3239 , TRUE , collect:OHnydk6INUIfDHNl , org.odk.collect.android/v2023.3.1 Dalvik/2.1.0 (Linux; U; Android 10; vivo 1937 Build/QP1A.190711.020), 12 , field_key , ruodk , 2023-08-09T03:51:12.864Z |

The list of submissions critically contains each submission’s unique ID
in `instance_id`. If the submissions shall be downloaded and uploaded
into another data warehouse, the `instance_id` can be used to determine
whether a record already exists in the downstream warehouse or not. This
workflow is preferable where the majority of submissions is already
imported into another downstream data warehouse, and we only want to add
new submissions, as in submissions which are not already imported into
the data warehouse.

Furthermore, the `instance_id`s can now be used to retrieve the actual
submissions.

### Get submission data

In order to import each submission, we need to retrieve the data by
`instance_id`.

``` r

# One submission
fq_one_submission <- ruODK::get_one_submission(
  fq_submission_list$instance_id[[1]]
)

# Multiple submissions
fq_submissions <- ruODK::submission_get(fq_submission_list$instance_id)
```

### Parse submissions

The data in `sub` is one row of the bulk downloaded submissions in
`data_quadrat`. The data in `submissions` represents all (or let’s
pretend, the selected) submissions in `data_quadrat`. The field `xml`
contains the actual submission data including repeating groups.

The structure is different to the output of
[`ruODK::odata_submission_get`](https://docs.ropensci.org/ruODK/reference/odata_submission_get.md),
therefore
[`ruODK::odata_submission_rectangle`](https://docs.ropensci.org/ruODK/reference/odata_submission_rectangle.md)
does not work for those, as here we might have repeating groups included
in a submission.

This structure could be used for upload into data warehouses accepting
nested data as e.g. JSON.

``` r

if (requireNamespace("listviewer")) {
  listviewer::jsonedit(fq_submissions, mode = "code")
} else {
  ru_msg_info("Please install package listviewer!")
}
```

## Outlook

The approach shown here yields nested and stand-alone records, which is
useful if the subsequent use requires records in nested JSON or XML
format. Complex forms with repeating sub-groups will result in highly
nested lists, whose structure heavily depends on the completeness of the
submissions.

The other approach shown in
[`vignette("odata-api", package="ruODK")`](https://docs.ropensci.org/ruODK/articles/odata-api.html)
yields rectangled data in several normalised tables, which is useful for
analysis and visualisation.
