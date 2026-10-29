# NA

First release:

[`usethis::use_cran_comments()`](https://usethis.r-lib.org/reference/use_cran_comments.html)
(file present: `cran-comments.md`)

Update (aspirational) install instructions in README

Proofread `Title:` and `Description:`

Check that all exported functions have `@return` and `@examples`

Check that `Authors@R:` includes a copyright holder (role ‘cph’)

Check [licensing of included
files](https://r-pkgs.org/license.html#sec-code-you-bundle)

Review <https://github.com/DavisVaughan/extrachecks>

Prepare for release:

`git pull`

`urlchecker::url_check()`

`devtools::build_readme()`

`devtools::check(remote = TRUE, manual = TRUE)` (2 NOTES: archived
resubmission info + future timestamp verification)

`devtools::check_win_devel()` (submitted 2026-02-18; wait for email
results)

`git push`

Submit to CRAN:

`usethis::use_version('patch')` (only if you want to bump beyond 0.6.0)

`devtools::submit_cran()`

Approve email

Wait for CRAN…

Accepted 🎉

[`usethis::use_github_release()`](https://usethis.r-lib.org/reference/use_github_release.html)

`usethis::use_dev_version(push = TRUE)`
