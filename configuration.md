# Configuration

- [Configuration File](#configuration-file)
- [Configuration Resolvers](#configuration-resolvers)
- [Policies](#policies)

<a name="configuration-file"></a>
## Configuration File

If you did not run the ```cortex:install``` command, you have to publish the config file.
In terminal, run:
```bash
php artisan vendor:publish --provider="\LaravelCortex\Cortex\ServiceProvider" --tag="config"
```

As Cortex is very customizable, you can change many things like route prefix, controllers namespace if you will use your own controllers, middlewares, etc.

Here is a list of options that you'd probably like to update:
- ```routing.url_prefix``` This is a route prefix for Cortex, you can change this to media for example so Cortex will be at yourdomain.localhost/media. Default is ```cortex```.
- ```namespace``` Namespace in your app for custom Cortex classes, like Policies or Config Resolvers
- ```middleware``` An array of middlewares for Cortex routes. Default is ```web```.
- ```policies``` An array of fully qualified class names of policies you'd like to apply.
- ```generate_file_previews``` Whether previews should be generated. Default is ```true```.
- ```preview_generators``` An array of key/value pairs of fully qualified class names of preview generators you'd like to apply and mime types.
- ```preview_dimensions``` An array with width and height for preview images.
- ```storage.disk``` Name of the disk you want to use that is defined in ```filesystems.php``` configuration file. Default is ```public```.
- ```storage.base_dir``` Relative path to the base directory that's being used. Default is ```/```. 
- ```modes``` An array of modes for Cortex. Default is ```default```, or ```popup``` if Cortex is being called from an editor or file chooser.

<a name="configuration-resolvers"></a>
## Configuration Resolvers

Configuration Resolvers are classes that can create dynamic configuration. You can place a fully qualified class name in the configuration file instead of the actual value.

For example, if you want to limit users to specific folders, you'd want to dynamically change ```storage.base_dir```.

```php
'base_dir' => \App\Cortex\ConfigResolvers\BaseDirConfigResolver::class,
```

To create a config resolver, run in terminal:
```bash
php artisan cortex:make:config-resolver BaseDirConfigResolver
```

Which will place ```BaseDirConfigResolver``` under your Cortex namespace.

All config resolvers must have a ```resolve``` method which should return a dynamic configuration value you need.

```php
public function resolve()
{
  return '/' . auth()->user()->id;
}
```

<a name="policies"></a>
## Policies

Next step of configuring Cortex are [Policies](policies.md).