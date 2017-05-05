# Behat testing on platform sh

Instructions are similar to the ones on [behat drupal extension](https://behat-drupal-extension.readthedocs.io/en/3.1/localinstall.html)

## Installation

##### Create a separate branch

```
platform branch behat
git commit --allow-empty "branch behat created"
git push bitbucket
platform snapshot:create
```

##### Add behat.yml file to application root

create a file named behat.yml and add it to web app root with the following code. Add base\_url for specific environments

1. ```
     suites:
       default:
         contexts:
           - FeatureContext
           - Drupal\DrupalExtension\Context\DrupalContext
           - Drupal\DrupalExtension\Context\MinkContext
     extensions:
       Behat\MinkExtension:
         goutte: ~
         selenium2: ~
         #base_url: https://baseurl.com
       Drupal\DrupalExtension:
         blackbox: ~
         api_driver: 'drupal' 
         drush:
           alias: 'local'
         drupal: 
           drupal_root: 'web' 
         region_map:
           footer: "#footer"
   ```

##### add a bash

on platform.sh root folder .environment, add the following command which will create a base\_url for each branch created. In this way, we can run behat on every branch without the need of change base\_url

```
#export parameters to behat.yml by jmo 
export BEHAT_PARAMS='{"extensions" : {"Behat\\MinkExtension" : {"base_url" : "http://'$PLATFORM_ENVIRONMENT'-'$PLATFORM_PROJECT'.us.platform.sh/"}, "Drupal\\DrupalExtension" : {"drush" :   {  "alias":  "@drupal.'$PLATFORM_BRANCH'" }}}}'
cd ~ && behat --config=behat.yml "$@"
```

##### drupal-extension

```
composer require guzzlehttp/guzzle
composer config bin-dir
```

##### run behat --init

```
behat --ini
behat -dl
```

##### Add a simlink and test that works

```
cd ~
ln -s /var/www/drupalvm/drupal/vendor/behat/behat/bin/behat /var/www/drupalvm/drupal/config/behat
cd drupalvm/drupal/config/behat
behat --dl
behat --help
```

## Add a feature

##### Save the following file as homepage.feature inside features folder

```
Feature: Test DrupalContext
  In order to prove the Behat is working correctly in Drupal VM
  As a developer
  I need to run a simple interface test

  Scenario: Viewing homepage
    Given I am on the homepage
    Then I should see "Welcome to Drupal"
```

##### Test on platform.sh or local app root

```
platform build
behat
```



