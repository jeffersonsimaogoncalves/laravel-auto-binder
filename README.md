![Laravel Auto Binder](https://user-images.githubusercontent.com/37669560/145568267-0498caf2-fb8a-4715-85ee-6374b8adadc5.png)

# Laravel Auto Binder
[![Latest Version on Packagist](https://img.shields.io/packagist/v/michael-rubel/laravel-auto-binder.svg?style=flat-square&logo=packagist)](https://packagist.org/packages/michael-rubel/laravel-auto-binder)
[![Total Downloads](https://img.shields.io/packagist/dt/michael-rubel/laravel-auto-binder.svg?style=flat-square&logo=packagist)](https://packagist.org/packages/michael-rubel/laravel-auto-binder)
[![Code Quality](https://img.shields.io/scrutinizer/quality/g/michael-rubel/laravel-auto-binder.svg?style=flat-square&logo=scrutinizer)](https://scrutinizer-ci.com/g/michael-rubel/laravel-auto-binder/?branch=main)
[![Code Coverage](https://img.shields.io/scrutinizer/coverage/g/michael-rubel/laravel-auto-binder.svg?style=flat-square&logo=scrutinizer)](https://scrutinizer-ci.com/g/michael-rubel/laravel-auto-binder/?branch=main)
[![GitHub Tests Action Status](https://img.shields.io/github/workflow/status/michael-rubel/laravel-auto-binder/run-tests/main?style=flat-square&label=tests&logo=github)](https://github.com/michael-rubel/laravel-auto-binder/actions)
[![PHPStan](https://img.shields.io/github/workflow/status/michael-rubel/laravel-auto-binder/phpstan/main?style=flat-square&label=larastan&logo=laravel)](https://github.com/michael-rubel/laravel-auto-binder/actions)

> This package automatically binds interfaces to implementations in the Service Container, scanning the specified project folders. This helps avoid manually registering container bindings when the project needs to bind a lot of interfaces to its implementations without any additional dependencies.

One requirement you should follow to use this package:
- Folder with interfaces always should be the child of the folder where it belongs.

For example: `App\Services\YourService => App\Services\Interfaces\YourServiceInterface`

You can customize folders to scan, type of bindings, and the naming convention of your interfaces in the config.

The package requires PHP `^8.x` and Laravel `^8.71`.

[![PHP Version](https://img.shields.io/badge/php-^8.x-777BB4?style=flat-square&logo=php)](https://php.net)
[![Laravel Version](https://img.shields.io/badge/laravel-^8.71-FF2D20?style=flat-square&logo=laravel)](https://laravel.com)
[![Laravel Octane Compatible](https://img.shields.io/badge/octane-compatible-success?style=flat-square&logo=laravel)](https://github.com/laravel/octane)

## Installation
Install the package using composer:
```bash
composer require michael-rubel/laravel-auto-binder
```

Then publish and customize the configuration:
```bash
php artisan vendor:publish --tag="auto-binder-config"
```

## Usage

Edit the config and put your classes and interfaces to the proper folders with proper class naming. That's all.

So, this kind of bindings:
```php
$this->app->bind(AuthServiceInterface::class, AuthService::class);
$this->app->bind(UserServiceInterface::class, UserService::class);
$this->app->bind(CompanyServiceInterface::class, CompanyService::class);
...
```

Or provider's array:
```php
public array $singletons = [
    AuthServiceInterface::class    => AuthService::class,
    UserServiceInterface::class    => UserService::class,
    CompanyServiceInterface::class => CompanyService::class,
    ...
];
```

Will be registered automatically for you.

## Testing
```bash
composer test
```
