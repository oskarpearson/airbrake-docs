---
layout: classic-docs
title: When is data removed from Airbrake
categories: [airbrake-faq]
last_updated: May 11, 2016
description: when is data removed from Airbrake
---

In order to reduce space consumed by old or redundant data Airbrake may remove
backtraces and extra request information from individual error occurances. If
data is removed, the Rails environment name, error class, error message, file,
controller, action, and date are preserved.  When information has been removed,
you will see information message that reads:

> "Some information on the occurance of this error has been removed from the
database."

Airbrake deletes this information after based on your plan's retention period.
