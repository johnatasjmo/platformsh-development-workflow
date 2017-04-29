Checking PHP code with code sniffer

Developers must code using Drupal standard codes, coder sniffer helps to check php code from developers. PHP coder sniffer commands must be used in local machine.

[https://www.drupal.org/node/1419988](https://www.drupal.org/node/1419988)

on app root

```
composer global require drupal/coder
phpcs --config-set installed_paths ~/.composer/vendor/drupal/coder/coder_sniffer
```

check installation

```
composer global show -P
```

check that works, restult m

```
cd /web/modules/custom
phpcs -i
```

Result expected is

```
$ The installed coding standards are PHPCS, MySource, Squiz, PEAR, Zend, PSR1, PSR2, Drupal and DrupalPractice
```

# Usage

check module

```
phpcs --standard=DrupalPractice --extensions=php,module,inc,install,test,profile,theme,css,info,txt,md web/modules/custom/aftership_entity
```

check file

```
phpcs --standard=Drupal example.module
```

correct file

```
phpcbf --standard=Drupal --extensions=php,module,inc,install,test,profile,theme,css,info,txt,md /file/to/drupal/example_module
```



