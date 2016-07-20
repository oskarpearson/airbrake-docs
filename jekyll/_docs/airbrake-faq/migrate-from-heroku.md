---
layout: classic-docs
title: Migrate from heroku
categories: [airbrake-faq]
last_updated: May 11, 2016
description: migrate from heroku
---

## Steps to migrate projects from heroku

### Step 1: [Create a new Airbrake account](https://airbrake.io/pricing)
Choose a plan that has enough projects to accommodate the  heroku apps you want
to migrate.

### Step 2: Create projects
For each of your heroku apps create a new project in your new Airbrake
account.

### Step 3: Add `AB_API_KEY` to each heroku app
For each of your heroku apps add a new env var called `AB_API_KEY` that holds
the new project's API Key.

{% highlight bash %}
heroku config:set AB_API_KEY=realProjectApiKey -a yourHerokuAppName`
{% endhighlight %}

### Step 4: Update your notifier configs to use `AB_API_KEY`

For each of your apps, update their notifier configs to use `ENV["AB_API_KEY"]`

After you complete these steps, new errors will be reported to the projects in
your new Airbrake account and you can safely remove the heroku Airbrake addon at
your convenience.

### A note on `AIRBRAKE_API_KEY`
When you add the Airbrake addon a heroku environment variable is created.
This variable is called `AIRBRAKE_API_KEY` containing your project's API key.
You can retrieve this variable with:

{% highlight bash %}
heroku config:get AIRBRAKE_API_KEY -a yourHerokuAppName
{% endhighlight %}

If you remove the Airbrake addon then the `AIRBRAKE_API_KEY` env var will also
be removed. Make sure to add `AB_API_KEY` to your heroku apps environment
variables and configure your app to use `AB_API_KEY` before removing the addon
to avoid any interruptions in error collection.
