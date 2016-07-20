---
layout: classic-docs
title: How do I use the Airbrake heroku addon
categories: [airbrake-faq]
last_updated: May 11, 2016
description: how do I use the Airbrake heroku addon
---

Please review the [Airbrake addon docs on
heroku](http://devcenter.heroku.com/articles/airbrake)

If you have problems after upgrading, please check that you don't still have
Hoptoad installed. You can do this by running:

{% highlight bash %}
heroku config -a <app-name> | grep -E "(AIRBRAKE_API_KEY|HOPTOAD_API_KEY)"
heroku config:remove HOPTOAD_API_KEY --app <app-name>
{% endhighlight %}
