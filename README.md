[![Latest Stable Version](https://poser.pugx.org/tomgrohl/laravel-memory-auth-provider/v/stable)](https://packagist.org/packages/tomgrohl/laravel-memory-auth-provider)
[![Latest Unstable Version](https://poser.pugx.org/tomgrohl/laravel-memory-auth-provider/v/unstable)](https://packagist.org/packages/tomgrohl/laravel-memory-auth-provider)
[![License](https://poser.pugx.org/tomgrohl/laravel-memory-auth-provider/license)](https://packagist.org/packages/tomgrohl/laravel-memory-auth-provider)

# Laravel Memory Auth Provider

A In Memory User Auth Provider for Laravel 5.1+.

Allows you to Authenticate and admin area without the need for a database. 
Great as a quick and temporary solution during development, 
particularly if your site is mocked out and not let using a database.


## Installation

You can install it using composer:

`composer require tomgrohl/laravel-memory-auth-provider`


## Configuration

### 1 .Add service provider

Add the following to your `providers` in the `app` config

```php
<?php

return [
    
    //...
    
    'providers' => [
        //...    
        'Tomgrohl\Laravel\Auth\AuthServiceProvider',
        
        // OR
        \Tomgrohl\Laravel\Auth\AuthServiceProvider::class,
    ]
    
    
];

```

### 2. Setup config

In the `auth` config you will need to set the driver:

```
    'driver' => 'memory',
```

Add also setup your in memory users:

```
    'memory' => [
        'model' => 'Illuminate\Auth\GenericUser',
        'users' => [
    
            'admin' => [
                'id' => 1,
                // Hashed passord using the hasher service
                'password' => '$2y$10$Mfusxb1546MFxQ4A1s4GE.OF/gFuI8Y6Hw9xnlZeiHtjDl0/pnXPK',
            ],
        ],
    ],
```

You can add any properties you want making it easy to switch out the Auth drivers.

The package comes with a command for hashing passwords, making it easier to setup passwords, just run the following command to hash your password:

```
php artisan tomgrohl:hash:password mypassword
```