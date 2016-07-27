---
layout: classic-docs
title: Installing Airbrake in a Node.js app
short-title: Node.js
categories: [installing-airbrake]
last_updated: June 14, 2016
description: installing airbrake in a node app
---
![node flag](/docs/assets/img/docs/node_flag.jpeg)

## Features
* Send chosen environment variables (whitelist or blacklist)
* Detect and fix circular references in error context information
* Support for all features of the 2.1 notification API
* Support for long-stack-traces
* Optional auto-handler for `uncaughtException` events
* Provides notification URL linking to Airbrake in `notify()` callback
* Timeout Airbrake requests after 30 seconds, you never know

## Installation

#### *Visit our [official GitHub repository](https://github.com/airbrake/node-airbrake) for full installtion and configuration information.*

### NPM

Add the Node Airbrake package to your `package.json`:

```js
{
  "dependencies": {
    "airbrake": "~1.0.3"
  }
}
```

### Manual

Invoke the following command from your terminal:

```sh
npm install airbrake
```
