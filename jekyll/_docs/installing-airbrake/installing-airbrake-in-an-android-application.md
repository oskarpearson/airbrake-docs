---
layout: classic-docs
title: Installing Airbrake in an Android application
short-title: Android
categories: [installing-airbrake]
last_updated: May 11, 2016
description: Installing Airbrake in an Android application
---

## Setting up your Android project
Download the Airbrake Jar of the build from source via
[GitHub](https://github.com/airbrake/airbrake-android).
Copy the .jar file to your Android app's `libs/` folder.
Import the `AirbrakeNotifier` class in your app's `main` Activity.

{% highlight java %}
import com.loopj.android.airbrake.AirbrakeNotifier;
{% endhighlight %}

In your activity's `onCreate` function, call `AirbrakeNotifier.register` to
begin capturing exceptions:

{% highlight java %}
AirbrakeNotifier.register(this, "API_KEY");
{% endhighlight %}

## Configuration
`AirbrakeNotifier.register` requires a context and an Airbrake API key to
be passed in, and optionally a third argument specifying the environment. The
environment defaults to 'production' if not set.

## Notify from a try catch block
To notify Airbrake of non-fatal exceptions, or exceptions you have explicitly
caught in your app, you can call `AirbrakeNotifier.notify`. This call takes
exactly one argument, a `Throwable`, and can be called from anywhere in your
code. For example:

{% highlight java %}
try {
  // Something dangerous
} catch(Exception e) {
  // We don't want this to crash our app, but we would like to be notified
  AirbrakeNotifier.notify(e);
}
{% endhighlight %}
