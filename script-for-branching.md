Scritps

Script for create a local branch

Add a file named branching.sh with below code into project root /drupal

From drupalVM type the new branch name you would like to create. Example: child-branch

```
$sh branching child-branch
```

Script

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
    drush cr @drupal._local
    TIMESTAMP=`date "+%Y-%m-%d %H:%M:%S"`
    echo "$TIMESTAMP"
    echo "*** branch created in local, bitbucket and platform"
    echo "*** branching finished ***"



