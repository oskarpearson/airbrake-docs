---
layout: classic-docs
title: Jira
categories: [integrations]
last_updated: May 11, 2016
description: Jira
---


Tired of wasting your limited time scraping together the context and
details needed to create useful Jira issues? By the end of this doc Airbrake
will be automatically creating them for you!

When your Airbrake project receives a new error a corresponding
[Jira](http://www.atlassian.com/software/jira/overview) issue is created.
Jira issues created by Airbrake let you get to work quickly on
problems effecting your users, giving you everything you need to solve problems
fast!

This integration supports **onDemand** and **Standalone** versions of Jira.

## Configuring the Jira integration

1. Click **Integrations** for your project
2. Click **Jira**

![jira settings](/docs/assets/img/docs/integrations/jira_settings.png)

Identify which type of Jira setup you are using. **OnDemand** means you're using an
Atlassian account. **Standalone** means you setup Jira yourself or with a 3rd
party.

**Please ensure this user you provide has proper permissions to the Project.**

### OnDemand Settings:
- Server URL: http://myaccount.atlassian.net
- Username: Jirauser
- Password: JirauserPass
- Project Key: EXAMPLE

### Standalone Settings:
- Server URL: http://jiraurl.mywebsite.com
- Context Path: /jira
- Username: Jirauser
- Password: JirauserPass
- Project Key: EXAMPLE

## Testing your Jira integration settings

Testing your Jira integration settings is as easy as clicking on the **Test
integration** link.

![jira test link](/docs/assets/img/docs/integrations/jira_testing.png)

You should see notification about integration success.
If the test reports any issues, please check our doc on [troubleshooting jira issues](/docs/integrations/troubleshooting-jira-issues).

## Manually create a Jira issue from an Airbrake error

Select the error you want to create a Jira issue for, in the errors overview
tab, click the **Create Jira Issue** button:

![jira button](/docs/assets/img/docs/integrations/jira_button.png)

After the Jira issue is created your Airbrake error will show a link to go the
Jira issue. The Jira issue will also link back to get back to the Airbrake error.
If you would like to remove the association between the Error and issue, just
click the **Remove issue association** button:

![jira issue link](/docs/assets/img/docs/integrations/jira_issue_link.png)
