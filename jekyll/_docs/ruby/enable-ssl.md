---
layout: classic-docs
title: Enable SSL
categories: [ruby]
last_updated: May 11, 2016
description: Enable SSL
---

### DEPRECATION WARNING AIRBRAKE V4
This document contains information for the Airbrake V4 notifier. This notifier
is deprecated and we highly recommend [migrating to Airbrake
V5](https://github.com/airbrake/airbrake/blob/master/docs/Migration_guide_from_v4_to_v5.md)
to get the most out of the Airbrake service and features.

## Using the `config.secure` option
The `secure` option in your project's `config/initializers/airbrake.rb` file is
used to set SSL:

{% highlight ruby %}
AirbrakeNotifier.configure do |config|
  config.api_key = 'secret key'
  config.secure = true
end
{% endhighlight %}

This is enabled by default and ensures that your error information isn't being
sent to Airbrake as cleartext.

We have more config options in https://github.com/airbrake/airbrake/wiki
