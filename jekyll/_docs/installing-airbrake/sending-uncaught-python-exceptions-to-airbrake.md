---
layout: classic-docs
title: Sending uncaught Python exceptions to Airbrake
short-title: Uncaught Python exceptions
categories: [installing-airbrake]
last_updated: May 11, 2016
description: Sending uncaught Python exceptions to Airbrake
---

## Overview
This example shows you how to send uncaught exceptions in Python to Airbrake.  For general instructions how to setup Airbrake with your Python application please visit the repository on Github [here](https://github.com/airbrake/airbrake-python).

By overriding `sys.excepthook` we can send uncaught exceptions to Airbrake.

## Example Code

{% highlight python %}
import logging
import sys
import traceback
import airbrake

def f():
    return g()

def g():
    return h()

def h():
    return i()

def i():
    1/0

def log_uncaught_exceptions(ex_cls, ex, tb):
    logging.critical(''.join(traceback.format_tb(tb)))
    logging.critical('{0}: {1}'.format(ex_cls, ex))

if __name__ == '__main__':
    logging = airbrake.getLogger(api_key="******",
                                project_id=****,
                                environment="development")

    sys.excepthook = log_uncaught_exceptions

    logging.debug('About to do f().')

    try:
        f()
    except:
        pass
{% endhighlight %}

Having trouble? Email us at [support@airbrake.io](mailto:support@airbrake.io)
