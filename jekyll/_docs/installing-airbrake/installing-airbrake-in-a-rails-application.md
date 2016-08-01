---
layout: classic-docs
title: Installing Airbrake in a Rails application
short-title: Rails
categories: [installing-airbrake]
last_updated: May 11, 2016
description: Installing Airbrake in a Rails application
---
![ruby flag](/docs/assets/img/docs/ruby_flag.jpeg)

**DEPRECATION WARNING: The information presented on this page is related to
Airbrake v4 only. If you seek for information for Airbrake v5, please refer to
our [gem's README](https://github.com/airbrake/airbrake)!**

*Airbrake account note: In order to create new projects and view your project's
API key, your user needs to be an administrator on the your Airbrake account.
Not an admin?  Contact an admin on your account, they can change your admin
status.*

# Rails Installation

## Rails 4.x & 3.x
Add the airbrake gem to your Gemfile. In Gemfile:
{% highlight ruby %}
gem 'airbrake'
{% endhighlight %}

In your project's root, run:

{% highlight bash %}
bundle install
rails generate airbrake --api-key your_project_key_here
{% endhighlight %}

The generator creates a file under `config/initializers/airbrake.rb` configuring Airbrake with your API key. This file should be checked into your version control system so that it is deployed to your staging and production environments.

Here is an [asciicast](https://asciinema.org/a/20035) of this process.

## Rails 2.x
Add the airbrake gem to your app. In `config/environment.rb`:

{% highlight ruby %}
config.gem 'airbrake'
{% endhighlight %}

or if you are using bundler:

{% highlight ruby %}
gem 'airbrake', :require => 'airbrake/rails'
{% endhighlight %}

Then from your project's RAILS_ROOT, and in your development environment, run:

{% highlight bash %}
rake gems:install
rake gems:unpack GEM=airbrake
script/generate airbrake --api-key your_key_here
{% endhighlight %}

As always, if you choose not to vendor the airbrake gem, make sure every server you deploy to has the gem installed or your application won't start.

The generator creates a file under `config/initializers/airbrake.rb` configuring Airbrake with your API key. This file should be checked into your version control system so that it is deployed to your staging and production environments.

## Errors from development, test, cucumber envs
Exceptions raised from Rails environments named development, test or cucumber will be ignored by default.

You can clear the list of ignored environments with this setting:

{% highlight ruby %}
config.development_environments = []
{% endhighlight %}

if you want to report **500 Errors** from these environments you will need to change the consider_all_reqeusts_local from true to false in config/environments/development.rb:

{% highlight ruby %}
config.consider_all_requests_local = false
# Shows prod style errors
{% endhighlight %}

## Errors Ignored by default

Airbrake will not report errors with the following classes by default

{% highlight ruby %}
ActiveRecord::RecordNotFound
ActionController::RoutingError
ActionController::InvalidAuthenticityToken
CGI::Session::CookieStore::TamperedWithCookie
ActionController::UnknownHttpMethod
ActionController::UnknownAction
AbstractController::ActionNotFound
Mongoid::Errors::DocumentNotFound
{% endhighlight %}

You can allow errors from all classes to be sent with the following config line
Note: This may cause you to hit your max errors per minute limit

{% highlight ruby %}
config.ignore_only = []
{% endhighlight %}

## More Info and Customizations in the Airbrake GitHub wiki
Please visit [Airbrake gem repo](https://github.com/airbrake/airbrake) for
more config customizations and special use cases.
