---
layout: classic-docs
title: Installing Airbrake in a Wordpress Application
short-title: WordPress
categories: [installing-airbrake]
last_updated: May 11, 2016
description: Installing Airbrake in a Wordpress Application
---

The Airbrake wordpress plugin collects and aggregates errors created by
WordPress and it's plugins. Airbrake collects, notifies on, and aggregates your
errors, giving developers the ability understand and fix issues fast.

Configuring the plugin with your project API key from
[Airbrake](http://airbrake.io) is required in order to report your errors to
Airbrake.  View more details about the [Airbrake wordpress
plugin](http://wordpress.org/plugins/airbrake).

## Automatic Installation

### Step 1: Login to your wp-admin control panel

### Step 2: Go to Plugins -> Add New

![add new plugin](/docs/assets/img/docs/wordpress/add_new_plugin.png)

### Step 3: Search for the Airbrake plugin

Search for 'Airbrake' to find and install the Airbrake wordpress plugin.

![airbrake search](/docs/assets/img/docs/wordpress/airbrake_search.png)

### Step 4: Configure FTP/FTPS or Modify wp-config.php

#### Step 4a:  FTP/FTPS

![airbrake config](/docs/assets/img/docs/wordpress/ftp_config.png)

#### Step 4b: Automatic

add the following to your `wp-config.php` file:

{% highlight php %}
define ('FS_METHOD', 'direct');
{% endhighlight %}

### Step 5: Configure the plugin
You should now have the Airbrake plugin on your left menu bar.
Add your Airbrake project API key, set the status to 'Enabled'.
Your wordpress application will now report exceptions to Airbrake.

![airbrake config](/docs/assets/img/docs/wordpress/airbrake_config.png)

## Manual Installation

### Step 1: Download and extract the Airbrake plugin

[Download](http://downloads.wordpress.org/plugin/airbrake.latest-stable.zip)
the plugin and extract it to your wordpress /wp-content/plugins/ folder.


### Step 2: Activate

After you have completed the download and extraction, select activate for
Airbrake in the the 'Installed Plugins' section section.

![activate plugin](/docs/assets/img/docs/wordpress/activate_plugin.png)

### Step 5: Configure the plugin
You should now have the Airbrake plugin on your left menu bar.
Add your Airbrake project API key, set the status to 'Enabled'.
Your wordpress application will now report exceptions to Airbrake.

![airbrake config](/docs/assets/img/docs/wordpress/airbrake_config.png)
