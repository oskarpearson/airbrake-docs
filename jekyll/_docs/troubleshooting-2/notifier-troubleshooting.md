---
layout: classic-docs
title: Notifier troubleshooting
categories: [troubleshooting-2]
last_updated: May 11, 2016
description: Notifier troubleshooting
---

### DEPRECATION WARNING AIRBRAKE V4

This document contains information for the Airbrake V4 notifier. This notifier
is deprecated and we highly recommend [migrating to Airbrake
V5](https://github.com/airbrake/airbrake/blob/master/docs/Migration_guide_from_v4_to_v5.md)
to get the most out of the Airbrake service and features.

## Reporting issues

Please report issues to [support@airbrake.io](mailto:support@airbrake.io) and include as much of the following
information in your support request as possible:

- The output from `rake airbrake:test --trace`
- Ruby and Rails version
- Contents of your Gemfile and Gemfile.lock

## Ignored exceptions

There are a number of exceptions that are common enough that we explicitly do
not send them to Airbrake at all. These include:

{% highlight ruby %}
ActiveRecord::RecordNotFound
CGI::Session::CookieStore::TamperedWithCookie
ActionController::RoutingError
ActionController::InvalidAuthenticityToken
ActionController::UnknownAction
{% endhighlight %}

The ruby notifier is configured to avoid sending these to Airbrake by default.
Even if you override these defaults sending these errors to Airbrake will not
trigger emails.

## `rake airbrake:test` succeeds, but some exceptions don't showing up in the dashboard

Check that the exception is not [ignored by default](#ignored-exceptions), then
double check that you have checked **Notify on error** for the
project in your notification settings.

If you're running Rails 2.3.x, or any other rack-based system, then be sure you
have the latest version of the notifier plugin.  There was a known issue with
prior versions of the plugin and rack clients.

## I don't see any error notifications from my development environment

Check that the exception is not [ignored by default](#ignored-exceptions), then
double check that you have checked **Notify on error** for the
project in your notification settings.

Airbrake does not send notifications for the development and test environments.
This allows you to test and develop locally without flooding your inbox with
noisy false positives.

## `rake airbrake:test` works from my production environement but not with my other environment

Running `rake airbrake:test` tests your configuration and generates a
`RuntimeException` from your rails application.  The Airbrake Notifier plugin
then catches that exception and sends it on to the Airbrake service.  To ensure
that Airbrake doesn't receive bogus exceptions, the Notifier only sends them
along if it's running in production (well, if
`config.action_controller.consider_all_requests_local` is false, to be more
precise).  This means that your development exception will get ignored.

To test that Airbrake is properly installed, you'll have to either run the test
on staging or production, You can use an inline environment variable to convince
your local rails application that it's running in production:

{% highlight bash %}
RAILS_ENV=production rake airbrake:test
{% endhighlight  %}
   You can do that
Depending on your version of the airbrake gem, you may need to update your
`config/environments/development.rb` file:

{% highlight ruby %}
config.action_controller.consider_all_requests_local = false
{% endhighlight  %}

## Would an Airbrake API outage effect Application performance?

We completely understand that concern, and have included configurable timeout
settings into the notifier. You can specify the `http_open_timeout` and
`http_read_timeout` values in your Airbrake.rb file:

{% highlight ruby %}
AirbrakeNotifier.configure do |config|
  # other configurations
  config.http_open_timeout = 1 # defaults to 2 (seconds)
  config.http_read_timeout = 3 # defaults to 5 (seconds)
end
{% endhighlight %}

## I'm using `rescue_from` in my controller & not see the exceptions in Airbrake

Airbrake uses `alias_method_chain` to hook into the `rescue_action_in_public`
method.  Overrides the rescue_action method in ActionController::Base, but does
not inhibit any custom processing that is defined with Rails 2's exception
helpers.

{% highlight ruby %}
def rescue_action_in_public_with_Airbrake exception
  notify_Airbrake(exception) unless ignore?(exception)
  rescue_action_in_public_without_Airbrake(exception)
end
{% endhighlight %}

The `rescue_from` system in Rails actually catches the exceptions before
`rescue_action_in_public` happens.  The consequence is that if you want to see
those exceptions in Airbrake, you'll need to explicitly send them along in your
rescue_from method using `notify_Airbrake(exception)`:

{% highlight ruby %}
rescue_from SillyError, :with => :render_silly_error

def render_silly_error(e)
  notify_Airbrake(e)
  render :template => 'i_blowzed_up'
end
{% endhighlight %}

## Airbrake is throwing `TypeError (can't dump anonymous class Class)`

[Known issue when Rack::Bug](http://github.com/brynary/rack-bug/issues#issue/6)
is installed, make sure to turn it off when in the production environment. You
can also try adding an environment filter, which is the recommended workaround:

{% highlight ruby %}
Airbrake.configure do |config|
  config.environment_filters << 'rack-bug.*'
end
{% endhighlight %}

## Errors when submitting custom data with `AirbrakeNotifier.notify`

Make sure to check out the documentation in [Submitting Errors to
Airbrake](/docs/api-2/notifier-api-v3/). Also, here's an
[example gist](http://gist.github.com/166029) of a YAML hash that Airbrake
accepts that was generated by Sinatra.
