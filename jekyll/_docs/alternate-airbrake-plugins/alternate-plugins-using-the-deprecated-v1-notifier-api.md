---
layout: classic-docs
title: Alternate plugins using the retired V1 API
categories: [alternate-airbrake-plugins]
last_updated: May 11, 2016
description: Alternate plugins using the retired V1 API
---

## WARNING the V1 API has been shut down
Any alternate plugins that use the V1 API will not function any longer.

The following projects are alternative Airbrake notifier plugins for a variety
of languages and frameworks which use the retired V1 Notifier API. For current
API information please visit our [API
docs](https://{{ site.host }}/docs/api/#error-notification-v3).

## Notifier plugin that using Beanstalkd
The [Reevoo](http://www.reevoo.com) team has integrated their
[exception_messaging](http://labs.reevoo.com/plugins/exception-messaging) plugin
with their [Beanstalk
messaging](http://labs.reevoo.com/plugins/beanstalk-messaging) plugin and their
[fork of the hoptoad
notifier](http://github.com/lukeredpath/hoptoad_notifier/tree/extract_notifier)
to queue your exceptions from all your apps and send them to Hoptoad from a
centralized server.

## .Net
Ken Robertson wrote HopSharp, a [plugin for
.Net](http://github.com/krobertson/hopsharp/tree/master).

Brennan Falkner developed a [filter for ASP.NET
MVC](http://github.com/BFalkner/hoptoad_notifier_filter/tree/master) that
reports exceptions to Airbrake.

## Java
SNIF Labs, Inc. provides
[jhoptoad](http://github.com/sniflabs/jhoptoad/tree/master), for interacting
with Airbrake from Java.

## Python
Mahmoud Abdelkader maintains a [fork of the django-hoptoad
notifier](http://bitbucket.org/mahmoudimus/django-hoptoad/) which works with the
Deprecated V2 API.

## Ramaze
Pistos created an [Airbrake notifier for
Ramaze](http://blog.purepistos.net/index.php/2008/09/22/managing-web-application-errors-with-hoptoad-and-ramaze).

## ColdFusion
Shayne Sweeney developed
[coldfusion-hoptoad-notifier](http://github.com/shayne/coldfusion-hoptoad-notifier/tree/master),
a simple ColdFusion CFC.

## ActionScript
This [gist](http://gist.github.com/156368) will help to post errors from your
Flash app to Airbrake.
