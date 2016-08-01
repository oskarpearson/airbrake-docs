---
layout: classic-docs
title: JIRA
categories: [integrations]
last_updated: May 11, 2016
description: JIRA
---


Tired of wasting your limited time scraping together the context and
details needed to create useful JIRA issues? By the end of this doc Airbrake
will be automatically creating them for you!

When your Airbrake project receives a new error a corresponding
[JIRA](http://www.atlassian.com/software/jira/overview) issue is created.
JIRA issues created by Airbrake let you get to work quickly on
problems effecting your users, giving you everything you need to solve problems
fast!

This integration supports **onDemand** and **Standalone** versions of JIRA.

## Configuring the JIRA integration

1. Click **Integrations** for your project
2. Click **JIRA**

![jira settings](/docs/assets/img/docs/integrations/jira_settings.png)

Identify which type of JIRA setup you are using. **OnDemand** means you're using an
Atlassian account. **Standalone** means you setup JIRA yourself or with a 3rd
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

## Testing your JIRA integration settings

Testing your JIRA integration settings is as easy as clicking on the **Test
integration** link.

![jira test link](/docs/assets/img/docs/integrations/jira_testing.png)

You should see notification about integration success.
If the test reports any issues, please check our doc on [troubleshooting jira issues](/docs/integrations/troubleshooting-jira-issues).

## Manually create a JIRA issue from an Airbrake error

Select the error you want to create a JIRA issue for, in the errors overview
tab, click the **Create JIRA Issue** button:

![jira button](/docs/assets/img/docs/integrations/jira_button.png)

After the JIRA issue is created your Airbrake error will show a link to go the
JIRA issue. The JIRA issue will also link back to get back to the Airbrake error.
If you would like to remove the association between the Error and issue, just
click the **Remove issue association** button:

![jira issue link](/docs/assets/img/docs/integrations/jira_issue_link.png)
