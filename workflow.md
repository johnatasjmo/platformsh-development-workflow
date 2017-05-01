# Development workflow

### As Senior developer

1. Create a branch from master for each user story \(i.e. US-1\)
2. Create pull request on bitbucket
3. After developer finished coding, merge pull request
4. Delete user story \(US-1\)

### As Developer

1. Pull user story locally \(US-1\)
2. work, commit
3. Rebase, notify that branch is ready for testing
4. Push to bitbucket

##### Checkout

```
git checkout WORKINGBRANCH
platform tunnel:open
```

##### Pull code

```
git pull branch
git status
platform buil
```

##### Pull DB

```
drush sql-sync @MASTER-BRANCH @self -y && drush cr
```

##### Pull files

```
drush rsync  @drupal.MY-BRANCH:%files @self:%files
```

##### Code and commit

```
git add -A
git commit -m "some code done"
```

##### Optional - export configuration and commit

```
drush cex -y
git add -A
git  commit -m "configuration exported"
```

##### Rebase

```
git rebase -i bb/master
```

##### Push

```
platform snapshot:create
git commit --allow-empty -m "branch ready to merge"
git push bitbucket
platform snapshot:create
```



