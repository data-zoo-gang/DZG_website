## Repository for the Data Zoo Gang's website

This repository contains the material behind the Data Zoo Gang's website.

Go to www.datazoogang.de or www.datazoogang.com to visit the website.

### for website maintainers

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

For changing or updating references: 

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

