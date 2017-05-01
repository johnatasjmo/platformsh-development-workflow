# Development workflow

### As Senior developer

1. Create a branch from master for each user story \(i.e. US-1\)
2. Create pull request on bitbucket
3. After developer finished coding, merge pull request
4. Delete user story \(US-1\)

### As Developer

1. Pull user story locally \(US-1\). Pull code, pull DB, build environment with platform build
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
git pull bitbucket WORKINGBRANCH
```

##### Pull DB

```
drush sql-sync @MASTER-BRANCH @self -y && drush cr
```

##### Pull files

```
drush rsync  @drupal.MY-BRANCH:%files @self:%files
```

##### Build the environment locally

```
platform build
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
git rebase -i bitbucket/master
```

##### Push

```
platform snapshot:create
git push bitbucket
platform snapshot:create
```

### Merge a branch by Senior Developer

* On bitbucket, create a pull request and approve it
* On bitbucket, merge the pull request
* Delete branch from bitbucket



