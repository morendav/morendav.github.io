Hacky way to rebase main between branches

To migrate between themes by rebasing main branch to a backup branch in git
Example: from some_branch --> main

// start off with updating local dir
git checkout main
git pull

// use 'ours' strategy for the merge
git checkout some_branch
git merge -s ours main
git checkout main
git merge some_branch


This will force branch 'main' to be replaced by 'some_branch'

