# Working with DB

### with Drush sql-sync

Get your drush aliases

```

```

local:drush-aliases  

drush sql-sync @source @target  

drush sql-sync @platform.master @platform.\\_local  

drush sql-sync @self  @drupal.dev001  

drush sql-sync @drupal.dev001 @self



### with Drush sql-dump

```
ssh b5ciwn3jjhwsg-dev001-hcarzeq@ssh.us.platform.sh  
cd web  
drush sql-dump &gt; ../drush-backups/drushdump.sql  
```

On Vagrant VM

```
Vagrant ssh
scp b5ciwn3jjhwsg-dev001-hcarzeq@ssh.us.platform.sh:~/drush-backups/drushdump.sql ~/sites/
```



