Checking PHP code with code sniffer

Developers must code using Drupal standard codes, coder sniffer helps to check php code from developers. PHP coder sniffer commands must be used in local machine.

https://www.drupal.org/node/1419988

on app root

```
composer global require drupal/coder
```

Registed drupal best practices

```
phpcs --config-set installed_paths ~/drupalvm/drupal/vendor/coder/coder_sniffer
```

check that works, restult m

```
cd /web/modules/custom
phpcs -i
```

Result expected is

```
$ The installed coding standards are MySource, PEAR, PHPCS, PSR1, PSR2, Squiz and Zend
```



