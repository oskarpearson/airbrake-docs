---
layout: classic-docs
title: Assembla
categories: [integrations]
last_updated: May 11, 2016
description: Assembla
---

**NOTE: This feature is only available with [paid assembla
plans](https://www.assembla.com/plans).**

This guide will help you add the Assembla integration to start the automatically
posting new Airbrake errors to an Assembla space that you choose.

### Step 1: Get your Api key and Api key secret from Assembla
Go to [API applications
page](https://www.assembla.com/user/edit/manage_clients) in your Assembla
account.

### Step 2: Copy **Api key** and **Api key secret**

![assembla key](/docs/assets/img/docs/integrations/assembla_key.png)

### Step 3: Enter your **Space name**, **Api key**, and **Api key secret**

![assembla config](/docs/assets/img/docs/integrations/assembla_config.png)

That's it! Now any new Airbrake errors will automatically create Assembla
tickets for the specified space!
