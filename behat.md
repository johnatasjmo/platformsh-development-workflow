# Behat testing on platform sh

Instructions are similar to the ones on [behat drupal extension](https://behat-drupal-extension.readthedocs.io/en/3.1/localinstall.html)

### Installation

1. Create a separate branch
   ```
   platform checkout PARENT-BRANCH
   platform branch behat
   git commit --allow-empty "branch behat created"
   git push bitbucket
   platform snapshot:cre
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
   behatndor/bin/
   ```



Features as shared

* modify .platform.yml file and add features folder as a mount file
* on app root type 

```

```

Testing locally

Testing on server

