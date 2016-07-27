---
layout: classic-docs
title: Installing Airbrake in a PHP application
short-title: PHP
categories: [installing-airbrake]
last_updated: May 11, 2016
description: Installing Airbrake in a PHP application
---

![PHPBrake](http://f.cl.ly/items/0e2f2R2I0i081N2w3R0a/php.jpg)

## Features
[PHPBrake](https://github.com/airbrake/phpbrake) is the official Airbrake PHP notifier.
PHPBrake includes a many useful features that give you control over when and
what you send to Airbrake, you can:

- [Send notices from try-catch blocks in your code](https://github.com/airbrake/phpbrake#quickstart)
- [Add custom data to a notice](https://github.com/airbrake/phpbrake#adding-custom-data-to-the-notice)
- [Filter sensitive data from the notice](https://github.com/airbrake/phpbrake#filtering-sensitive-data-from-the-notice)
- [Ignore specific exceptions](https://github.com/airbrake/phpbrake#ignoring-specific-exceptions)
- Configure an error handler to capture uncaught exceptions
- [Integrate with monolog](https://github.com/airbrake/phpbrake#monolog-integration)

## Installation

#### *Visit our [official GitHub repository](https://github.com/airbrake/phpbrake) for full installation instructions and configuration options.*

```
composer require airbrake/phpbrake
```

## Quickstart

```
// Create new Notifier instance.
$notifier = new Airbrake\Notifier(array(
    'projectId' => 12345, // FIX ME
    'projectKey' => 'abcdefg', // FIX ME
));

// Set global notifier instance.
Airbrake\Instance::set($notifier);

// Register error and exception handlers.
$handler = new Airbrake\ErrorHandler($notifier);
$handler->register();

// Somewhere in the app...
try {
    throw new Exception('hello from phpbrake');
} catch(Exception $e) {
    Airbrake\Instance::notify($e);
}
```
