---
layout: classic-docs
title: Installing Airbrake in a Rails application
short-title: Rails
categories: [installing-airbrake]
last_updated: May 11, 2016
description: Installing Airbrake in a Rails application
---
![ruby flag](/docs/assets/img/docs/ruby_flag.jpeg)

## Airbrake gem vs Airbrake Ruby
**[The Airbrake gem](https://github.com/airbrake/airbrake)**: Acts as a
collection of integrations with frameworks and other libraries and is built on
top of Airbrake Ruby.

**[Airbrake Ruby](https://github.com/airbrake/airbrake-ruby)**: The core library
that performs exception sending, filtering sensitive values, ignoring errors,
managing the configuration, and other heavy lifting.

We link to both projects in this guide and want to be clear about their
responsibilities.

# Integrating Airbrake in your Rails app

## Install the Airbrake gem
Open up your `Gemfile` in your favorite text editor and add the `airbrake` gem.

{% highlight ruby %}
gem 'airbrake', '~> 5.4'
{% endhighlight %}

> **NOTE:** This version could be out of date, [the
README](https://github.com/airbrake/airbrake#bundler) will always have the
correct version.

To install the Airbrake gem, run from the root directory of your application.

{% highlight bash %}
bundle install
{% endhighlight %}

## Configure the Airbrake gem to report to your project

This generation command is meant to be run from the root directory of your
application.

{% highlight bash %}
rails g airbrake PROJECT_ID PROJECT_KEY
{% endhighlight %}

> **INFO:** This creates the `config/initializers/airbrake.rb` file containing
your `PROJECT_ID` and `PROJECT_KEY` along with some common config options
and descriptions.

Additional configuration options are detailed in the [airbrake-ruby
README](https://github.com/airbrake/airbrake-ruby#configuration).

## Testing your configuration
The following rake command to sends a test exception to verify your app's
configuration.

{% highlight bash %}
rake airbrake:test
# A Successful test should result in a locate link to see your test exception
The test exception was sent. Find it here: https://airbrake.io/locate/1745875337968541048
{% endhighlight %}

> **HELP:** If you don't see the locate link, please email the complete output
of `rake airbrake:test` to [support@airbrake.io](mailto:support@airbrake.io).

## Ignoring errors
You can choose which errors to ignore before sending them to Airbrake with [**the
`add_filter` method**](https://github.com/airbrake/airbrake-ruby#airbrakeadd_filter).
This makes it simple to ignore errors based on type, message, file, region, or
any other part of the [error's
JSON](https://airbrake.io/docs/api/#create-notice-v3).

For example, to ignore all `StandardError`s you could use the following
`add_filter`:
{% highlight ruby %}
Airbrake.add_filter do |notice|
  if notice[:errors].any? { |error| error[:type] == 'StandardError' }
    notice.ignore!
  end
end
{% endhighlight %}

> **TIP:** A good place to keep your `add_filter`s is below your `configure`
block in `config/initializers/airbrake.rb`

## Filtering keys
You can use
[blacklist](https://github.com/airbrake/airbrake-ruby#blacklist_keys) or
[whitelist](https://github.com/airbrake/airbrake-ruby#whitelist_keys) filtering
to specify keys to filter [out of the payload](https://airbrake.io/docs/api/#create-notice-v3)
(`environment`, `parameters`, `session`, etc). Before sending an
error, filtered keys will be substituted with the `[Filtered]` label.

## Deploy tracking
With deploy tracking you can send information about the deployment of your app
to Airbrake. This unlocks error filtering by deploy and deploy markers are
added to your error graphs.

![graph with deploys](/docs/assets/img/docs/airbrake/graph_with_deploys.png)

We offer several ways to track your deploys:

- [Deploy tracking with the Rake task](https://github.com/airbrake/airbrake#rake-task)
- [Deploy tracking with Capistrano](https://github.com/airbrake/airbrake#capistrano)
- [Deploy tracking guide](/docs/airbrake-faq/deploy-tracking/)
- [Deploy tracking API (create, list, show)](https://airbrake.io/docs/api/#deploys-v4)

## Supported frameworks
Since it's not all about Rails, here are some of our favorite supported ruby
frameworks:

##  Web frameworks

- [Sinatra](https://github.com/airbrake/airbrake#sinatra)
- [Rack applications](https://github.com/airbrake/airbrake#rack)
  - [Our guide for appending info from Rack requests](https://github.com/airbrake/airbrake#rack)
    is applicable to all Rack apps (including Rails).

## Job processing libraries

- [ActiveJob](https://github.com/airbrake/airbrake#activejob)
- [Resque](https://github.com/airbrake/airbrake#resque)
- [Sidekiq](https://github.com/airbrake/airbrake#sidekiq)
- [DelayedJob](https://github.com/airbrake/airbrake#delayedjob)

## Additional libraries

- [Rake](https://github.com/airbrake/airbrake#rake)
- [Plain Ruby scripts](https://github.com/airbrake/airbrake#plain-ruby-scripts)

## More information available on GitHub
Please visit the [Airbrake gem repo](https://github.com/airbrake/airbrake)
for more configuration options, use cases, examples, and tips.

## Looking for the Heroku guide?
If so, you may prefer [Getting started with Airbrake, Rails, &
Heroku](/docs/ruby/0-60-airbrake-rails-31-heroku/), in which you will create a
new rails app on heroku that integrates with airbrake.
