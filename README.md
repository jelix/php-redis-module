This is a plugin for jKVDb, the nosql API of Jelix.

This plugin allows to access to a Redis database through jKVDb.
It uses the library [php-redis](https://github.com/jelix/php-redis).

This plugin is for Jelix 1.7.x and higher. See the jelix/jelix repository to see
its history before Jelix 1.7.

## installation

Install it by hands like any other Jelix plugins, or use Composer if you installed
Jelix 1.7+ with Composer.

In your project:

```
composer require "jelix/php-redis-plugin"
```

You can use the plugin. Its name is "redis".

## configuration

For the configuration, indicate a ```host``` and a ```port``` parameter in the profiles.ini.php
file. Example of a profile:

```ini
[jkvdb:myredis]
driver=redis
host = localhost
port = 6379
```

This driver supports the ```jIKVttl``` interface.

## unit tests

Unit tests are in Testapp, in the jelix/jelix repository.


