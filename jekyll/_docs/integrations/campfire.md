---
layout: classic-docs
title: Campfire
categories: [integrations]
last_updated: May 11, 2016
description: Campfire
---

With the [Campfire](http://www.campfirenow.com)integration Airbrake sends new
error notifications to the Campfire room of your choosing.

## Gathering the Pieces
To configure the Campfire integration you will need to your **Campfire
Subdomain**, **API Token**, and the **Room Name** you want to receive new
Airbrake error notifications in.

#### **Campfire Subdomain**
[login to
your campfire account](https://launchpad.37signals.com/campfire/signin)
and you will see your **Campfire Subdomain** in the URL.

#### **API Token**
You can get your Campfire API Token by clicking the "My Info" link in the top
right of the screen when logged in. The API Token will be near the bottom below
your info.  The API Token is located in the member edit section of your
campfire account, e.g.
[YOURSUBDOMAIN.campfirenow.com/member/edit](https://campfirenow.com/member/edit).

#### **Room Name**
Airbrake will post to the room you specify, please note that **room names are
case sensitive!**

## Putting it all Together
Now that we have everything to integrate with campfire, let's do it!

1. Navigate to the Airbrake project you want to add campfire to and select
   **Integrations**.
2. Select Campfire from the left
3. Fill in the form
4. Save!

![campfire settings](/docs/assets/img/docs/integrations/campfire_settings.png)

> **Common Issue:** If you have problems double check the Room Name is exactly
the same as it appears in YOURSUBDOMAIN.campfirenow.com/rooms

## Testing
Now use the **Test Integration** link from your Campfire Integration to check
your configuration. This will send a test message from Airbrake to your
Campfire room.
![campfire test](/docs/assets/img/docs/integrations/campfire_testing.png)

You should see a message like this in your Campfire room:
![campfire test](/docs/assets/img/docs/integrations/campfire_test_results.png)
