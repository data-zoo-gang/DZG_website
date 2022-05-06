## Repository for the Data Zoo Gang's website

This repository contains the material behind the Data Zoo Gang's website.

Go to www.datazoogang.de to visit our website.

### for website maintainers

To update the website, do the changes locally, save, and then run the following in R:

```r
rmarkdown::render_site(encoding = 'UTF-8')   # to build the updated website
gert::git_add(".")                           # to stage all changes
gert::git_commit(message = "Update website") # to add the commit message
gitcreds::gitcreds_set()                     # to load GH credentials 
                                             # (paste the token stored in my_GH_token.txt)
gert::git_push()                             # to push all changes on GitHub
```

Once the Github actions have run (ca. 1 min), the site should be up to date!
