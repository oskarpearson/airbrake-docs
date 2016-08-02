---
layout: classic-docs
title: GitLab
categories: [integrations]
last_updated: August 2, 2016
description: GitLab
---

# Adding The GitLab integration
Create GitLab issues for new Airbrake errors!
This integration allows you to create a GitLab issue from an Airbrake error manually.
You can also set this integration to automatically create a GitLab issue when a new type of error is reported to Airbrake.

## Authentication
Airbrake needs your private GitLab token to create GitLab issues for your project.

1. Click **Integrations** for your project
2. Click **GitLab**
3. Enter your private GitLab token
4. Click **Save**

![gitlab-adding-token.png](/docs/assets/img/docs/integrations/gitlab_adding_token.png)

### Find your private GitLab token

You can find your private GitLab token on your [**Profile Settings** page under the **Account** tab](https://gitlab.com/profile/account).

![gitlab-private-token.png](/docs/assets/img/docs/integrations/gitlab_private_token.png)

## Add your project's GitLab repo url
For a GitLab user **shifi** who has a repo named **test-repo** the GitLab repo URL you would use is:

```
https://gitlab.com/shifi/test-repo.git
```

1. Enter GitLab repo URL
2. Click **Save**

![gitlab-adding-repo-url.png](/docs/assets/img/docs/integrations/gitlab_adding_repo_url.png)

# Adding The GitLab Customer/Enterprise Edition integration
Create GitLab CE/EE issues for new Airbrake errors!
This integration allows you to create a GitLab CE/EE issue from an Airbrake error manually.
You can also set this integration to automatically create a GitLab CE/EE issue when a new type of error is reported to Airbrake.

## Authentication
Airbrake needs your private GitLab CE/EE token to create GitLab issues for your project.

1. Click **Integrations** for your project
2. Click **GitLab**
3. Choose  **GitLab CE/EE** from select menu
4. Enter your private GitLab CE/EE token
5. Click **Save**

![giltab-ce-ee-adding-token.png](/docs/assets/img/docs/integrations/giltab_ce_ee_adding_token.png)

### Find your private GitLab CE/EE token

On your GitLab CE/EE account go to **Profile Settings**

![gitlab-ce-ee-profile-settings.png](/docs/assets/img/docs/integrations/gitlab_ce_ee_profile_settings.png)

Click on **Account**

![gitlab-ce-ee-account.png](/docs/assets/img/docs/integrations/gitlab_ce_ee_account.png)

Copy and paste your private GitLab CE/EE token

![gitlab-ce-ee-private-token.png](/docs/assets/img/docs/integrations/gitlab_ce_ee_private_token.png)


## Add your project's GitLab CE/EE repo url
For a GitLab CE/EE account **airbrake-gitlab.airbrake.io**, for a user **shifi** who has a repo named **test-repo** the GitLab CE/EE URL you would use is:

```
https://airbrake-gitlab.airbrake.io/shifi/test-repo.git
```

1. Enter GitLab CE/EE repo URL
2. Click **Save**

![gitlab-ce-ee-adding-repo-url.png](/docs/assets/img/docs/integrations/gitlab_ce_ee_adding_repo_url.png)

### What do these settings mean?
- **Enabled:** Pause/Unpause the integration
- **Auto create GitLab issue when an error occurs:** Create a GitLab issue for every new type of Airbrake error
- **Production environment notifications only:** Only create GitLab issues for errors form the `production` environment

Please email support@airbrake.io If you have any issues or questions!
