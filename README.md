## Repository for the Data Zoo Gang's website

This repository contains the material behind the Data Zoo Gang's website.

Go to www.datazoogang.de or www.datazoogang.com to visit the website.

### Development requirements

Check that you have all R packages required for building this website:

```r
if (!requireNamespace("knitr"))      install.packages("knitr")
if (!requireNamespace("distill"))    install.packages("distill")
if (!requireNamespace("tibble"))     install.packages("tibble")
if (!requireNamespace("tidyr"))      install.packages("tidyr")
if (!requireNamespace("RefManageR")) install.packages("RefManageR")
if (!requireNamespace("bibtex")) install.packages("bibtex")
if (!requireNamespace("kableExtra")) install.packages("kableExtra")
if (!requireNamespace("stringr"))    install.packages("stringr")
```

### Changing or updating publications

- 1. do not alter the BibTeX file directly, but perform changes in the shared Zotero library DZG.
- 2. use `dzg_xxx` tags in Zotero library since those are used to create tables (`xxx` refers to markdown labels defined in `publications.Rmd`).
- 3. export the updated library using Zotero (Select all, then File -> Export Library...) so as to overwrite the previous version of the BibTeX file `publications.bib`. I add issues exporting using "UTF-8" encoding (missing authors), so I now use "western".
- 4. add the PDFs in the folder *pdfs* and name them with the same bibtex keys as those referring to the corresponding publications.

For pictures, before committing please make sure that they are saved with a resolution of 270px wide (GIMP can be used for resizing: Image -> Scale Image...) and an extension `.jpg` or `.png`.

To update the website, do the changes locally, save, and run the following in R:

```r
rmarkdown::render_site(encoding = 'UTF-8')   # to build the updated website
gert::git_add(".")                           # to stage all changes
gert::git_commit(message = "Update website") # to add the commit message
gitcreds::gitcreds_set()                     # to load GH credentials (if using token system)
                                             # (paste the token stored in my_GH_token.txt)
gert::git_push()                             # to push all changes on GitHub
```

Once the Github actions have run (ca. 1 min), the site should be up to date!

As an experiment, the repo is forked onto https://github.com/courtiol/DZG_website.com to deploy the website on .com domain as well.
To update the .com pages, the fork must thus be updated after any change on the main original repo.
Do that in GitHub directly using the sync fork button on the page of the forked repo.


### Blogging

For creating blogs, run the following in R:

```r
distill::create_post("my_new_post") # adjust the name used to name the Rmd file
```

Then, edit the Rmd file newly created in `_post`.

Here is a skeleton:

```
---
title: "A sexy title"
description: |
  Post description
categories:
  - R
author: Alexandre Courtiol
preview: image_in_blog_folder.jpg
output: distill::distill_article
repository_url: https://github.com/data-zoo-gang/DZG_website
---

Blog content
```

Then, you must knit this post, and *then* render the website:

```r
rmarkdown::render_site(encoding = 'UTF-8') 
```

If you are not happy, rince and repeat.

You can also update the internal name to match the blog title:

```r
rename_post_dir("_posts/2026-02-23-test") # adjust the data and name
```

If you are happy, publish it:

```r
gert::git_add(".")                           # to stage all changes
gert::git_commit(message = "Update website") # to add the commit message
gitcreds::gitcreds_set()                     # to load GH credentials (if using token system)
                                             # (paste the token stored in my_GH_token.txt)
gert::git_push()                             # to push all changes on GitHub
```

For more details about blogging using distill, see [the documentation](https://rstudio.github.io/distill/blog.html).
