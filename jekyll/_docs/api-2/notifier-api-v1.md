---
layout: classic-docs
title: API V1 deprecated
short-title: API V1
categories: [api-2]
description: Depricated Notifier API V1
last_updated: May 7, 2016
---

**NOTE: this API has been replaced by the V3 Notifier API**: <https://{{ site.host }}/docs/api>.

The V1 Notifier API will be shut down on February 1,
2010, and projects still using the old API after that date will no longer
receive error notifications.  All libraries and applications should be updated
to use the V2 Notifier API.

If you are using Rails, you can obviously use the [hoptoad_notifier
plugin](http://www.github.com/thoughtbot/hoptoad_notifier).  If you are
interested in submitting errors from a non-Rails application,  you can submit
errors directly to hoptoad via HTTP post.  For complete details of how to do
this, it might be best to look at the notifier source.  But here is some basic
information to get you started.

To submit an error, make an HTTP POST with the error details to
<http://hoptoadapp.com/notices.yml>. You must pass YAML to this.

The POST expects the following parameters as YAML keys, scoped under the key
"notice":

* api_key - The API key for the project this error is from (required).  Get this
  from the project's page in Hoptoad.
* error_message - The message that describes the error (ie. "undefined method
  'password' for nil:NilClass").
* backtrace - An array where each element is a line of the backtrace (required,
  but can be empty).
* request - A hash of the request parameters that were given when the error
  occurred (required, but can be empty).
* session - A hash of the session data that existed when the error occurred
  (required, but can be empty).
* environment - A hash of the environment data that existed when the error
  occurred (required, but can be empty).

Right now, there is specific support for Rails on the server side.  So, given a
Rails request, and environment, we are pulling Rails specific information out of
it, for special display.

We have posted [an example notice](http://gist.github.com/154406).

Restrictions
----------------------------------

* The Hoptoad server rejects incoming requests larger than 100kB.
