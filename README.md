## Repository for the Data Zoo Gang's website

Go to www.datazoogang.de to visit this website.

### for website maintainers

To update the website, do the changes locally.

Then

```r
rmarkdown::render_site(encoding = 'UTF-8')
gitcreds::gitcreds_set() # and paste the token stored in my_GH_token.txt
gert::git_push()
```

Once the Github action has run (ca. 1 min), the site should be up to date!
