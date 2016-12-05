# A fluent builder Schema.org types and ld+json generator

[![Latest Version on Packagist](https://img.shields.io/packagist/v/spatie/schema-org.svg?style=flat-square)](https://packagist.org/packages/spatie/schema-org)
[![Software License](https://img.shields.io/badge/license-MIT-brightgreen.svg?style=flat-square)](LICENSE.md)
[![Build Status](https://img.shields.io/travis/spatie/schema-org/master.svg?style=flat-square)](https://travis-ci.org/spatie/schema-org)
[![SensioLabsInsight](https://img.shields.io/sensiolabs/i/xxxxxxxxx.svg?style=flat-square)](https://insight.sensiolabs.com/projects/xxxxxxxxx)
[![Quality Score](https://img.shields.io/scrutinizer/g/spatie/schema-org.svg?style=flat-square)](https://scrutinizer-ci.com/g/spatie/schema-org)
[![Total Downloads](https://img.shields.io/packagist/dt/spatie/schema-org.svg?style=flat-square)](https://packagist.org/packages/spatie/schema-org)

`spatie/schema-org` provides a fluent builder for **all** Schema.org types and their properties. The code in `src` is generated from Schema.org's [RFDa standards file](https://github.com/schemaorg/schemaorg/blob/sdo-callisto/data/schema.rdfa), so it provides objects and methods for the entire core vocabulary. The classes and methods are also fully documented as a quick reference.

```php
use Spatie\SchemaOrg\Schema;

$localBusiness = Schema::localBusiness()
    ->name('Spatie')
    ->email('info@spatie.be')
    ->contactPoint(Schema::contactPoint()->areaServed('Worldwide'));

$localBusiness->toScript();
```

```html
<script type="application/ld+json">
{
    "@context": "http:\/\/schema.org",
    "@type": "LocalBusiness",
    "name": "Spatie",
    "email": "info@spatie.be",
    "contactPoint": {
        "@type":"ContactPoint",
        "areaServed":"Worldwide"
    }
}
</script>
```

## Postcardware

You're free to use this package (it's [MIT-licensed](LICENSE.md)), but if it makes it to your production environment we highly appreciate you sending us a postcard from your hometown, mentioning which of our package(s) you are using.

Our address is: Spatie, Samberstraat 69D, 2060 Antwerp, Belgium.

The best postcards will get published on the open source page on our website.

## Installation

You can install the package via composer:

``` bash
composer require spatie/schema-org
```

## Usage

All types can be instantiated though the `Spatie\SchemaOrg\Schema` factory class, or with the `new` keyword.

``` php
$localBusiness = Schema::localBusiness()->name('Spatie');

// Is equivalent to:

$localBusiness = new LocalBusiness();
$localBusiness->name('Spatie'); 
```

Types can be rendered to a script, or converted to an array (which contains the same data as the json in the script).

```php
$localBusiness->toScript();

$localBusiness->toArray();
```

### Advanced usage

If you'd need to set a custom property, you can use the `setProperty` method.

```php
$localBusiness->setProperty('foo', 'bar');
```

If you'd need to retrieve a property, you can use the `getProperty` method. You can optionally pass in a second parameter to provide a default value. 

```php
$localBusiness->getProperty('name'); // 'Spatie'
$localBusiness->getProperty('bar'); // null
$localBusiness->getProperty('bar', 'baz'); // 'baz'
```

All properties can be retrieved as an array with the `getProperties` method.

```php
$localBusiness->getProperties(); // ['name' => 'Spatie', ...]
```

Context and type can be retrieved with the `getContext` and `getType` methods.

```php
$localBusiness->getContext(); // 'http://schema.org'
$localBusiness->getType(); // 'LocalBusiness'
```

## Changelog

Please see [CHANGELOG](CHANGELOG.md) for more information what has changed recently.

## Testing

``` bash
$ composer test
```

## Contributing

Please see [CONTRIBUTING](CONTRIBUTING.md) for details.

## Security

If you discover any security related issues, please email freek@spatie.be instead of using the issue tracker.

## Credits

- [Sebastian De Deyne](https://github.com/sebastiandedeyne)
- [All Contributors](../../contributors)

## About Spatie
Spatie is a webdesign agency based in Antwerp, Belgium. You'll find an overview of all our open source projects [on our website](https://spatie.be/opensource).

## License

The MIT License (MIT). Please see [License File](LICENSE.md) for more information.