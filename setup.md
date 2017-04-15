# Set Up

### Drupal VM

Follow instructions as per[https://www.drupalvm.com/](https://www.drupalvm.com/)and initiate a VM

### platform.sh

Create an account on [https://platform.sh/](https://platform.sh/)and initiate a project

On local machine

```
platform get \[project-id\] \[folder-name\]
cd drupal
platform build
```

create local.settings.php and add drupal VM credentials

add hash by going to vagrant ssh and type

```
drush cget system.site

get default\_config\_hash code and copy
```

Copy contents to settings.local.php

    `settings['hash_salt'] = 'myhash';        
    config_directories[CONFIG_SYNC_DIRECTORY] = '../config/sync';` 

> note You should never commit a settings.local.php file to your repository. The file will always be overwritten by Platform.sh \(when using the drupal build flavor\).

### Platform CLI in Vagrant VM

```
vagrant ssh
cd home/vagrant
curl -sS https://platform.sh/cli/installer
platform
```

### Bitbucket

Create an account on[https://bitbucket.org/](https://bitbucket.org/)and an empty repo

Get the bitbucket url

On local machine

```
git remote add bitbucket https://USERNAME@bitbucket.org/USERNAME/REPO.git
git remote -v
```

### platform.sh and Bitbucket integration

Go to bitbucket and add platform sh as integration and select your new project
