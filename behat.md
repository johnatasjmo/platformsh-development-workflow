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

   ```
4. drupal-extension
   ```
   composer require drupal/drupal-extension
   composer require guzzlehttp/guzzle
   composer config bin-dir
   ```
5. behat --init, be sure folders are created
   ```
   behat --ini
   ```
6. add a feature  
   Add a simple feature, copy content of below code and save it into /features folder as .yml

7. ```

   ```
8. behat -dl

   ```

   ```

9. run vendor/bin/behat

   ```

   ```

Features as shared

* modify .platform.yml file and add features folder as a mount file
* on app root type 

```

```

Testing locally

Testing on server

