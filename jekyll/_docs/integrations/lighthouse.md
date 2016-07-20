---
layout: classic-docs
title: Lighthouse
categories: [integrations]
last_updated: May 11, 2016
description: Lighthouse
---

Airbrake can integrate with your existing
[Lighthouse](https://lighthouseapp.com) account, allowing you to create
Lighthouse tickets for new Airbrake errors.

Configuration involves 2 stess, The first step involves creating a Lighthouse API token on the Lighthouse site.
The second is to configure Airbrake to use your Lighthouse **API token**, **subdomain**, and **project id**.

## Lighthouse API token creation

You can create a Lighthouse token on your Lighthouse account's user profile
page. Be sure to give **full access** to the token as shown below.

![generate token](/docs/assets/img/docs/integrations/lighthouse_generate_token.png)

Once you've successfully created the token, you'll see it listed in that same
area (see image below). Take note of the token value for the next steps.

![new token](/docs/assets/img/docs/integrations/lighthouse_new_token.png)

## Airbrake Account and Project Configuration

To setup the and make use of the information in your lighthouse URL:

![subdomain and project id](/docs/assets/img/docs/integrations/lighthouse_subdomain_and_project_id.png)

Click on **Integrations** and then on **Lighthouse** to fill in your Lighthouse
information. First, fill in the Lighthouse access token:

![token settings](/docs/assets/img/docs/integrations/lighthouse_token_settings.png)

After that, fill in the Lighthouse subdomain and the Lighthouse project ID:

![integration settings](/docs/assets/img/docs/integrations/lighthouse_settings.png)
