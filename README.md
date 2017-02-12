Plugins for Jelix to access to Redis through jKVDb (the nosql API of Jelix) and 
jCache.

These plugins are using the library [php-redis](https://github.com/jelix/php-redis),
a pure PHP library to connect to Redis.

You may want to use these plugins if you cannot use Redis plugins provided
into Jelix 1.7+, that use the API of the [Redis extension](https://github.com/phpredis/phpredis).

These plugins are for Jelix 1.7.x and higher. See the jelix/jelix repository to see
their history before Jelix 1.7.

## installation

Install it by hands like any other Jelix plugins, or use Composer if you installed
Jelix 1.7+ with Composer.

In your project:

```
composer require "jelix/php-redis-plugin"
```

You can use the plugins. There name is "redis_php".

## configuration

For the configuration, indicate a ```host``` and a ```port``` parameter 
in the profiles.ini.php file. The ```db``` parameter is optional (default is 0)
and should indicate the number of the database to use into Redis.

Example of profiles:

```ini
; for jkvdb
[jkvdb:myredis]
driver=redis_php
host = localhost
port = 6379
db=3

; for jcache
[jcache:myredis]
driver=redis_php
host = localhost
port = 6379

```

This driver supports the ```jIKVttl``` interface.

Other parameter configuration:

- `key_prefix`: indicate a name in it, and all keys will be prepend by this name
- `key_prefix_flush_method`: when a key_prefix is set, indicates how the flush 
  should be made, as deletion can be very expensive in resources.
  Possible values are 
  - `direct`: keys are directly deleted, one after one. Warning: this can be
    very time expensive. Use it only if you know you are using only few keys.
  - `jcacheredisworker` for a jCache profile, or `jkvdbredisworker` for a jKvDb 
    driver: It pushes the prefix into a 'list' value in Redis. Keys
    then should be delete by an other process/worker. Such worker is provided
    in jelix (see lib/jelix/core-modules/jelix/controllers/redisworker.cmdline.php)
  - `event`: a jelix event is notified (`jCacheRedisFlushKeyPrefix` for jCache,
    or `jKvDbRedisFlushKeyPrefix` for jKvDb). Up to you
    to create a listener that will delete the keys in the manner you want.
    Event parameters: `prefix` indicates the prefix of keys to delete, `profile`
    indicate the jCache/jKvdb to use for the connection.


## unit tests

Unit tests are in Testapp, in the jelix/jelix repository.


