# laravel-azure-storage

Microsoft Azure Blob Storage integration for Laravel's Storage API


# Requirements
- Laravel 5.6

# Installation

Install the package using composer:

```bash
composer require feilongcui/laravel-azure-storage
```

Then add this to the `disks` section of `config/filesystems.php`:

```php
    'azure' => [
        'driver'    => 'azure',
        'name'      => env('AZURE_ACCOUNT_NAME'),
        'key'       => env('AZURE_ACCOUNT_KEY'),
        'container' => env('AZURE_CONTAINER_NAME'),
    ],
```

Finally, add the fields `AZURE_ACCOUNT_NAME`, `AZURE_ACCOUNT_KEY` and `AZURE_CONTAINER_NAME` to your `.env` file with the appropriate credentials. Then you can set the `azure` driver as either your default or cloud driver and use it to fetch and retrieve files as usual.

Constructing a URL
------------------

This driver doesn't support the `Storage::url($path)` method, and adding support as a third-party package doesn't appear to be practical. However, you can construct a URL to retrieve the asset as follows:

```php
$url = 'https://' . config('filesystems.disks.azure.name'). '.blob.core.windows.net/' . config('filesystems.disks.azure.container') . '/' . $filename;
```

You may want to create a helper function for this.
