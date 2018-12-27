# laravel-postal-code-validation
Postal code validation for Laravel

![Build status](https://travis-ci.org/axlon/laravel-postal-code-validation.svg?branch=master)

## Installation
You can install this package with Composer, by running the command below:

```bash
composer require axlon/laravel-postal-code-validation
```

### Laravel 5.5+
If you are running Laravel 5.5 or higher, package discovery will automatically register the package for you after
running the Composer command.

### Laravel 5.4 and below
If you are running a Laravel version lower than 5.5, register the package by adding the service provider to the
providers array in your `config/app.php` file:

```php
'providers' => [
   ...
   Axlon\PostalCodeValidation\ValidationServiceProvider::class,
   ...
],
```

### Lumen
If you are running Lumen, register the package by adding the following line to your `bootstrap/app.php` file:

```php
$app->register(Axlon\PostalCodeValidation\ValidationServiceProvider::class);
```

## Usage
Postal code validation perfectly integrates into your Laravel application, you can use it just like you would any
framework validation rule.

### Using the rule as a string
You can call the rule as part of your validation string (see example below). The rule expects at least one country code
to validate against.

```php
$this->validate($request, [
    'postal_code' => 'postal_code:NL,BE',
]);
```

### Using the rule directly
If you prefer a more object-like style, that's available too (see example below).

```php
$this->validate($request, [
    'postal_code' => [
        PostalCode::forCountry('NL')->andCountry('BE'),
    ],
]);
```

### Adding an error message
To add an error message your users will be able to understand, open `resources/lang/{your language}/validation.php` and
add the following line to it:

```php
'postal_code' => 'The :attribute field must be a valid postal code.',
```

## Special thanks
Special thanks to [sirprize](https://github.com/sirprize), the author of the underlying postal code validation library.

## Contributing
This is a small and straight forward package, but if you spot a bug or see room for improvement, create an issue or a
pull request and I will try to respond within a few days
