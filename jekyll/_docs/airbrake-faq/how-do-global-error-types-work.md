---
layout: classic-docs
title: Global error grouping
categories: [airbrake-faq]
last_updated: May 11, 2016
description: Global error grouping
---

Exceptions matching a global error type will be grouped with other errors of its
class, regardless of where they happen in your application.

For example, if your MySQL server goes down, in a Rails applications the errors
will appear from many different controllers and models and clutter your Airbrake
dashboard up.  By setting the error class for these errors as a global class,
the errors will be grouped together as they are delivered to our service.

A full list of grouping options is available in our [grouping
doc](/docs/airbrake-kb/configuring-error-grouping-settings).

## Adding a global error class

### Find the `Error Type` of the error you'd like to be grouped globally This
can be found on the **Overview** tab of an error group.  Example error types
include: `ActiveRecord::RecordNotFound`, `NoMethodError`, `TypeError`, or
`java.lang.NullPointerException`

### Go to your project's settings in the upper left

![settings cog](/docs/assets/img/docs/airbrake/settings_cog.png)

### Add the Error Type then **Save**
Error types are whitespace delimited, use a newline or space to separate types.

![global settings](/docs/assets/img/docs/airbrake/global_grouping.png)
