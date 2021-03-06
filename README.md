# Unofficial PHP SDK for Skyscanner's API

[![Latest Version on Packagist][ico-version]][link-packagist]
[![Software License][ico-license]](LICENSE.md)
[![Build Status][ico-travis]][link-travis]
[![Total Downloads][ico-downloads]][link-downloads]

This is an unofficial PHP SDK for the [Skyscanner's API](http://business.skyscanner.net/portal/en-GB/Documentation/ApiOverview)
to support Flights, Car Hire and Hotels services.

Currently, only the Flights service is implemented.

## Install

Via Composer

``` bash
$ composer require ozdemirburak/skyscanner-php
```

## Usage

Please see the **[wiki](https://github.com/ozdemirburak/skyscanner-php/wiki)** for more detailed information about the methods and the parameters.
 
You can find a simple demonstration of how to use the methods below, or check the
[tests](tests/) for more advanced examples.

### Flights: Live Pricing

``` php
use OzdemirBurak\SkyScanner\Travel\Flights\LivePricing;

$pricing = new LivePricing($apiKey = 'your-api-key', $country = 'GB', $currency = 'GBP', $locale = 'en-GB');
$pricing->setParameters([
    'adults' => 1,
    'destinationplace' => 'IST',
    'originplace' => 'LHR',
    'outbounddate' => date('Y-m-d', strtotime('+1 week')),
    'stops' => 0
]);
$flights = $pricing->parseFlights($onlyCheapestAgentPerItinerary = true);
```

### Flights: BrowseCache

``` php
use OzdemirBurak\SkyScanner\Travel\Flights\BrowseCache;

$cache = new BrowseCache($apiKey = 'your-api-key', $country = 'GB', $currency = 'GBP', $locale = 'en-GB');
$cache->setParameters([
    'destinationPlace' => 'IST',
    'originPlace' => 'LHR',
    'outboundPartialDate' => date('Y-m-d', strtotime('+1 week')),
]);
$quotes = $cache->getData('browsequotes');
```
    
## Change log

Please see [CHANGELOG](CHANGELOG.md) for more information what has changed recently.

## Testing

``` bash
$ composer test
```

## Contributing

Please see [CONTRIBUTING](CONTRIBUTING.md) and [CONDUCT](CONDUCT.md) for details.

## Security

If you discover any security related issues, please email mail@burakozdemir.co.uk instead of using the issue tracker.

## Credits

- [Burak Özdemir][link-author]
- [All Contributors][link-contributors]

## License

The MIT License (MIT). Please see [License File](LICENSE.md) for more information.

[ico-version]: https://img.shields.io/packagist/v/ozdemirburak/skyscanner-php.svg?style=flat-square
[ico-license]: https://img.shields.io/badge/license-MIT-brightgreen.svg?style=flat-square
[ico-travis]: https://img.shields.io/travis/ozdemirburak/skyscanner-php/master.svg?style=flat-square
[ico-downloads]: https://img.shields.io/packagist/dt/ozdemirburak/skyscanner-php.svg?style=flat-square

[link-packagist]: https://packagist.org/packages/ozdemirburak/skyscanner-php
[link-travis]: https://travis-ci.org/ozdemirburak/skyscanner-php
[link-downloads]: https://packagist.org/packages/ozdemirburak/skyscanner-php
[link-author]: https://github.com/ozdemirburak
[link-contributors]: ../../contributors
