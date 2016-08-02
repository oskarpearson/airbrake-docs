---
layout: classic-docs
title: GitHub
categories: [integrations]
last_updated: May 11, 2016
description: GitHub
---

# Adding The GitHub integration
Create GitHub issues for new Airbrake errors!
This integration allows you to create a GitHub issue from an Airbrake error manually.
You can also set this integration to automatically create a GitHub issue when a new type of error is reported to Airbrake.

## Authenticate with GitHub
Airbrake needs permission to create GitHub issues for your project.

1. Click **Integrations** for your project
2. Click **GitHub**
3. Click the button that says **Redirect to GitHub for authentication**

![github auth](/docs/assets/img/docs/integrations/github_auth.png)

## Add your project's GitHub repo url
For a GitHub user **mmcdaris** who has a repo named **coffee-bot** the GitHub repo URL you would use is:

{% highlight bash %}
https://github.com/mmcdaris/coffee-bot.git
{% endhighlight %}

1. Enter GitHub repo URL
2. Click **Save**

![github repo url](/docs/assets/img/docs/integrations/github_repo_url.png)


# Adding The GitHub Enterprise integration
Create GitHub Enterprise issues for new Airbrake errors!
This integration allows you to create a GitHub Enterprise issue from an Airbrake error manually.
You can also set this integration to automatically create a GitHub Enterprise issue when a new type of error is reported to Airbrake.

## Authentication
Airbrake needs your personal GitHub Enterprise access token to create GitHub Enterprise issues for your project.

1. Click **Integrations** for your project
2. Click **GitHub**
3. Choose  **GitHub Enterprise** from select menu
4. Enter your personal GitHub Enterprise access token
5. Click **Save**

![github integration type](/docs/assets/img/docs/integrations/github_integration_type.png)

### Find your personal GitHub Enterprise access token

On your GitHub Enterprise account go to personal **Settings**:

![github enterprise dropdown](/docs/assets/img/docs/integrations/github_enterprise_dropdown.png)

Click on **Personal access tokens** button:

![github enterprise tokens](/docs/assets/img/docs/integrations/github_enterprise_tokens.png)

Click on **Generate new token** button:

![github enterprise generate token](/docs/assets/img/docs/integrations/github_enterprise_generate_token.png)

Enter **Token description**, and select **repo** and **public_repo** scopes. Click on **Generate token** button:

![github enterprise token fields](/docs/assets/img/docs/integrations/github_enterprise_token_fields.png)

Copy and paste your token:

![github enterprise new token](/docs/assets/img/docs/integrations/github_enterprise_new_token.png)

## Add your project's GitHub Enterprise repo url
For a GitHub Enterprise account **airbrake-github.airbrake.io**, for a user **shifi** who has a repo named **airbrake** the GitHub Enterprise URL you would use is:

{% highlight bash %}
https://airbrake-github.airbrake.io/shifi/airbrake.git
{% endhighlight %}

1. Enter GitHub Enterprise repo URL
2. Click **Save**

![github enterprise repo url](/docs/assets/img/docs/integrations/github_enterprise_repo_url.png)
