---
title: Configuration
---


You can publish the package configuration using the following command:

```bash
php artisan vendor:publish --provider="Nwidart\Modules\LaravelModulesServiceProvider"
```

In the published configuration file you can configure the following things:

## Default namespace

What the default namespace will be when generating modules.

Default: `Modules`

The default namespace is set as Modules this will apply the namespace for all classes the module will use when it's being created and later when generation additional classes.

## Overwrite the generated files (stubs)

Overwrite the default generated stubs to be used when generating modules. This can be useful to customise the output of different files.

These stubs set options and paths.

Enabled true or false will enable or disable a module upon creation, the default is false meaning you will have to enable a module manually. 

To enable a module edit **module_statuses.json** or run the command:

```php
php artisan module:enable ModuleName
```

> note the module_statues.json file will be created if it does not exist using this command.

The contents of module_statuses.json looks like:

```php
{
    "Users": true
}
```

> The above would be when there is a single module called Users and is enabled.

Path points to a vendor directly where the default stubs are located, these can be published and modified.

Files set the file locations defaults.

Replacements is a way to do a Find and Replace on generation any matches will be replaced.

```php
'stubs' => [
    'enabled' => false,
    'path' => base_path() . '/vendor/nwidart/laravel-modules/src/Commands/stubs',
    'files' => [
        'routes/web' => 'Routes/web.php',
        'routes/api' => 'Routes/api.php',
        'views/index' => 'Resources/views/index.blade.php',
        'views/master' => 'Resources/views/layouts/master.blade.php',
        'scaffold/config' => 'Config/config.php',
        'composer' => 'composer.json',
        'assets/js/app' => 'Resources/assets/js/app.js',
        'assets/sass/app' => 'Resources/assets/sass/app.scss',
        'webpack' => 'webpack.mix.js',
        'package' => 'package.json',
    ],
    'replacements' => [
        'routes/web' => ['LOWER_NAME', 'STUDLY_NAME'],
        'routes/api' => ['LOWER_NAME'],
        'webpack' => ['LOWER_NAME'],
        'json' => ['LOWER_NAME', 'STUDLY_NAME', 'MODULE_NAMESPACE', 'PROVIDER_NAMESPACE'],
        'views/index' => ['LOWER_NAME'],
        'views/master' => ['LOWER_NAME', 'STUDLY_NAME'],
        'scaffold/config' => ['STUDLY_NAME'],
        'composer' => [
            'LOWER_NAME',
            'STUDLY_NAME',
            'VENDOR',
            'AUTHOR_NAME',
            'AUTHOR_EMAIL',
            'MODULE_NAMESPACE',
            'PROVIDER_NAMESPACE',
        ],
    ],
    'gitkeep' => true,
],
```

## Generator Path

By default, these are the files that are generated by default where generate is set to true, when false is used that path is not generated.

Don't like Entities for the Models here's where you can change the path to Models instead.

```php
'generator' => [
    'config' => ['path' => 'Config', 'generate' => true],
    'command' => ['path' => 'Console', 'generate' => true],
    'migration' => ['path' => 'Database/Migrations', 'generate' => true],
    'seeder' => ['path' => 'Database/Seeders', 'generate' => true],
    'factory' => ['path' => 'Database/factories', 'generate' => true],
    'model' => ['path' => 'Entities', 'generate' => true],
    'routes' => ['path' => 'Routes', 'generate' => true],
    'controller' => ['path' => 'Http/Controllers', 'generate' => true],
    'filter' => ['path' => 'Http/Middleware', 'generate' => true],
    'request' => ['path' => 'Http/Requests', 'generate' => true],
    'provider' => ['path' => 'Providers', 'generate' => true],
    'assets' => ['path' => 'Resources/assets', 'generate' => true],
    'lang' => ['path' => 'Resources/lang', 'generate' => true],
    'views' => ['path' => 'Resources/views', 'generate' => true],
    'test' => ['path' => 'Tests/Unit', 'generate' => true],
    'test-feature' => ['path' => 'Tests/Feature', 'generate' => true],
    'repository' => ['path' => 'Repositories', 'generate' => false],
    'event' => ['path' => 'Events', 'generate' => false],
    'listener' => ['path' => 'Listeners', 'generate' => false],
    'policies' => ['path' => 'Policies', 'generate' => false],
    'rules' => ['path' => 'Rules', 'generate' => false],
    'jobs' => ['path' => 'Jobs', 'generate' => false],
    'emails' => ['path' => 'Emails', 'generate' => false],
    'notifications' => ['path' => 'Notifications', 'generate' => false],
    'resource' => ['path' => 'Transformers', 'generate' => false],
    'component-view' => ['path' => 'Resources/views/components', 'generate' => false],
    'component-class' => ['path' => 'View/Component', 'generate' => false],
]
```

