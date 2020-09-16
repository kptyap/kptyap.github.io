---
layout: post
title: Creating data rows from a summary table - Reverse Pivot
date: 2016-12-12 14:11:29.000000000 +11:00
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- Excel
tags: []
meta:
  _edit_last: '1'
  _oembed_d2c5f3ee43c4d68fc8fa66d5215cc1fa: "{{unknown}}"
  _oembed_4efc42511a49847dd95befb7d544476a: "{{unknown}}"
  _wpas_done_all: '1'
  _jetpack_dont_email_post_to_subs: '1'
  _yoast_wpseo_content_score: '30'
  _yoast_wpseo_primary_category: '2'
  _jetpack_related_posts_cache: a:1:{s:32:"8f6677c9d6b0f903e98ad32ec61f8deb";a:2:{s:7:"expires";i:1526317167;s:7:"payload";a:3:{i:0;a:1:{s:2:"id";i:5;}i:1;a:1:{s:2:"id";i:24;}i:2;a:1:{s:2:"id";i:87;}}}}
  dsq_thread_id: '5497963968'
author:
permalink: "/creating-data-rows-summary-table-reverse-pivot/"
---
I needed to transform a table with data somewhat summarised (see below), back into a database, or data rows.

![]({{ site.baseurl }}/assets/images/2016/12/reversepivot.png)

&nbsp;

Thanks to [the internet](http://sachachua.com/blog/2014/10/microsoft-excel-converting-summary-table-crosstab-back-data-rows/), I uncovered this little trick.

1. Press ALT + D + P to bring up the PivotChart wizard (Didn't know this existed? Me neither.)
2. In the PivotTable dialog box, select the **Multiple consolidation ranges** option
3. In Step 2, choose the **I will create the page fields** option.
4. In Step 2b specify your summary table range in the **Range** field and then&nbsp; **Add it**.
5. Finish off the rest of the wizard
6. Select your newly created Pivot table and uncheck 'Row' and 'Column'
7. Double click on the single value cell that is left.
8. Magic.

![]({{ site.baseurl }}/assets/images/2016/12/x3IjqixX2u.gif)

&nbsp;

