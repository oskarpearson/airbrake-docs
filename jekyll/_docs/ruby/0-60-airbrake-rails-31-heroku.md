---
layout: classic-docs
title: Airbrake, Rails and Heroku
title: Airbrake, Rails and Heroku
categories: [ruby]
last_updated: May 11, 2016
description: Airbrake, Rails + Heroku
---

![ruby flag](/docs/assets/img/docs/ruby_flag.jpeg)

## Setting up new Rails Project with Airbrake

### Step 1: Install Rails

{% highlight bash %}
gem install rails
=> Successfully installed rails-x.x.x
{% endhighlight %}

### Step 2: Create a new Rails app
Heroku apps use postgresql so be sure to add `--database=postgresql` when you
create your Rails app.

{% highlight bash %}
rails new airbrake_rails_test --database=postgresql
{% endhighlight %}

### Step 3: Add airbrake to the Gemfile and install

{% highlight bash %}
cd airbrake_rails_test
echo "gem 'airbrake'" >> Gemfile
bundle install
{% endhighlight %}

### Step 4: Sign up for Airbrake and create a project

[Sign up for Airbrake](https://airbrake.io) and create a project for your Rails
app.  After your Airbrake project has been created you will need it's `API_KEY`
and `PROJECT_KEY` to generate your Airbrake config.

{% highlight bash %}
rails generate airbrake PROJECT_ID API_KEY
{% endhighlight %}

If your configuration was successful and the test error was sent correctly you
should see a locate link at the bottom of the output:

{% highlight bash %}
The test exception was sent. Find it here: https://airbrake.io/locate/1699511183527872975
{% endhighlight %}

you can view your error in the Airbrake dashboard by following the locate link.

If you would like to test your Airbrake config/setup, run the following rake
command from your local environment:

{% highlight bash %}
bundle exec rake airbrake:test
{% endhighlight %}

## Deploying to Heroku (without the addon)

### Step 1: initialize your project with git
Starting from where we left off--in the `airbrake_rails_test` directory from
above. Make a local git repo:

{% highlight bash %}
git init
git add .
git commit -am "Projet Start"
{% endhighlight %}

### Step 2: Then create the heroku app:

{% highlight bash %}
heroku create airbrake_rails_test
{% endhighlight %}

### Step 3: And push your code to heroku:

{% highlight bash %}
git push heroku master
{% endhighlight %}

### Step 4: Test your Airbrake setup on heroku

run this rake command to send a test exception from your heroku app:

{% highlight bash %}
heroku run rake airbrake:test
{% endhighlight %}

visit the locate link near at the bottom of the command's output to see your
error in Airbrake.
