# Scritps

### Script for create a local branch

1. Add a file named branching.sh with below code into project root /drupal
2. From drupalVM type the new branch name you would like to create. Example: child-branch

```
$sh branching child-branch
```

##### Script

    #!/bin/bash
    # Scritp to branch from platform master, create a local branch, pull db
    # As per github flow, create a branch with own environment
    # $sh branching.sh child-branch
    # be sure to have git config --global push.default simple

    TIMESTAMP=`date "+%Y-%m-%d %H:%M:%S"`

    echo "*** start branching at $TIMESTAMP"
    unset $(git rev-parse --local-env-vars)
    echo " *** master check out"
    platform checkout master
    echo "creating snapshot of master"
    platform snapshot:create
    echo "*** create branch" $1
    platform branch $1
    echo "*** branch created" 
    git commit --allow-empty -m "branch created"
    echo "*** push branch to origin"
    git push bb
    echo "*** setting bb as upstream"
    git branch -u bb/$1
    echo "create snapshot after 30s while platform builds"
    sleep 30s
    platform snapshot:create
    platform

    echo "*** drush clear"
    drush cc drush 
    echo "*** drush droping db"
    drush @drupal._local sql-drop --yes
    echo "drush *** sync localdb with platform"
    TIMESTAMP=`date "+%Y-%m-%d %H:%M:%S"`
    echo "Waiting for platform to create snapshot at $TIMESTAMP"
    sleep 80s
    drush sql-sync @drupal.$1 @drupal._local -y
    echo "*** starting build"
    platform build
    echo "*** finishing build"
    drush @drupal._local cr
    TIMESTAMP=`date "+%Y-%m-%d %H:%M:%S"`
    echo "$TIMESTAMP"
    echo "*** branch created in local, bitbucket and platform"
    echo "*** branching finished ***"

### Script for automatic snapshots using AWS EC2 nano instance

Follow the next steps for creating automatic snapshots

* Create an EC2 instance as nano instance
* Install php on EC2
* Install git on EC2
* Install platform on EC2 and use `platform get` to get the project

Save this file on /home/ec2-user and name it script.sh

```
cd  /home/ec2-user/drupal/web
~/.platformsh/bin/platform checkout master
~/.platformsh/bin/platform snapshot:create
```

make script executable

```
$ chmod a+x script.sh
```

set cron to run

```
$ crontab -e
```

Edit the file with the following commands

```
*****test every 5 min
*/5 * * * * /bin/bash /home/ec2-user/script.sh >> /var/tmp/out.log 2>&1

*** every 3 hours ****
0 */3 * * * /bin/bash /home/ec2-user/script.sh >> /var/tmp/out.log 2>&1
```



