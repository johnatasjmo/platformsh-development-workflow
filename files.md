# Working with files

Recommendation, put files on master branch and sync back to developing branches using platform sync bottom.

### With RSYNC

```
rsync -r my/local/files/. [PROJECT-ID]-[ENV]@ssh.[REGION].platform.sh:public/sites/default/files/
```

_comment: Hey, instead of -r, you probably want to use -aPv_

Go to your default folder on local machine!

```
rsync -r files/. \[SSH-URL\]:public/sites/default/files/
```

\# to sync from local to remote, not delete files not present on remote

```
rsync -r files/. [PROJECT-ID]-[ENV]@ssh.[REGION].platform.sh:web/sites/default/files/
```

\# to sync form local to remote, delete files on remote not present in local

```
rsync -r --delete files/. [PROJECT-ID]-[ENV]@ssh.[REGION].platform.sh:web/sites/default/files/
```

### with drush

```
drush rsync @platform.\_local:%files @platform.MY-BRANCH:%files
```

```
drush rsync @self:%files @drupal.MY-BRANCH:%files
```

```
drush rsync -s --delete @self:%files @drupal.MY-BRANCH:%files
```



##### After files are on master branch, sync them to child-branches as needed

![](/assets/sync.png)

