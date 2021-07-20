Config manager for open-admin
========================

[![StyleCI](https://styleci.io/repos/387844084/shield?branch=main)](https://styleci.io/repos/387844084)
[![Packagist](https://img.shields.io/github/license/open-admin-org/config?style=flat-square&color=brightgreen)](https://packagist.org/packages/open-admin-ext/config)
[![Total Downloads](https://img.shields.io/packagist/dt/open-admin-ext/config?style=flat-square)](https://packagist.org/packages/open-admin-ext/config)
[![Pull request welcome](https://img.shields.io/badge/pr-welcome-green?style=flat-square&color=brightgreen)]()


[Documentation](http://open-admin.org/docs/en/extension-config)

## Screenshot

![config screenshot](https://open-admin.org/docs/images/screenshots/ext-config.png)

## Installation

```
$ composer require open-admin-ext/config

$ php artisan migrate
```

Open `app/Providers/AppServiceProvider.php`, and call the `Config::load()` method within the `boot` method:

```php
<?php

namespace App\Providers;

use OpenAdmin\Admin\Config\Config;
use Illuminate\Support\Facades\Schema;
use Illuminate\Support\ServiceProvider;

class AppServiceProvider extends ServiceProvider
{
    public function boot()
    {
        $table = config('admin.extensions.config.table', 'admin_config');
        if (Schema::hasTable($table)) {
            Config::load();
        }
    }
}
```

Then run: 

```
$ php artisan admin:import config
```

Open `http://your-host/admin/config`

## Usage

After add config in the panel, use `config($key)` to get value you configured.

License
------------
Licensed under [The MIT License (MIT)](LICENSE).
