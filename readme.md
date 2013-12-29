## Description

This project is to demonstrate [phpseclib issue #217](https://github.com/phpseclib/phpseclib/pull/217).

### Steps

- Install laravel

`composer create-project laravel/laravel --prefer-dist phpseclib-demo`

- Create package workbench

`./artisan workbench --resources sumardi/phpseclibtest`

- Edit `/workbench/sumardi/phpseclibtest/composer.json`

```
...
"require": {
    "php": ">=5.3.0",
    "phpseclib/phpseclib": "dev-master"
},
...
```

- Run `composer install` in the package workbench

```
cd workbench/sumardi/phpseclibtest
composer install
```

- Open the page and fatal error.

`Fatal error: Cannot redeclare crypt_random_string()`

### Call stack

```
Call Stack
#	Time	Memory	Function	Location
1	0.0008	648232	{main}( )	../index.php:0
2	0.0010	657400	require( 'phpseclib-demo/bootstrap/autoload.php' )	../index.php:21
3	0.0083	2004928	Illuminate\Workbench\Starter::start( )	../autoload.php:74
4	0.0194	3405304	Illuminate\Filesystem\Filesystem->requireOnce( )	../Starter.php:29
5	0.0195	3408368	require_once( 'phpseclib-demo/workbench/sumardi/phpseclibtest/vendor/autoload.php' )	../Filesystem.php:70
6	0.0196	3434600	ComposerAutoloaderInitb05f640e14d21ed9bdcfc08f7640821b::getLoader( )	../autoload.php:7
```