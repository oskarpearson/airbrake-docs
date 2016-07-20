---
layout: classic-docs
title: Filtering component and action
categories: [airbrake-faq]
last_updated: May 11, 2016
description: filtering component and action
---

![component and action](/docs/assets/img/docs/airbrake/component_and_action.png)

## Component and Action

**Component** usually relates to a controller and **Action** is usually the
method in the controller.  Using this filter option you can easily see all the
errors from a given Component or Action.

The typical format is `yourapplication.com/component/action`

For example if an error is experienced on `rent-a-kitten.com/kittens/new`, the
Component is **kittens** and the Action is **new**.
