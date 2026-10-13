# Google APIs Client Library for PHP

A PHP library for integrating Google APIs into web applications and backend services. It provides a convenient interface for authentication, API requests, and communication with supported Google services.

## Overview

The Google APIs Client Library for PHP helps developers connect PHP applications with Google services such as Gmail, Google Drive, YouTube, and Google Books.

The library simplifies API integration by providing client classes, authentication helpers, and generated service interfaces. It supports OAuth 2.0 authentication, API keys where applicable, and service account credentials for supported APIs.

This repository contains the PHP client library project and its associated resources.

## Features

- Integration with supported Google APIs
- OAuth 2.0 authentication
- Service account authentication
- API key configuration where supported
- Access token and refresh token handling
- Generated service classes for Google APIs
- HTTP requests through Guzzle
- Optional caching support
- Composer-based dependency management

## Requirements

- PHP 8.0 or higher, as specified by the referenced project documentation
- Composer
- Credentials and API access configured in Google Cloud where required

Check the current package requirements before installing, as requirements may vary by release.

## Installation

Install the library through Composer:

```bash
composer require google/apiclient
```

Include Composer's autoloader in your PHP application:

```php
require_once __DIR__ . '/vendor/autoload.php';
```

## Basic Usage

The following example demonstrates how to initialize the client and access the Google Books API using an API key.

```php
<?php

require_once __DIR__ . '/vendor/autoload.php';

$client = new Google\Client();
$client->setApplicationName('My PHP Application');
$client->setDeveloperKey('YOUR_API_KEY');

$service = new Google\Service\Books($client);

$results = $service->volumes->listVolumes(
    'Henry David Thoreau',
    ['filter' => 'free-ebooks']
);

foreach ($results->getItems() ?? [] as $item) {
    echo $item->getVolumeInfo()->getTitle() . PHP_EOL;
}
```

Replace the placeholder API key with a valid key and enable the relevant API in your Google Cloud project.

## Authentication

The library supports multiple authentication methods, depending on the Google API being used.

**OAuth 2.0:** Suitable for applications that need to access Google user data with authorization.

**Service accounts:** Suitable for server-to-server integrations with APIs that support this authentication method.

**API keys:** Suitable for APIs and operations that permit API-key authentication.

Always keep credentials and tokens secure. Do not commit private keys, OAuth client secrets, or other sensitive configuration files to a public repository.

## Documentation

- [Google API PHP Client Documentation](https://googleapis.github.io/google-api-php-client/)
- [Google API PHP Client on GitHub](https://github.com/googleapis/google-api-php-client)
- [Google Cloud PHP Libraries](https://github.com/googleapis/google-cloud-php)

For Google Cloud services such as Cloud Storage, Pub/Sub, and Compute Engine, consider the dedicated Google Cloud PHP client libraries where recommended.

## Project Status

The Google API PHP Client Library is maintained primarily for critical bug fixes and security updates rather than new feature development. Review the official repository for current maintenance status, compatibility, and release information.

## License

The upstream Google API PHP Client Library is distributed under the Apache License 2.0. Retain the original license and attribution notices when redistributing its source code.
