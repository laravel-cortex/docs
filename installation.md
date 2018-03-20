# Installation

- [Requirements](#requirements)
- [Installing Cortex](#installing-cortex)
- [Configuration](#configuration)

<a name="requirements"></a>
## Requirements

<a name="installation"></a>
## Installation
Install the package with composer:

```bash
composer require laravel-cortex/cortex
```

Package auto discovery will automatically detect the package.

Cortex ships with a helper command which can set up everything automatically for you.
In terminal, run:

```bash
php artisan cortex:install
```

This command will make a symlink for storage and you can choose if you want to publish assets, views, language and config files and install routes.

<a name="configuration"></a>
## Configuration

The whole idea behind this project is to make it as customizable as possible. The configuration file is very brief. To learn more about configuring Cotex, head over to the [configuration](configuration.md) page.