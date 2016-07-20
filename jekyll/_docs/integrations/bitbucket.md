---
layout: classic-docs
title: BitBucket
categories: [integrations]
last_updated: May 11, 2016
description: BitBucket
---
Adding the Airbrake-Bitbucket integration will create Bitbucket issues for new
Airbrake errors.
The default behaviour is to automatically create a Bitbucket issue when a new
type of error is reported to Airbrake, this can be turned off if you prefer to
create a Bitbucket issue from an Airbrake error manually.

## Adding the Bitbucket integration

### Project settings
Click the upper left cog to get to your project's settings:

![airbrake settings cog](/docs/assets/img/docs/airbrake/settings_cog.png)

### Authenticate with Bitbucket
Airbrake needs permission to create Bitbucket issues for your project, our next
step is to authenticate!

1. Click **Integrations** for your project
2. Click **Bitbucket**
3. Click **Redirect to Bitbucket for authentication**

![bitbucket auth](/docs/assets/img/docs/integrations/bitbucket_auth.png)

### Add Bitbucket integration
Add your Bitbucket account name and project's repository name then **save**.
![bitbucket settings](/docs/assets/img/docs/integrations/bitbucket_settings.png)
