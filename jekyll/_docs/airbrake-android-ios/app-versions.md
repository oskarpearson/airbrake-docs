---
layout: classic-docs
title: App versions
categories: [airbrake-android-ios]
last_updated: May 11, 2016
description: App versions
---

![arthur ios](/docs/assets/img/docs/arthur_ios.jpeg)

You can download the Airbrake iOS notifier at [github.com/airbrake/airbrake-ios](https://github.com/airbrake/airbrake-ios**).

Airbrake can be set to ignore errors that come from older versions of your
application. This is most useful when releasing new versions of iOS or Android
apps. Not everyone will upgrade the app, but you don't want to see reports
from errors you've already fixed.

## Current app version
**Current app version** is the version is the version of your app currently in the app store.
This is the version you want to report errors for and should list in your
Airbrake project's **Min app version** setting. See [airbrake-ios
versioning](https://github.com/airbrake/airbrake-ios#versioning) for more
details.

## Configuring **Min app version**

### Use the **upper left cog** to get to your project's settings

![airbrake settings cog](/docs/assets/img/docs/airbrake/settings_cog.png)

### Enter the **Min app version** and **Save**
Fill in the **Min App Version** field with the version for the current
release in the app store then **Save**.

![edit min app version](/docs/assets/img/docs/edit_min_app_version.png)

## **App version** examples

Here are a few examples going over how Airbrake will handle various versions if
an exception occurs.
The **Min app version** is the version you have set in your project's settings.
The **User's app version** is the version of your app running on the user's device.
**Accepted** indicates if Airbrake will accept the error.

<table>
  <tbody>
    <tr>
      <th>Min app version</th>
      <th>User's app version</th>
      <th>Accepted</th>
    </tr>
    <tr>
      <td>1.0.0</td>
      <td>1.0.0</td>
      <td>Yes</td>
    </tr>
    <tr>
      <td></td>
      <td>1.0.1</td>
      <td>Yes</td>
    </tr>
    <tr>
      <td></td>
      <td>2.0.0</td>
      <td>Yes</td>
    </tr>
    <tr>
      <td></td>
      <td>1.0</td>
      <td>Yes</td>
    </tr>
    <tr>
      <td></td>
      <td>1</td>
      <td>Yes</td>
    </tr>
    <tr>
      <td></td>
      <td>1.0.0beta1</td>
      <td>No</td>
    </tr>
    <tr>
      <td></td>
      <td>1.0.0rc1</td>
      <td>No</td>
    </tr>
    <tr>
      <td></td>
      <td>1.0.0foobar1</td>
      <td>No</td>
    </tr>
    <tr>
      <td></td>
      <td>0.9.0</td>
      <td>No</td>
    </tr>
    <tr>
      <td></td>
      <td>&lt;empty&gt;</td>
      <td>No</td>
    </tr>
    <tr>
      <td>2.0.0beta1</td>
      <td>2.0.0</td>
      <td>Yes</td>
    </tr>
    <tr>
      <td></td>
      <td>2.0.0beta1</td>
      <td>Yes</td>
    </tr>
    <tr>
      <td></td>
      <td>2.0.0beta2</td>
      <td>Yes</td>
    </tr>
    <tr>
      <td>v1.0</td>
      <td>v1.0</td>
      <td>Yes</td>
    </tr>
    <tr>
      <td></td>
      <td>1.0</td>
      <td>No</td>
    </tr>
    <tr>
      <td>b4666a9</td>
      <td>b4666a9</td>
      <td>Yes</td>
    </tr>
    <tr>
      <td></td>
      <td>b4666b0</td>
      <td>No</td>
    </tr>
  </tbody>
</table>
