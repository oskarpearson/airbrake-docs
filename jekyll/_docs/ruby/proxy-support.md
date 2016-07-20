---
layout: classic-docs
title: Proxy support
categories: [ruby]
last_updated: May 11, 2016
description: Proxy support
---

## Can I configure Airbrake to send errors through a proxy?

Yes, you can! If your server is not able to directly reach the Airbrake
servers you can configure the Airbrake ruby notifier to send errors through
your proxy.

Configuring Airbrake to use your proxy is as simple as setting the relevant proxy
options in the initializer

### Configuring Airbrake V5 to use a proxy

{% highlight ruby %}
Airbrake.configure do |c|
  c.proxy = {
    host: 'example.com'
    port: 8080
    user: 'user'
    password: 'p4ssw0rd'
  }
end
{% endhighlight %}

### Configuring the DEPRECATED Airbrake V4 to use a proxy

The Airbrake V4 notifier is deprecated and we highly recommend [migrating to
Airbrake
V5](https://github.com/airbrake/airbrake/blob/master/docs/Migration_guide_from_v4_to_v5.md)
to get the most out of the Airbrake service and features.

{% highlight ruby%}
Airbrake.configure do |config|
  config.proxy_host = 'example.com'
  config.proxy_port = 8080
  config.proxy_user = 'proxy-mus prime'
  config.proxy_pass = 'tr4nsF0rm3rs'
end
{% endhighlight %}

We have more config options in https://github.com/airbrake/airbrake/wiki
