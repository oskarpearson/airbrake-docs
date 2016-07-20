---
layout: classic-docs
title: Deploy tracking troubleshooting
categories: [airbrake-faq]
last_updated: May 11, 2016
description: deploy tracking troubleshooting
---

*For more general information on tracking your application's deploys, Please
read our [article on deploy tracking](/docs/airbrake-faq/deploy-tracking).*

# Deploy Tracking is not resolving errors for your env?

### Reason 1: Environment name does not match exactly

Deploy tracking environment names are case sensitive.  Therefore `Production`
and `production` would be treated as different environments.  Please make sure
that the string in your deploy code for `RAILS_ENV` matches exactly with the
environment variable you initialized your notifier with.

> e.g.  If an error occurs with the environment `Production` you would need
to specify `RAILS_ENV` as "Production" or no errors with the `Production`
env will be resolved.

### Reason 2: **Resolve all errors after a deploy** is unchecked

The **Resolve all errors after a deploy** setting is enabled by default but if
you're having issues with errors not resolving after a deploy, this setting may
be disabled.  Please check your project's settings page by clicking the gear
icon in the top left corner of the error dashboard.

![resolve all checkbox](/docs/assets/img/docs/airbrake/resolve_all_checkbox.png)

**Resolve all errors on this project after a deploy** should be checked.

# Heroku Deploy Hooks

To implement Deploy Hooks on Heroku/Cedar stack, please use one of the following:

{% highlight bash %}
heroku addons:add deployhooks:http \
--url="http://airbrake.io/deploys.txt \
?deploy[rails_env]=production \
&api_key=AIRBRAKE_API_KEY \
&deploy[local_username]={{user}} \
&deploy[scm_revision]={{head_long}} \
&deploy[scm_repository]=GITHUB_URL" # e.g. git@github.com:username/repo.git
{% endhighlight %}

{% highlight bash %}
rake airbrake:heroku:add_deploy_notification
{% endhighlight %}

Be sure to provide the app name for the rake task if you have multiple Heroku
apps configured. You can send it by specifying `ENV["HEROKU_APP"]`.

# Capistrano Deploys
If the notification of the deploy is not happening automatically when you do a
capistrano deploy.

You may need to add `require 'airbrake/capistrano'` to your `deploy.rb`
