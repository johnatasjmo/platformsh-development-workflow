Drupal Console

### Instructions on how to install Drupal console are in:

[https://docs.drupalconsole.com/en/getting/composer.html](https://docs.drupalconsole.com/en/getting/composer.html)

### Drupal console must be installed as Global and as Composer

[https://docs.drupalconsole.com/en/getting/launcher.html](https://docs.drupalconsole.com/en/getting/launcher.html)

### Troubleshooting

##### Clear cache

```
cd /var/www/drupalvm/drupal/web && ../vendor/drupal/console/bin/drupal cr all
```

##### Fix permissions on drupalvm

    sudo chown -R `whoami`:admin /usr/local/bin
    sudo chown -R `whoami`:admin /usr/local/share



