Config manager for open-admin
========================

[![StyleCI](https://styleci.io/repos/97900916/shield?branch=main)](https://styleci.io/repos/97900916)
[![Packagist](https://img.shields.io/github/licence/open-admin-org/config.svg?style=flat-square&color=brightgreen)](https://packagist.org/packages/open-admin-ext/config)
[![Total Downloads](https://img.shields.io/packagist/dt/open-admin-ext/config.svg?style=flat-square)](https://packagist.org/packages/open-admin-ext/config)
[![Pull request welcome](https://img.shields.io/badge/pr-welcome-green.svg?style=flat-square&color=brightgreen)]()


[Documentation](http://open-admin.org/docs/en/extension-config)

## Screenshot

![wx20170810-100226](https://user-images.githubusercontent.com/1479100/29151322-0879681a-7db3-11e7-8005-03310686c884.png)

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
