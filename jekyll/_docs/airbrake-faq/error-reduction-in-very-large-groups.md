---
layout: classic-docs
title: Error reduction in very large groups
categories: [airbrake-faq]
last_updated: May 11, 2016
description: error reduction in very large groups
---
![high occurrence warning](/docs/assets/img/docs/airbrake/high_occurrence_warning.png)

Some errors live for a long time, and in rare cases, you may have an error
with an extremely large number of occurrences marked with this note:

>This error has an extremely high number of occurrences. As a result, we are
not storing every occurrence.

### Further storage details
This note means that Airbrake is not storing every single occurrence. This
functionality prevents error storage requirements from getting out of control,
ensuring we can continue delivering fast and reliable service. We drop roughly
25% of the occurrences, using an algorithm to distribute these deletions
evenly.

### Total occurrence numbers
Error occurrence counts are not affected and behave as normal, giving you the
real number of occurrences. Error overview graphs will also show the real
number of occurrences (the number before our algorithm runs).  The only
difference is that you can not browse every single occurrence of this error.
