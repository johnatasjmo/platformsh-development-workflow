# About

Following process is a guide for Drupal 8 development using Drupal VM locally and platform.sh

The following is an unofficial guide 

# Preparation

Installed on local machine
* Vagrant
* Virtual Box
* Drupal VM [Drupal VM](https://www.drupalvm.com/)
* Platfrom CLI
* Git
* Source Tree

Accounts on cloud
* Bitbucket
* platform.sh

# Local Machine
## Drupal VM
copy settings.php
delete files on drupal/
#DEBUG local Drupal VM
http://pimpmylog.couriersh.dev/
## Platform CLI
Platform on local machine
Platform on VM
  Install platform on vagrant ssh
  go to home/vagrant
  curl -sS https://platform.sh/cli/installer | php
  chmod 777 .platformsh
  curl -sS https://platform.sh/cli/installer | php
  source ~/.profile
  platform
## Git
Git ignore files

# First deployment
## Create site on platform.sh
Create a site on platform.sh web
Build on local machine
  platform get [project-id] [folder-name]
  cd drupal
  platform build
create local.settings.php
  local settings go to settings.local.php
  add hash by going to vagrant ssh and type
  drush cget system.site
  get default_config_hash code and copy
  $settings['hash_salt'] = 'AyT9s8OUcclfALRE_imByOMgtZ19eOlqdF6zI3p7yqo';
  $config_directories[CONFIG_SYNC_DIRECTORY] = '../config/sync';
  add hash and config
  note You should never commit a settings.local.php file to your repository. The file will always be overwritten by Platform.sh (when using the drupal build flavor).

move config
## Add remote bitbucket
Add remote on bitbucket
  git remote add bitbucket https://avalanchaa@bitbucket.org/avalanchaa/couriersh.git
Integration bitbucket with platform.sh
First commit
## Create test branch
create with platform:branch Test 


## Working with files
Files
RSYNC
http://www.tecmint.com/rsync-local-remote-file-synchronization-commands/
rsync -r my/local/files/. [PROJECT-ID]-[ENV]@ssh.[REGION].platform.sh:public/sites/default/files/
https://docs.platform.sh/frameworks/drupal7/migrating.html
comment: Hey, instead of -r, you probably want to use -aPv
without drush
  hne3vvou3repg-dev001-hcarzeq@ssh.us.platform.sh
  Go to your default folder on local machine!
  rsync -r files/. [SSH-URL]:public/sites/default/files/
#to sync from local to remote, not delete files not present on remote
  rsync -r files/. hne3vvou3repg-dev001-hcarzeq@ssh.us.platform.sh:web/sites/default/files/
#to sync form local to remote, delete files on remote not present in local
  rsync -r --delete files/. hne3vvou3repg-dev001-hcarzeq@ssh.us.platform.sh:web/sites/default/files/
with drush
  drush rsync @platform._local:%files @platform.master:%files
  drush rsync @self:%files @drupal.dev001:%files
  drush rsync -s --delete @self:%files @drupal.dev001:%files


## Working with DB
# DRUSH
local:drush-aliases
drush sql-sync @source @target
drush sql-sync @platform.master @platform._local
drush sql-sync @self  @drupal.dev001
drush sql-sync @drupal.dev001 @self

Drush aliases for Courier (hne3vvou3repg):
    @drupal._local
    @drupal.dev001
    @drupal.dev002
    @drupal.master 

#with drush on platform sh and backup
ssh b5ciwn3jjhwsg-dev001-hcarzeq@ssh.us.platform.sh
cd web
drush sql-dump > ../drush-backups/drushdumpjmo.sql
exit
scp b5ciwn3jjhwsg-dev001-hcarzeq@ssh.us.platform.sh:~/drush-backups/drushdumpjmo.sql ~/sites/

# Collaborate with other developers
## Add permissions on bitbucket
## Add persmissions on platform.sh 

#Worflow
1. Create a Sprint
2. Create a Branch
3. Create a Story
4. Sync
How to do configuration-management
How to move DB up

