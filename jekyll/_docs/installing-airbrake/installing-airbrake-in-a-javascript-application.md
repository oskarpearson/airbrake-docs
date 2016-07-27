---
layout: classic-docs
title: Installing Airbrake in a JavaScript application
short-title: JavaScript
categories: [installing-airbrake]
last_updated: July 27, 2016
description: Installing Airbrake in a Javascript application
---

![](http://f.cl.ly/items/443E2J1D2W3x1E1u3j1u/JS-airbrakeman.jpg)

## Features

- Easy and flexible installation options including NPM, Bower and a public CDN
- Send uncaught errors to Airbrake or manually using a try/catch
- [Add custom parameters](https://github.com/airbrake/airbrake-js#filtering-errors) to your errors for more context
- [Source map support](https://github.com/airbrake/airbrake-js#source-map)
- Control which errors you send with customizable filtering options
- Works well with all frameworks
- Support for the [Backbone.js library](https://github.com/airbrake/airbrake-js/wiki/Using-Airbrake-with-Backbone.js)

## Installation

#### *Visit our [official GitHub repository](https://github.com/airbrake/airbrake-js) for full installation instructions and configuration options.*

The notifier is built using a
[standalone browserify build](http://www.forbeslindesay.co.uk/post/46324645400/standalone-browserify-builds)
and can be used with:

- [RequireJS](https://github.com/airbrake/airbrake-js/tree/master/examples/requirejs).
- [Global/Window](https://github.com/airbrake/airbrake-js/tree/master/examples/legacy).

We include the full source code with the package, so you can use
[Browserify](https://github.com/airbrake/airbrake-js/tree/master/examples/browserify) too.

If you prefer not to host the library yourself,
[airbrake-js is available on the excellent cdnjs CDN](https://cdnjs.com/libraries/airbrake-js).

## Basic Usage

First you need to initialize notifier with project id and API key taken from [Airbrake.io](https://airbrake.io):

```js
var airbrake = new airbrakeJs.Client({projectId: 1, projectKey: 'abc'});
```

Or if you are using browserify/webpack/etc:

```js
var airbrakeJs = require('airbrake-js');
var airbrake = new airbrakeJs({projectId: 1, projectKey: 'abc'});
```

The simplest method is to report errors directly:

```js
try {
  // This will throw if the document has no head tag
  document.head.insertBefore(document.createElement("style"));
} catch(err) {
  airbrake.notify(err);
  throw err;
}
```

Alternatively you can wrap any code which may throw errors using the client's `wrap` method:

```js
var startApp = function() {
  // This will throw if the document has no head tag.
  document.head.insertBefore(document.createElement("style"));
}
startApp = airbrake.wrap(startApp);

// Any exceptions thrown in startApp will be reported to Airbrake.
startApp();
```

#### *Visit our [official GitHub repository](https://github.com/airbrake/airbrake-js) for more information.*
