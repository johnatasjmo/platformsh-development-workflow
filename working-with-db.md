# Working with DB

### with Drush sql-sync

Get your drush aliases

```
platform local:drush-aliases
drush sa
```

using sql-sync on local root or vagrant VM

```
drush sql-sync @source @target
drush sql-sync @platform.MASTER @platform.\_local
drush sql-sync @self  @drupal.dev001
drush sql-sync @drupal.MY-BRANCH @self
```

### with Drush sql-dump

    ssh [PROJECT-ID]-[ENV]@ssh.[REGION].platform.sh 
    cd web  
    drush sql-dump --result-file=../drush-backups/couriertms_`date +"%m_%d_%Y-%H:%M"`.sql
    drush sql-dump --result-file=PATH/TO/BACKUP/DIR/DBNAME_`date +"%m_%d_%Y-%H:%M"`.sql

### On Vagrant VM

```
Vagrant ssh
scp [PROJECT-ID]-[ENV]@ssh.[REGION].platform.sh:~/drush-backups/drushdump.sql ~/sites/
```

### with Sequel Pro

Before connecting to platform, you must open a tunnel

```
platform tunnel:info -e BRANCH
platform tunnel:list
platform tunnel:open
```

* Export DB from platform
* Import DB into local host



