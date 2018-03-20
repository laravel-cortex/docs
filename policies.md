# Policies

- [Default Policies](#default-policies)
- [Creating Policies](#creating-policies)
- [Use Cases](#use-cases)

Policies are classes that guard access to specific paths. You can guard read, write and delete actions and apply your own rules to restrict those actions.

Note that all paths are relative to your storage path.

<a name="default-policies"></a>
## Default Policies

Default Policies are:

```php
[
  LaravelCortex\Cortex\Policies\HidePreviewDirectoriesPolicy::class,
  LaravelCortex\Cortex\Policies\DiscardDoubleDotsPolicy::class,
]
```

```HidePreviewDirectoriesPolicy``` hides preview directories from the file list.
```DiscardDoubleDotsPolicy``` blocks any action if the path contains double dots (```/../```) for secutiry purposes.

<a name="creating-policies"></a>
## Creating Policies

To create your own Policy, run in terminal:
```bash
php artisan cortex:make:policy MyPolicy
```

Which will create a policy under your Cortex namespace.

<a name="use-cases"></a>
## Use Cases

For example if you want to restrict access to ```admin``` folder if a user is not an admin, you would create rules like this:

```php
protected function isAllowed(){
  if(starts_with($this->path, '/admin')){
    return auth()->user()->is_admin;
  }
  return true;
}

protected function read() : bool
{
    return $this->isAllowed();
}

protected function write() : bool
{
    return $this->isAllowed();
}

protected function delete() : bool
{
    return $this->isAllowed();
}
```

You might also want to restrict types of files that are displayed for example in popup mode. If you want to display only images if current mode is ```popup```, you would create rules like this:

```php
protected function read() : bool
{
  if(Input::get('mode') !== 'popup'){
    return true; // Allow if not in popup mode
  }
  $file = new \LaravelCortex\Cortex\Library\File($this->path);
  return $file->mime_type === 'folder' || starts_with($file->mime_type, 'image/');
}
```