## Package Commands

The commands you can run is determined from this list. Any commands you don't want to use can be commented out / removed from this list and will not then be available when running `php artisan`.

```php
'commands' => [
    Commands\CommandMakeCommand::class,
    Commands\ComponentClassMakeCommand::class,
    Commands\ComponentViewMakeCommand::class,
    Commands\ControllerMakeCommand::class,
    Commands\DisableCommand::class,
    Commands\DumpCommand::class,
    Commands\EnableCommand::class,
    Commands\EventMakeCommand::class,
    Commands\JobMakeCommand::class,
    Commands\ListenerMakeCommand::class,
    Commands\MailMakeCommand::class,
    Commands\MiddlewareMakeCommand::class,
    Commands\NotificationMakeCommand::class,
    Commands\ProviderMakeCommand::class,
    Commands\RouteProviderMakeCommand::class,
    Commands\InstallCommand::class,
    Commands\ListCommand::class,
    Commands\ModuleDeleteCommand::class,
    Commands\ModuleMakeCommand::class,
    Commands\FactoryMakeCommand::class,
    Commands\PolicyMakeCommand::class,
    Commands\RequestMakeCommand::class,
    Commands\RuleMakeCommand::class,
    Commands\MigrateCommand::class,
    Commands\MigrateRefreshCommand::class,
    Commands\MigrateResetCommand::class,
    Commands\MigrateRollbackCommand::class,
    Commands\MigrateStatusCommand::class,
    Commands\MigrationMakeCommand::class,
    Commands\ModelMakeCommand::class,
    Commands\PublishCommand::class,
    Commands\PublishConfigurationCommand::class,
    Commands\PublishMigrationCommand::class,
    Commands\PublishTranslationCommand::class,
    Commands\SeedCommand::class,
    Commands\SeedMakeCommand::class,
    Commands\SetupCommand::class,
    Commands\UnUseCommand::class,
    Commands\UpdateCommand::class,
    Commands\UseCommand::class,
    Commands\ResourceMakeCommand::class,
    Commands\TestMakeCommand::class,
    Commands\LaravelModulesV6Migrator::class,
    Commands\ComponentClassMakeCommand::class,
    Commands\ComponentViewMakeCommand::class,
],
```

## Overwrite the paths

Overwrite the default paths used throughout the package.

Set the path for where to place the Modules folder, where the assets will be published and the location for the migrations.

> It's recommend keep the defaults here.

```php
'paths' => [
    'modules' => base_path('Modules'),
    'assets' => public_path('modules'),
    'migration' => base_path('database/migrations'),
```

## Scan additional folders for modules

By default, modules are loaded from a directory called Modules, in addition to the scan path.  Any packages installed for modules can be loaded from here.

```php
'scan' => [
    'enabled' => false,
    'paths' => [
        base_path('vendor/*/*'),
    ],
],
```

You can add your own locations for instance say you're building a large application and want to have multiple module folder locations, you can create as many as needed.

```php
'scan' => [
    'enabled' => true,
    'paths' => [
        base_path('ModulesCms'),
        base_path('ModulesERP'),
        base_path('ModulesShop'),
    ],
],
```

> Remember to set enabled too true to enable these locations.

## Composer file template

When generating a module the composer.json file will contain the author details as set out below, change them as needed.

Take special notice of the vendor, if you plan on extracting modules to packages later it's recommend using your BitBucket/GitHub/GitLab vendor name here.

```php
'composer' => [
    'vendor' => 'nwidart',
    'author' => [
        'name' => 'Nicolas Widart',
        'email' => 'n.widart@gmail.com',
    ],
]
```

## Caching

If you have many modules it's a good idea to cache this information (like the multiple `module.json` files for example).

Modules can be cached, by default caching is off.

```php
'cache' => [
    'enabled' => false,
    'key' => 'laravel-modules',
    'lifetime' => 60,
],
```

## Registering custom namespace

Decide which custom namespaces need to be registered by the package. If one is set to false, the package won't handle its registration.