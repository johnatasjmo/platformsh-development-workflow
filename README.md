# Web development in Drupal 8 with platform.sh

The following is a guide for web development with Drupal 8 using the following techniques:

* Drupal VM for local development
* Git repository using Bitbucket
* All codes goes via git push to Bitbucket and deployed in platform.sh
* Github workflow, one branch per user-story, one environment per branch
* Everything in Master branch is deployable

# Roles

**Senior developer** - the one who merges code into Master

**Developer** - contributor to code

# Requirements

Cloud accounts

* Bitbucket
* platform.sh

On local machine

* Source Tree
* Platform CLI
* Drupal VM
* Drush
* Drupal Console

Platform CLI

Platform CLI must be installed in local machine and virtual machine

```bash
vagrant ssh
cd home/vagrant        
curl -sS`[`https://platform.sh/cli/installer`](https://platform.sh/cli/installer\)` | php  
chmod 777 .platformsh  
curl -sS `[`https://platform.sh/cli/installer`]\(https://platform.sh/cli/installer)`| php        
source ~/.profile
platform
```





