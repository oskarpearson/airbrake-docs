---
layout: classic-docs
title: Project group and notice API
categories: [api-2]
last_updated: May 11, 2016
description: project group and notice API
---

## Please try out new API doc site for full
[https://airbrake.io/docs/api/#projects-v4](https://airbrake.io/docs/api/#projects-v4)

## Projects
{% highlight bash %}
curl "https://airbrake.io/api/v3/projects?key=USER_KEY"
{% endhighlight %}

{% highlight json %}
{
  "projects": [
    {
      "id": 1,
      "name": "Airbrake project name",
      "deployId": "1",
      "deployAt": "2014-09-26T17:37:33.638348Z",
      "noticeTotalCount": 1,
      "rejectionCount": 1,
      "fileCount": 1,
      "deployCount": 1,
      "groupResolvedCount": 1,
      "groupUnresolvedCount": 1
    }
  ]
}
{% endhighlight %}
