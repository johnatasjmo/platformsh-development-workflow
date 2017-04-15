# Working with Code

### Create a branch as child of master \(one per user-story\)

```bash
platform checkout PARENT-BRANCH // checkout parent branch
platform branch CHILD-BRANCH //creates a new branch as child of parent (1 min process)
git commit --allow-empty -m "branch created" // bookmark
git push bitbucket // this push a new commit to bitbucket and you can see changes on bitbucket and platform are linked
git branch -u bitbucket/CHILD-BRANCH
platform snapshot:create
```

### Merge a branch

XXXXX?????XXXXXX

### Delete a branch

On local machine, the following code force deletes a local branch and pushes to bitbucket

```
git branch -D BRANCHNAME
git push bitbucket --delete BRANCHNAME
```

### Export configuration from local to platform

On local machine

```
drush cex -y
git add -A
git add./ #optional
git  commit -m "configuration exported"
platform snapshot:create
git push bitbucket
platform snapshot:create
```

On local machine with config-merge \(testing\)

```
drush @drupal.MY-BRANCH config-merge @self --git --branch=export
```

Install module

```
composer require drupal/<modulename>
```



