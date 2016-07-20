---
layout: classic-docs
title: Slack
categories: [integrations]
last_updated: May 11, 2016
description: Slack
---

## [Airbrake](http://airbrake.io) integrates with [Slack](https://slack.com/)

With our Slack integration, Airbrake will post a notification to your Slack
account each time a new error occurs or an error previously marked as resolved
occurs.

![slack example message](/docs/assets/img/docs/integrations/slack_example_message.png)

## Add the Airbrake integration in Slack

### Navigate to **Apps & Integrations**
In top left corner under the drop down menu, choose **Apps & integrations**

![slack apps and integrations](/docs/assets/img/docs/integrations/slack_apps_and_integrations.png)

### Search for Airbrake
Search for **Airbrake** from integrations search box and select it.

![slack airbrake integration](/docs/assets/img/docs/integrations/slack_airbrake_integration.png)

### Pick a channel to post errors to
Airbrake will post new error notifications and comments on errors in the
channel you specify

![slack airbrake settings](/docs/assets/img/docs/integrations/slack_airbrake_settings.png)

### Copy the generated **Slack webhook URL**

Once you have specified a channel Slack will generate a webhook for the
Airbrake service to use.
Copy the **Slack webhook URL** from instructions to Your Airbrake project's slack integration

![slack webhook](/docs/assets/img/docs/integrations/slack_webhook.png)

## Add the **Slack webhook URL** to your Airbrake project
From your Airbrake project's error dashboard, click the **cog in
the upper left** near the project's name. From your project settings page click
**Integrations** in the left sidebar and then select **Slack**.

Paste your **Slack webhook URL** into the form and Save!

![slack settings in airbrake](/docs/assets/img/docs/integrations/slack_settings_in_airbrake.png)
