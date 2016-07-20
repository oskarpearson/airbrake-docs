---
layout: classic-docs
title: Troubleshooting jira issues
categories: [integrations]
last_updated: May 11, 2016
description: Troubleshooting jira issues
---

# **Environment can't be set** error

{% highlight bash %}
400 Bad Request - Field 'environment' cannot be set. It is not on the appropriate screen, or unknown.
{% endhighlight %}

This error arrises when the **Environment** field is unavailable as an option
for Jira issue creation.
The fix is to add the **Environment** field on your Jira issue screen. These
next steps will help you add the **Environment field**.

### Click **Administration** in the top right corner and select **Issues**

![jira issues cog dropdown](/docs/assets/img/docs/integrations/jira_issues_cog_dropdown.png)

### Select **Screens**

![jira issues admin dropdown](/docs/assets/img/docs/integrations/jira_issues_admin_dropdown.png)

### In **Default Screen** under the **Operations** column click **Configure**

![jira issues default screen](/docs/assets/img/docs/integrations/jira_issues_default_screen.png)

### Scroll to find the drop down menu and select **Environment**

![jira issues environment dropdown](/docs/assets/img/docs/integrations/jira_issues_environment_dropdown.png)

# **Labels can't be set** error

{% highlight bash %}
400 Bad Request - Field 'labels' cannot be set. It is not on the appropriate screen, or unknown.
{% endhighlight %}

The solution for this error is nearly identical to the previous **Environment
can't be set** error except for one variation.  The goal is to add a **Labels**
field on your Jira issue screen.  Follow the **Environment can't be set**
instructions above, but instead of adding **Environment** select **Labels**
from the dropdown menu.

If you are still experiencing this issue after adding **Labels** to your Jira
issue screen. This can be caused by created a custom created field named
**Labels** instead of adding the default one provided by Jira.
Please make sure to add the default **Labels** field.

# **Invalid issue type** error

{% highlight bash %}
400 Bad Request - The issue type selected is invalid.
{% endhighlight %}

This error is often the result of your Jira project not supporting the
**Bug** issue type.
The solution is to [create the **Bug** issue
type](https://confluence.atlassian.com/jira/defining-issue-type-field-values-185729517.html)
for your existing project, or create a new Jira project that supports the
**Bug** issue type.

# **Unauthorized** error

{% highlight bash %}
401 Unauthorized - Please make sure the credentials are correct and try again.
{% endhighlight %}

This is often caused by using an email address instead of your Jira username in
the **username** field.  Please verify that you are using your Jira username.
You can find your Jira username in your profile page by clicking your avatar in
Jira.

### Correct: specifies the username
![jira issues correct username](/docs/assets/img/docs/integrations/jira_issues_correct_username.png)

### Incorrect: specifies the email
![jira issues incorrect username](/docs/assets/img/docs/integrations/jira_issues_incorrect_username.png)
