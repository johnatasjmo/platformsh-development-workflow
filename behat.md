# Behat testing on platform sh

Instructions are similar to the ones on [behat drupal extension](https://behat-drupal-extension.readthedocs.io/en/3.1/localinstall.html)

## Installation

1. Create a separate branch
   ```
   platform checkout PARENT-BRANCH
   platform branch behat
   git commit --allow-empty "branch behat created"
   git push bitbucket
   platform snapshot:create
   ```
2. Add behat.yml file to application root  
   create a file named behat.yml and add it to web app root with the following code

3. ```
   default:
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
         #only on dev001
         base_url: https://baseurl.com
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
4. drupal-extension
   ```
   composer require drupal/drupal-extension
   composer require guzzlehttp/guzzle
   composer config bin-dir
   ```
5. behat --init, be sure folders are created and download commands
   ```
   behat --ini
   behat -dl
   ```
6. Add a simlink and test that works

```
cd ~
ln -s /var/www/drupalvm/drupal/vendor/behat/behat/bin/behat /var/www/drupalvm/drupal/config/behat
cd drupalvm/drupal/config/behat
behat --dl
behat --help
```

## Add a feature

##### Save the following file as homepage.feature

```
Feature: Test DrupalContext
  In order to prove the Behat is working correctly in Drupal VM
  As a developer
  I need to run a simple interface test

  Scenario: Viewing homepage
    Given I am on the homepage
    Then I should see "Welcome to Drupal"
```

##### Writing a test

Pull code and db locally and create scenarios saved as file.feature then test

```
behat
```

##### Test on platform.sh

behat.yml file has a profile for dev001 environment and can be run as:

```
behat --profile master
```



