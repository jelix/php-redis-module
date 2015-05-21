This is a module for Jelix, providing a plugin for jKVDb.

This plugin allows to access to a Redis database through jKVDb.
It uses the library [php-redis](https://github.com/sash/php-redis) (a bit patched).

This module is for Jelix 1.7.x and higher. See the jelix/jelix repository to see
its history before Jelix 1.7.

## installation

Install it by hands like any other Jelix modules, or use Composer if you installed
Jelix 1.7+ with Composer.

In your project:

```
composer require "jelix/minify-module"
```

Then declare the module into the configuration of your application

```ini
[modules]

jredis.access=1
```

Then run the installer

```
php your_app/install/installer.php
```

You can use the plugin. Its name is "redis"

## configuration

For the configuration, indicate a @@host@@ and a @@port@@ parameter in the profiles.ini.php
file. Example of a profile:

<code ini>
[jkvdb:myredis]
driver=redis
host = localhost
port = 6379
</code>

This driver supports the @@I@jIKVttl@@ interface.

## unit tests

Unit tests are in Testapp, in the jelix/jelix repository.