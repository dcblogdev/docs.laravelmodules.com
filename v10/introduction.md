---
title: Introduction
---

`nwidart/laravel-modules` is a Laravel package which was created to manage your large Laravel app using modules. A module is like a Laravel package, it has some views, controllers or models. This package is supported and tested in Laravel 10.

Find out why you should use this package in the article: [Writing modular applications with laravel-modules](https://nicolaswidart.com/blog/writing-modular-applications-with-laravel-modules).

> Heads up:
    If you upgrade to v6 from previous version, run the following command: `php artisan module:v6:migrate`

## Upgrading from v8.3.0

If you have an existing config file, and you get an error:
```bash
Target class [CommandMakeCommand] does not exist
```
Then the config file will need updating first import the commands class:

```php
use Nwidart\Modules\Commands;
```

Next replace the commands array with:

```php
'commands' => [
    Commands\CommandMakeCommand::class,
    Commands\ComponentClassMakeCommand::class,
    Commands\ComponentViewMakeCommand::class,
    Commands\ControllerMakeCommand::class,
    Commands\ChannelMakeCommand::class,
    Commands\DisableCommand::class,
    Commands\DumpCommand::class,
    Commands\EnableCommand::class,
    Commands\EventMakeCommand::class,
    Commands\FactoryMakeCommand::class,
    Commands\JobMakeCommand::class,
    Commands\ListenerMakeCommand::class,
    Commands\MailMakeCommand::class,
    Commands\MiddlewareMakeCommand::class,
    Commands\NotificationMakeCommand::class,
    Commands\ObserverMakeCommand::class,
    Commands\PolicyMakeCommand::class,
    Commands\ProviderMakeCommand::class,
    Commands\InstallCommand::class,
    Commands\LaravelModulesV6Migrator::class,
    Commands\ListCommand::class,
    Commands\ModuleDeleteCommand::class,
    Commands\ModuleMakeCommand::class,
    Commands\MigrateCommand::class,
    Commands\MigrateFreshCommand::class,
    Commands\MigrateRefreshCommand::class,
    Commands\MigrateResetCommand::class,
    Commands\MigrateRollbackCommand::class,
    Commands\MigrateStatusCommand::class,
    Commands\MigrationMakeCommand::class,
    Commands\ModelMakeCommand::class,
    Commands\ResourceMakeCommand::class,
    Commands\RequestMakeCommand::class,
    Commands\RuleMakeCommand::class,
    Commands\RouteProviderMakeCommand::class,
    Commands\PublishCommand::class,
    Commands\PublishConfigurationCommand::class,
    Commands\PublishMigrationCommand::class,
    Commands\PublishTranslationCommand::class,
    Commands\SeedCommand::class,
    Commands\SeedMakeCommand::class,
    Commands\SetupCommand::class,
    Commands\TestMakeCommand::class,
    Commands\UnUseCommand::class,
    Commands\UpdateCommand::class,
    Commands\UseCommand::class,
],
```

### Quick Example

Generate your first module using `php artisan module:make Blog`. The following structure will be generated.

```
Modules/
  ├── Blog/
      ├──app
          ├── Http/
          ├── Models/
              ├── Controllers/
              ├── Middleware/
              ├── Requests/
          ├── Providers/
              ├── BlogServiceProvider.php
              ├── RouteServiceProvider.php
     ├── config/
     ├── database/
          ├── factories/
          ├── migrations/
          ├── seeders/
      ├── lang
      ├── resources/
          ├── assets/
          ├── views/
      ├── routes/
          ├── api.php
          ├── web.php
      ├── tests/
      ├── composer.json
      ├── module.json
      ├── package.json
      ├── vite.config.js
```
