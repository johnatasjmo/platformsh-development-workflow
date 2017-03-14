# Working with DB

### with Drush sql-sync

Get your drush aliases

```
local:drush-aliases
```

using sql-sync on local root or vagrant VM

```
drush sql-sync @source @target
drush sql-sync @platform.master @platform.\_local
drush sql-sync @self  @drupal.dev001
drush sql-sync @drupal.dev001 @self
```

### with Drush sql-dump

    ssh b5ciwn3jjhwsg-dev001-hcarzeq@ssh.us.platform.sh  
    cd web  
    drush sql-dump &gt; ../drush-backups/drushdump.sql
    drush sql-dump --result-file=PATH/TO/BACKUP/DIR/DBNAME_`date +"%m_%d_%Y-%H:%M"`.sql

On Vagrant VM

```
Vagrant ssh
scp b5ciwn3jjhwsg-dev001-hcarzeq@ssh.us.platform.sh:~/drush-backups/drushdump.sql ~/sites/
```

### with Sequel Pro

Platform tunnel

```
platform tunnel:info -e dev001
platform tunnel:list
```



