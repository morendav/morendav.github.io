
# Migration to Introduction theme
Date: March 2024
Goal: migrate back from Introduction to PaperMod


## Roll back options

1. rebase main to backup created prior to theme migration from PaperMod --> Introduction
    * Do rebase main
    * Have to make other edits, including
        * copy new post (there is at least 1 new post in Introduction theme that needs to be copied into the rebased backup)
        * Updates to 'About Me' page

2. Update config file to swap theme from Introduction --> Papermod
    * Do _not_ rebase Main
    * Update Theme
    * Have to make other edits, including
        * file structure for posts
        * self-referencing links inside posts must update to new file structre
        * links to resources must update to file structure



## Roll back plan

Plan: Option 2

### Rollback action plan
[x] Update theme intro --> papermod
[x] Move old pages to papermode folder structure
[x] Move new post to papermode folder structure
[x] Test all pages on locally hosted site
[x] Update ABOUT ME section


### Post-Rollback action plan
[ ] Test favicon on dlm.rocks
[ ] Test all pages on dlm.rocks
[ ] 



------------------------------------------------------------------------
------------------------------------------------------------------------

## Update - Dec 2024

Status: Migration completed
- main to remote main push
- pushed to site

Rationale for rollback: 
- papermod has search feature
- intro 'art' sectino can link to other sites e.g. instagram

