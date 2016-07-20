---
layout: classic-docs
title: How do I use search and filtering
categories: [airbrake-faq]
last_updated: May 11, 2016
description: how do I use search and filtering
---

## Default Search Box

![basic search box](/docs/assets/img/docs/airbrake/basic_search_box.png)

The default search box at the top of your error groups list supports text searches for:

- Error type
- Error message
- Filename
- Environment

## Advanced Search & Filter

![filters](/docs/assets/img/docs/airbrake/filters.png)

- **Type**: The errors type/class
- **Message**: The error message
- **Hostname**: Will show if you send `context/hostname` as described in the [API docs](https://{{ site.host }}/docs/api/#create-notice-v3)
- **Environment**: e.g. Production, Staging, this requires you [track deploys](/docs/deploy-tracking)
- **Component**: The controller the error occurred in, [more info](/docs/airbrake-faq/filtering-component-and-action)
- **Action**: The controller method the error occurred in, [more info](/docs/airbrake-faq/filtering-component-and-action)
- **Deploys**: Via [Deployment Tracking](/docs/deploy-tracking)
- **Date**: Shows all groups with last occurrence values between two dates

*Note: You'll only see an option to sort if you are sending the data. E.g. If you don't have [Deployment Tracking](https://help.airbrake.io/kb/api-2/deploy-tracking) setup; you won't see the filter by deploy option.*

## Sort by options
![sort by options](/docs/assets/img/docs/airbrake/sort_by_options.png)

Sort by options include:

- **Last notice occurrence**: sorts by most recent notice
- **Notice count**: sorts by the number of notices in an error group
- **Creation date**: sorts by error group creation date
- **Error Weight**: sorts by recent error impact based on traffic distribution and
  density
