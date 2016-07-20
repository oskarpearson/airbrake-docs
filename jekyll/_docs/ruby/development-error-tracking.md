---
layout: classic-docs
title: Development error tracking
categories: [ruby]
last_updated: May 11, 2016
description: Development error tracking
---

# Tracking errors from your development environment

Want to track errors that occur in your development environment?
A small customization to your `airbrake.rb` file and you will be on your way!

### Airbrake V5: Track errors from the development environment
In Airbrake V5 errors are tracked from development by default.

The `development_environments` V4 option was renamed to `ignore_environments`
in V5. It's behaviour was also slightly changed. By default, the library sends
exceptions from **all environments**, so you don't need to assign an empty Array
anymore to get this behavior(as in V4). More details are available in the [V4
to V5 migration
guide](https://github.com/airbrake/airbrake/blob/master/docs/Migration_guide_from_v4_to_v5.md#development-environments).


### Airbrake V5: Don't track development environment errors

The following config settings will ignore errors originating from the
`development`, `test`, and `cucumber` environments.

{% highlight ruby %}
Airbrake.configure do |c|
  c.environment = Rails.env
  c.ignore_environments = %w(development test cucumber)
  # OR to collection exceptions in all envs
  # Simply don't set this option
end
{% endhighlight %}

### Track errors from development (DEPRECATED) Airbrake V4

Airbrake V4 is deprecated and we highly recommend [migrating to Airbrake
V5](https://github.com/airbrake/airbrake/blob/master/docs/Migration_guide_from_v4_to_v5.md)
to get the most out of the Airbrake service and features.

{% highlight ruby %}
Airbrake.configure do |c|
  c.development_environments = []
end
{% endhighlight %}
