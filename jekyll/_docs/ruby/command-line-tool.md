---
layout: classic-docs
title: Command line tool
categories: [ruby]
last_updated: May 11, 2016
description: Command line tool
---

### DEPRECATION WARNING AIRBRAKE V4
This document contains information for the Airbrake V4 notifier. This notifier
is deprecated and we highly recommend [migrating to Airbrake
V5](https://github.com/airbrake/airbrake/blob/master/docs/Migration_guide_from_v4_to_v5.md)
to get the most out of the Airbrake service and features.

You can use *Airbrake* from the command line.

{% highlight bash %}
airbrake raise --api-key <YOUR_API_KEY>
{% endhighlight %}

This will raise `RuntimeError` with the message `I've made a huge mistake` by
default. Or you can specify which exception class you want to raise.

{% highlight bash %}
airbrake raise -e EspressoException -m 'Out of beans!' -k <PROJECT_API_KEY>
{% endhighlight %}

You can save your api key in the environment if you're annoyed by passing it as
an argument, just set the `AIRBRAKE_API_KEY`.  You can also use
`ENV['AIRBRAKE_API_KEY']` in your airbrake config block:
`config/initializers/airbrake.rb`

Additionally, you can use this command line tool to list all your projects and
find out corresponding ids and api-keys.  your `AUTH_TOKEN` is located by
clicking the settings button when logged into [airbrake](https://airbrake.io)

To do this, execute the following command:

{% highlight bash %}
airbrake list --auth-token <AUTH_TOKEN> --account <ACCOUNT_SUBDOMAIN>
{% endhighlight %}

If you need any additional help about this tool and how to use it, please refer
to help:

{% highlight bash %}
airbrake -h
Usage: airbrake [COMMAND] [OPTION]...
Commands:
  raise         # Raise an exception specified by ERROR and MESSAGE.
  list          # List all the projects for given AUTH_TOKEN and ACCOUNT.
  create        # Create a project with the given NAME.
  deploy        # Send a new deployment notification to a project that matches the API_KEY.

Options:
  -e, [--error=ERROR]            # Error class to raise. Default:  RuntimeError
  -m, [--message=MESSAGE]        # Error message. Default: "I've made a huge mistake"
  -k, [--api-key=API_KEY]        # Api key of your Airbrake application.
  -h, [--host=HOST]              # URL of the Airbrake API server. Default: api.airbrake.io
  -p, [--port=PORT]              # Port of the Airbrake API server. Default: 80
  -t, [--auth-token=AUTH_TOKEN]  # The auth token used for API requests.
  -a, [--account=ACCOUNT]        # The account used for API requests.
  -n, [--name=NAME]              # The name of the project you're trying to create.
  -E, [--rails-env=NAME]         # The target deploy environment, defaults to production.
  -h, [--help]                   # Show this usage
{% endhighlight %}
