---
layout: classic-docs
title: What is a rate limit
categories: [airbrake-faq]
last_updated: May 11, 2016
description: what is a rate limit
---

## How does the rate limit work?
The Airbrake plan you have selected determines the number of incoming exceptions
that it will accept per minute. Once the limit is reached, all incoming
exceptions for your account will be discarded for the rest of that minute.

### For Example

If you have an account with a rate limit of 3 errors per minute, all errors
after the first 3 for that minute will be rate limited. The rate limit will be
reset at the start of the next minute:

![rate limit](/docs/assets/img/docs/airbrake/rate_limit.png)

## Where can I find my rate limit?
The limit is different for each plan. To see what your rate limit is, visit the
**Account settings** page at: `https://YOUR_SUBDOMAIN.airbrake.io/account/edit`
You'll receive an email notification each day that your account goes over the
limit for your plan.

## Rate limit notification
The dashboard notification is displayed for 24 hours after your account reaches
the rate limit. If you see this notification, that means that sometime in the
past day your account has reached the rate limit. The rate limit is reset each
minute so if your account hits the rate limit, then your projects will stop
reporting errors for the rest of that minute and start again the next minute.

## How can I increase my rate limit?
If you are exceeding your rate limit, you may want to upgrade your Airbrake
account's plan. An increased rate limit can stop error loss during high traffic
times.

## How many errors have I lost from not being on the right plan?
You can view the number of errors you are missing due to rate limit via the new
project overview graphs. The number of errors you have lost in the last 90 days
will be shown. This information should help you to decide which plan to upgrade
to.
