---
layout: classic-docs
title: Troubleshooting JIRA issues
categories: [integrations]
last_updated: May 11, 2016
description: Troubleshooting JIRA issues
---

## Error 1: "Environment can't be set"

>400 Bad Request - Field 'environment' cannot be set. It is not on the appropriate screen, or unknown.

This error arrises when the **Environment** field is unavailable as an option
for JIRA issue creation.
The fix is to add the **Environment** field on your JIRA issue screen. These
next steps will help you add the **Environment field**.

# Steps

### 1. Click **Administration** in the top right corner and select **Issues**

![jira issues cog dropdown](/docs/assets/img/docs/integrations/jira_issues_cog_dropdown.png)

### 2. Select **Screens**

![jira issues admin dropdown](/docs/assets/img/docs/integrations/jira_issues_admin_dropdown.png)

### 3. In **Default Screen** under the **Operations** column click **Configure**

![jira issues default screen](/docs/assets/img/docs/integrations/jira_issues_default_screen.png)

### 4. Scroll to find the drop down menu and select **Environment**

![jira issues environment dropdown](/docs/assets/img/docs/integrations/jira_issues_environment_dropdown.png)

# Error 2: "Labels can't be set"

>400 Bad Request - Field 'labels' cannot be set. It is not on the appropriate screen, or unknown.

The solution for this error is nearly identical to the previous **Environment
can't be set** error except for one variation.  The goal is to add a **Labels**
field on your JIRA issue screen.  Follow the **Environment can't be set**
instructions above, but instead of adding **Environment** select **Labels**
from the dropdown menu.

If you are still experiencing this issue after adding **Labels** to your JIRA
issue screen. This can be caused by created a custom created field named
**Labels** instead of adding the default one provided by JIRA.
Please make sure to add the default **Labels** field.

# Error 3: Invalid issue type

>400 Bad Request - The issue type selected is invalid.

This error is often the result of your JIRA project not supporting the
**Bug** issue type.
The solution is to [create the **Bug** issue
type](https://confluence.atlassian.com/jira/defining-issue-type-field-values-185729517.html)
for your existing project, or create a new JIRA project that supports the
**Bug** issue type.

# Error 4: Unauthorized

>401 Unauthorized - Please make sure the credentials are correct and try again.

This is often caused by using an email address instead of your JIRA username in
the **username** field.  Please verify that you are using your JIRA username.
You can find your JIRA username in your profile page by clicking your avatar in
JIRA.

### Correct: specifies the username
![jira issues correct username](/docs/assets/img/docs/integrations/jira_issues_correct_username.png)

### Incorrect: specifies the email
![jira issues incorrect username](/docs/assets/img/docs/integrations/jira_issues_incorrect_username.png)
