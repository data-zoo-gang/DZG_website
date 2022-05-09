## Repository for the Data Zoo Gang's website

This repository contains the material behind the Data Zoo Gang's website.

Go to www.datazoogang.de to visit the website.

### for website maintainers

Check that you have all R packages required for building this website:

```r
if (!requireNamespace("knitr"))      install.packages("knitr")
if (!requireNamespace("distill"))    install.packages("distill")
if (!requireNamespace("tibble"))     install.packages("tibble")
if (!requireNamespace("RefManageR")) install.packages("RefManageR")
if (!requireNamespace("kableExtra")) install.packages("kableExtra")
if (!requireNamespace("stringr"))    install.packages("stringr")
```

For changes related to references: 

- please do not alter the BibTeX file directly, but perform changes in the shared Zotero library DZG and overwrite a new file `publications.bib`.
- please add the PDFs in the folder *pdfs* and name them with the same bibtex keys as those referring to the corresponding publications.

For pictures, before committing please make sure that they are saved with a resolution of 270px wide (GIMP can be used for resizing: Image -> Scale Image...) and an extension `.jpg` or `.png`.

To update the website, do the changes locally, save, and then run the following in R:

```r
rmarkdown::render_site(encoding = 'UTF-8')   # to build the updated website
gert::git_add(".")                           # to stage all changes
gert::git_commit(message = "Update website") # to add the commit message
gitcreds::gitcreds_set()                     # to load GH credentials (if using token system)
                                             # (paste the token stored in my_GH_token.txt)
gert::git_push()                             # to push all changes on GitHub
```

Once the Github actions have run (ca. 1 min), the site should be up to date!
