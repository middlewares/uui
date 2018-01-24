# middlewares/uuid

[![Latest Version on Packagist][ico-version]][link-packagist]
[![Software License][ico-license]](LICENSE)
[![Build Status][ico-travis]][link-travis]
[![Quality Score][ico-scrutinizer]][link-scrutinizer]
[![Total Downloads][ico-downloads]][link-downloads]
[![SensioLabs Insight][ico-sensiolabs]][link-sensiolabs]

Middleware to generate an UUID (Universally Unique Identifiers) and save it in the `X-Uuid` header of the request and response. Useful for debugging purposes.

The UUID generated is compatible with [RFC 4122](http://tools.ietf.org/html/rfc4122) version 4 using [ramsey/uuid](https://github.com/ramsey/uuid) for that.

## Requirements

* PHP >= 7.0
* A [PSR-7](https://packagist.org/providers/psr/http-message-implementation) http message implementation ([Diactoros](https://github.com/zendframework/zend-diactoros), [Guzzle](https://github.com/guzzle/psr7), [Slim](https://github.com/slimphp/Slim), etc...)
* A [PSR-15 middleware dispatcher](https://github.com/middlewares/awesome-psr15-middlewares#dispatcher)

## Installation

This package is installable and autoloadable via Composer as [middlewares/uuid](https://packagist.org/packages/middlewares/uuid).

```sh
composer require middlewares/uuid
```

## Example

```php
$dispatcher = new Dispatcher([
	new Middlewares\Uuid(),

    function ($request) {
        //Get the UUID from the request
        echo $request->getHeaderLine('X-Uuid');
    }
]);

$response = $dispatcher->dispatch(new ServerRequest());

//Get the UUID from the response
echo $response->getHeaderLine('X-Uuid');
```

## Options

#### `header(string $header)`

To configure the header name. By default is `X-Uuid`.

---

Please see [CHANGELOG](CHANGELOG.md) for more information about recent changes and [CONTRIBUTING](CONTRIBUTING.md) for contributing details.

The MIT License (MIT). Please see [LICENSE](LICENSE) for more information.

[ico-version]: https://img.shields.io/packagist/v/middlewares/uuid.svg?style=flat-square
[ico-license]: https://img.shields.io/badge/license-MIT-brightgreen.svg?style=flat-square
[ico-travis]: https://img.shields.io/travis/middlewares/uuid/master.svg?style=flat-square
[ico-scrutinizer]: https://img.shields.io/scrutinizer/g/middlewares/uuid.svg?style=flat-square
[ico-downloads]: https://img.shields.io/packagist/dt/middlewares/uuid.svg?style=flat-square
[ico-sensiolabs]: https://img.shields.io/sensiolabs/i/1153fa6b-33b7-46d2-b39b-c744256b6e83.svg?style=flat-square

[link-packagist]: https://packagist.org/packages/middlewares/uuid
[link-travis]: https://travis-ci.org/middlewares/uuid
[link-scrutinizer]: https://scrutinizer-ci.com/g/middlewares/uuid
[link-downloads]: https://packagist.org/packages/middlewares/uuid
[link-sensiolabs]: https://insight.sensiolabs.com/projects/1153fa6b-33b7-46d2-b39b-c744256b6e83
