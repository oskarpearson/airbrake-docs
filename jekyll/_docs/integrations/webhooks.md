---
layout: classic-docs
title: Webhooks
categories: [integrations]
last_updated: May 11, 2016
description: Webhooks
---

Airbrake supports webhooks

You can supply us with a URL that we will POST to every time a new error occurs
(or a resolved error re-occurs). We will send a JSON object containing
information about the error to your URL. You can use this to build your own
service that performs some action every time an exception is thrown. Webhook
integration supports only TLSv1.2 protocol version.

### JSON structure
The JSON Airbrake will post to your webhook url has the following structure:

{% highlight json %}
{
  "error":{
    "id":37463546,
    "error_message":"KitchenException: You are all out of bacon!",
    "error_class":"KitchenException",
    "file":"[PROJECT_ROOT]/app/controllers/bacon_controller.rb",
    "line_number":35,
    "project":{
      "id":1111,
      "name":"Baconator"
     },
    "last_notice":{
      "id":4505303522,
      "request_method":null,
      "request_url":"http://airbrake.io:445/bacon/cook",
      "backtrace":[
        "[PROJECT_ROOT]/app/controllers/bacon_controller.rb:35:in `cook'",
        "[PROJECT_ROOT]/app/middleware/kitchen.rb:19:in `oven'",
        "[PROJECT_ROOT]/app/middleware/kitchen.rb:33:in `chef'",
        "[PROJECT_ROOT]/app/middleware/salumi.rb:23:in `store'"
      ]
    },
    "environment":"avocado",
    "first_occurred_at":"2012-02-23T22:03:03Z",
    "last_occurred_at":"2012-03-21T08:37:15Z",
    "times_occurred":118
  },
  "airbrake_error_url": "https://airbrake.io/airbrake-error-url"
}
{% endhighlight %}
