---
layout: classic-docs
title: Hipchat
categories: [integrations]
last_updated: May 11, 2016
description: Hipchat
---

This guide will help you automate posting Airbrake errors to
[Hipchat](http://www.hipchat.com)! You will need an **auth token** and to pick a
**Room name** that you want to receive Airbrake error notifications in.

## Create a Hipchat auth token for Airbrake
First you will need to [create a Hipchat V1 API auth token](https://www.hipchat.com/admin/api).
The new token's type should be be `Notification`

![hipchat new token](/docs/assets/img/docs/integrations/hipchat_new_token.png)

## Room Name
You can see your room names in hipchat with this link
[https://www.hipchat.com/rooms/ids](https://www.hipchat.com/rooms/ids).

## Configure the Hipchat integration
Fill in the Hipchat integration's fields with your **Api auth token** and
**Room name**, then Save. The **Test integration** link is a helpful way to check that your configuration will work when a new Airbrake error occurs.

![hipchat settings](/docs/assets/img/docs/integrations/hipchat_settings.png)
