# Safe Haven MFB Laravel package

Safe Haven MFB for your Laravel project made easy

## Installation

You can install the package via composer:

```bash
composer require chedilas/safehaven_mfb
```

Publishing the config file

```bash
php artisan vendor:publish --provider="CheDilas\SafeHaven\SafeHavenServiceProvider" --tag="config"
```

## Usage

```php

use CheDilas\SafeHaven\SafeHaven;

//Create Account
$accountType = "Savings";
$accountName = "Che Dilas Yusuph";
SafeHaven::account()->createAccount($accountType, $accountName, [
    "verified" => true,
    "notes" => ""
]);

```

For more information, please refer to the [package documentation](docs/index.md).

## Automatic API Token Refresh

For seamless and uninterrupted access to API endpoints, it's recommended to integrate an automated mechanism in your Laravel application. This mechanism will be responsible for generating client assertions and subsequently exchanging them for API tokens. By doing so, the API token gets refreshed automatically before it reaches its expiration, ensuring your API interactions remain consistent and uninterrupted. To implement this, simply add the provided script to your Laravel application's cron job configuration

**Step 1**: Import `ApiRequestor` from `CheDilas\SafeHaven`.

```php
use CheDilas\SafeHaven\ApiRequestor;
```

**Step 2**: Update `schedule` in `app/Console/Kernel.php` to refresh the token every 30 minutes.

```php
protected function schedule(Schedule $schedule)
{
    $schedule->call(function () {
        (new ApiRequestor())->token();
    })->everyThirtyMinutes();
}
```

## Contributing

Please see [CONTRIBUTING](CONTRIBUTING.md) for details.

### Security

If you discover any security-related issues, please email josephdilas@gmail.com instead of using the issue tracker.

## License

The MIT License (MIT). Please see [License File](LICENSE.md) for more information.
