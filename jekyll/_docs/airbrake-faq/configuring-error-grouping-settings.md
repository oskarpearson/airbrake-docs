---
layout: classic-docs
title: Configuring error grouping settings
categories: [airbrake-faq]
last_updated: May 11, 2016
description: configuring error grouping settings for your project
---

## Default grouping
Airbrake calculates a hash for each error and groups errors with same hash together.
The following attributes are used to calculate the hash:

- error type
- component and action
- file, line and column
- project id
- environment

## Custom grouping
There are a few exceptions where Airbrake uses different data for the hash, these
are configured per project from the projects's settings page.

### Global grouping
*Create Error Groups by error type, don't use default grouping rules*

Errors added to global grouping will be grouped together by **error type**,
differences in error message, component and action, and file/line/column will
not create new groups.

**e.g.** errors with the same **Error type**, and unique values for everything else will be grouped together.

Global grouping compares hashes based on:

- **error type**
- project id
- environment

### Distinct grouping
*Create error groups by unique message*

Error types added to distinct grouping will be grouped with the same rules as
default as well as by **error message**

**e.g.**
two errors that are exactly the same except for their **error message** will now
create 2 groups instead of ending up in the same group

Distinct grouping compares hashes based on:

- **error message**
- [default grouping rules](#default-grouping)

### Strict grouping
*Create error groups by unique backtrace*

A hash is created from the whole backtrace, not only the line where the error occured.

**e.g.**
two errors that are exactly the same except for their **backtraces** will now
create 2 groups instead of ending up in the same group

Strict grouping compares hashes based on:

- **backtrace**
- [default grouping rules](#default-grouping)



## Table of grouping rules

---|default|global|distinct|strict
---|---|---|---|---
error type|used|used|used|used
backtrace| - | - | - |used
error message| - | - |used| -
component & action|used| - |used|used
file, line, & column|used| - |used|used
project id|used|used|used|used
environment|used|used|used|used
