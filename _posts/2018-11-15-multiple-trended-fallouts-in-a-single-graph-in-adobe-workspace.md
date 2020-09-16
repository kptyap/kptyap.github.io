---
layout: post
title: Multiple trended fallouts in a single graph in Adobe Workspace
date: 2018-11-15 14:18:35.000000000 +11:00
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- Digital Analytics
tags: []
meta:
  _edit_last: '1'
  _yoast_wpseo_content_score: '30'
  _thumbnail_id: '318'
  _yoast_wpseo_primary_category: '9'
  _yoast_wpseo_metadesc: How to visualise multiple fallout report trends over time
    in a single line graph in Adobe Analytics
author:
 
permalink: "/multiple-trended-fallouts-in-a-single-graph-in-adobe-workspace/"
---
<!-- wp:paragraph -->

Adobe Analytics Workspace makes it extremely easy for anyone to build decent looking, dynamic graphs and charts. Yet, if you are trying to visualise something that doesn't fit within the constraints arbitrarily determined by Adobe, you're going to have a bad time.

<!-- /wp:paragraph -->

<!-- wp:image {"id":322,"align":"center","width":251,"height":421} -->

<figure class="aligncenter is-resized"><img src="{{ site.baseurl }}/assets/images/2018/11/Trend_touchpoint-1.png" alt="" class="wp-image-322" width="251" height="421"></figure>

<!-- /wp:image -->

<!-- wp:paragraph -->

An example is the fallout report. Beloved by digital analysts and business users everywhere, the fallout report allows us to see exactly where in the journey users are dropping off. And we can even track how our journey is performing overtime, as we iterate and make changes.

<!-- /wp:paragraph -->

<!-- wp:paragraph -->

This looks great. But what if we want to compare fallouts over time of different user journeys?

<!-- /wp:paragraph -->

<!-- wp:paragraph -->

Let's say we run an online business that sells kittens. We mainly sell kittens through our iPhone and Android apps, as well as our website.

<!-- /wp:paragraph -->

<!-- wp:image {"id":315,"align":"center"} -->

<figure class="aligncenter"><img src="{{ site.baseurl }}/assets/images/2018/11/animals-cats-cute-45170.jpg" alt="" class="wp-image-315"><br>
<figcaption>Generic-kitten-image.jpg</figcaption>
</figure>

<!-- /wp:image -->

<!-- wp:paragraph -->

In my workspace below, I have three separate trended fallouts for three separate hypothetical user journeys. The one on the left is for users of our iPhone app, the middle for the Android app and the last are visitors to our website.

<!-- /wp:paragraph -->

<!-- wp:image {"id":311} -->

