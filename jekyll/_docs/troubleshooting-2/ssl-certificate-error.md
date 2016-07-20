---
layout: classic-docs
title: SSL certificate error
categories: [troubleshooting-2]
last_updated: May 11, 2016
description: SSL certificate error
---
### DEPRECATION WARNING AIRBRAKE V4

This document contains information for the Airbrake V4 notifier. This notifier
is deprecated and we highly recommend [migrating to Airbrake
V5](https://github.com/airbrake/airbrake/blob/master/docs/Migration_guide_from_v4_to_v5.md)
to get the most out of the Airbrake service and features.

## Hostname does not match certificate
{% highlight ruby %}
OpenSSL::SSL::SSLError (hostname does not match the server certificate)
{% endhighlight %}

If you get this error, it means the hostname on your local machine does not
match what is listed on the certificate.

Make sure the AirBrake gem version you are using is Above `3.0.5` you can
check the current version of the AirBrake gem by running the following command:

{% highlight bash %}
gem list airbrake
{% endhighlight %}
