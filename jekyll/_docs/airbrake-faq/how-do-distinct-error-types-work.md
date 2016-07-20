---
layout: classic-docs
title: Distinct error grouping
categories: [airbrake-faq]
last_updated: May 11, 2016
description: distinct error grouping
---

**Distinct grouping**: Errors of the same class will not be grouped together even if they were thrown
in the same place in the code.

This can be useful in cases where third-party services throw errors of the same
class but are very different in root cause and origin or if Airbrake groups
errors too aggressively.

## Adding a Distinct error type

### Navigate to your Project settings
You can get to your Project settings by clicking the cog in the upper left from
your error dashboard.

![settings cog](/docs/assets/img/docs/airbrake/settings_cog.png)

### Add the error class to the text field, then **Save**

Errors types are whitespace delimited, so use newlines to separate your
Distinct error classes.

![distinct grouping](/docs/assets/img/docs/airbrake/distinct_grouping.png)