<figure class="wp-block-image"><img src="{{ site.baseurl }}/assets/images/2018/11/Multiple-trended-fallouts-1.png" alt="" class="wp-image-311"><br>
<figcaption>From left to right: iPhone users, Android users, Website users<br>(Yes they all look the same - it's demo data - but you get the point)</figcaption>
</figure>

<!-- /wp:image -->

<!-- wp:paragraph -->

This looks fancy, but it is hard to see which of our apps or website is performing better over time.

<!-- /wp:paragraph -->

<!-- wp:paragraph -->

It would be great to see these three journey fallouts on the same graph, so we can see which is performing better than others over time. Surely we can just put them onto a single graph?

<!-- /wp:paragraph -->

<!-- wp:paragraph -->

I actually reached out to Adobe Client Care and in a 100 word email response they essentially said "no you can't do that in workspace" and that it was "technically impossible". The source data from a graph can only come from a single workspace table, and as each fallout report is treated as a separate table, it is currently not possible.

<!-- /wp:paragraph -->

<!-- wp:paragraph -->

Faced with the prospect of having to tell my stakeholders that they would need to export the data and build the graph manually in excel, I decided to ignore Client Care and try to build the graph in workspace anyway.&nbsp;

<!-- /wp:paragraph -->

<!-- wp:paragraph -->

_Fast forward 30 minutes..._

<!-- /wp:paragraph -->

<!-- wp:image {"id":312} -->

<figure class="wp-block-image"><img src="{{ site.baseurl }}/assets/images/2018/11/Multiple-fallouts-trended-adobe-analytics.png" alt="" class="wp-image-312"></figure>

<!-- /wp:image -->

<!-- wp:paragraph -->

BOOM! Take that, Adobe Client Care! "Impossible is nothing".

<!-- /wp:paragraph -->

<!-- wp:paragraph -->

So, how did I do it? Well it ended up being a bit of a hack using custom segments and calculated metrics but I figured it may be useful for some others in the future, so here are the steps, in pictures. Note this example is calculating the % fallout using the visitors metric, but you can apply it to calculate the absolute figures as well.

<!-- /wp:paragraph -->

<!-- wp:paragraph -->

1.Set up each of your fallout reports

<!-- /wp:paragraph -->

<!-- wp:image {"id":306} -->

<figure class="wp-block-image"><img src="{{ site.baseurl }}/assets/images/2018/11/Multiple-trended-fallouts.png" alt="" class="wp-image-306"><br>
<figcaption>Here are three trended fallouts for our 'Kitten Purchase' user journey (Note: demo data)</figcaption>
</figure>

<!-- /wp:image -->

<!-- wp:paragraph -->

<!-- /wp:paragraph -->

<!-- wp:paragraph -->

2. Create a custom segment from the final step of each fallout (right click on the step in the fallout report and select 'create segment from touchpoint')

<!-- /wp:paragraph -->

<!-- wp:image {"id":307,"align":"center","width":255,"height":436} -->

<figure class="aligncenter is-resized"><img src="{{ site.baseurl }}/assets/images/2018/11/Custom_segment.png" alt="" class="wp-image-307" width="255" height="436"></figure>

<!-- /wp:image -->

<!-- wp:paragraph -->

3. Save each custom segment with a sensible sounding name, like 'Fallout 1 to Complete'. You should now have a custom segment for each fallout.

<!-- /wp:paragraph -->

<!-- wp:paragraph -->

4. Create a calculated metric from each of the custom segments. In this step you are essentially recreating the calculated % in the final step of the fallout report as a calculated metric. To do so, you will need to have the metric take the visitors in the first step of the fallout, divided by the visitors from your custom segment.

<!-- /wp:paragraph -->

<!-- wp:image {"id":320} -->

<figure class="wp-block-image"><img src="{{ site.baseurl }}/assets/images/2018/11/Calculated-metric-1.png" alt="" class="wp-image-320"></figure>

<!-- /wp:image -->

<!-- wp:paragraph -->

<!-- /wp:paragraph -->

<!-- wp:paragraph -->

5. Save each calculated metric with a sensible sounding name, like 'Fallout 1 Completed %'. You should now have a calculated metric for each fallout.

<!-- /wp:paragraph -->

<!-- wp:paragraph -->

6. Verify the calculated metric is calculating the fallout correctly. You can do this by picking a few dates and checking the number in the calculated metric builder matches the number when you trend that fallout.

<!-- /wp:paragraph -->

<!-- wp:paragraph -->

7. In a new freeform table in workspace, add each custom metric.

<!-- /wp:paragraph -->

<!-- wp:image {"id":313} -->

<figure class="wp-block-image"><img src="{{ site.baseurl }}/assets/images/2018/11/Custom_metric_table.png" alt="" class="wp-image-313"></figure>

<!-- /wp:image -->

<!-- wp:paragraph -->

<!-- /wp:paragraph -->

<!-- wp:paragraph -->

8. Trend the custom metrics to get your graph, then bask in your glory knowing that you've achieved something that Adobe considered impossible.

<!-- /wp:paragraph -->

<!-- wp:image {"id":314} -->

<figure class="wp-block-image"><img src="{{ site.baseurl }}/assets/images/2018/11/Multiple-fallouts-trended-adobe-analytics-1.png" alt="" class="wp-image-314"></figure>

<!-- /wp:image -->

