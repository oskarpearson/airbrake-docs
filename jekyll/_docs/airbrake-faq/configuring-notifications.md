---
layout: classic-docs
title: Configuring notifications
categories: [airbrake-faq]
last_updated: May 11, 2016
description: configuring notifications
---

## What settings are available per project?

### **Notify on error**
You will be notified whenever a new exception group is created or an error
group becomes unresolved.

### **Notify on comments**
You will be notified when another team member comments on an exception

### **Production environment only**
Only receive notifications from errors that occur in the `production`
environment.

### Notes

- These settings are user specific.
- These settings only affect email notifications. They will not affect your
  Slack or Hipchat integrations as those are setup per project.*

## Modify your notification settings

### Open the **upper left dropdown** near your user and click **settings**

![airbrake dropdown settings](/docs/assets/img/docs/airbrake/dropdown_settings.png)

### Tune your notification settings and **Save**

![airbrake notification settings](/docs/assets/img/docs/airbrake/notification_settings.png)
