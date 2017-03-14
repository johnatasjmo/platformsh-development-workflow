# Development workflow

### As Senior developer

1. Create a Master Branch
2. Create a Test Branch
3. Create a User-Story from Test Branch and assign to developer

### As Developer

Once user story is assigned, identify the branch

##### Checkout

```
platform environment:syncronize
platform tunnel:open
```

##### Pull code

```
platform local:build
git status
```

##### Pull DB

```
drush sql-sync @master-branch @self -y && drush cr
```

##### Pull files

```
drush rsync  @drupal.my-branch:%files @self:%files
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

##### Push

```
platform snapshot:create
git push bitbucket
platform snapshot:create
```



