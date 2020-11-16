---
layout: post
title: 'Cohort analysis: Adobe Analytics vs Tableau'
date: 2018-10-24 13:55:10.000000000 +11:00
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
  _yoast_wpseo_content_score: '60'
  _yoast_wpseo_primary_category: ''
  _thumbnail_id: '290'
  _yoast_wpseo_focuskw_text_input: cohort analysis
  _yoast_wpseo_focuskw: cohort analysis
  _yoast_wpseo_linkdex: '83'
author:
permalink: "/cohort-analysis-adobe-analytics-vs-tableau/"
---
<!-- wp:paragraph -->

[Cohort analysis](https://en.wikipedia.org/wiki/Cohort_analysis) is useful to track changes in groups of metrics over time. A good example is user engagement – do users who joined in January stay as engaged as users who joined in October? However, depending on how your data is stored and collected, it can be tricky to run.

<!-- /wp:paragraph -->

<!-- wp:paragraph -->

Both Google Analytics and Adobe Analytics have inbuilt templates to run cohort analysis. In Adobe, building the report is as simple as selecting two metrics, a date range and clicking ‘Build’. Total build time: 3-5 minutes. The end result is a nicely formatted cohort table which can reveal surprising insights.

<!-- /wp:paragraph -->

<!-- wp:image {"id":287,"linkDestination":"media"} -->

<figure class="wp-block-image"><a href="https://www.keithyap.com.au/wp-content/uploads/2018/10/cohort1.png"><img src="{{ site.baseurl }}/assets/images/2018/10/cohort1.png" alt="" class="wp-image-287"></a><br>
<figcaption>Cohort analysis in Adobe Analytics Workspace</figcaption>
</figure>

<!-- /wp:image -->

<!-- wp:paragraph -->

These template do have their limitations however:

<!-- /wp:paragraph -->

<!-- wp:list -->

- You can’t run more than 12 cohorts (or time periods) at one time
- You are limited to running them against the default, out of the box metrics
- The format you are given, while nice, is essentially fixed ([Adobe’s last update](https://marketing.adobe.com/resources/help/en_US/analytics/analysis-workspace/new-features-in-analysis-workspace.html#concept_AB1896F08E4544668A3FA68C39AC8761) did allow you to change the colour of the shading, which is cute)

<!-- /wp:list -->

<!-- wp:paragraph -->

So what do you do if you run up against one of these limitations? You’ll have to download the data and run your own analysis. Below is a quick overview of how you would approach this using Tableau.

<!-- /wp:paragraph -->

<!-- wp:paragraph -->

1. Download the data from AdobeAnalytics (probably via Data Warehouse) – at a minimum you will want date/time,visits and one other metric of your choice.

<!-- /wp:paragraph -->

<!-- wp:paragraph -->

2. In a blank excel workbook, make a list of numbers from 1 till the maximum number of time periods you want to compare you cohorts against. In this example, we’ve gone with 15 which is 3 more than Adobe will allow us to do.

<!-- /wp:paragraph -->

<!-- wp:image {"id":288,"align":"center"} -->

<figure class="aligncenter"><img src="{{ site.baseurl }}/assets/images/2018/10/cohort2-203x300.png" alt="" class="wp-image-288"><br>
<figcaption>Step 2</figcaption>
</figure>

<!-- /wp:image -->

<!-- wp:paragraph -->

3. Add your Adobe data export as well as the blank workbook to Tableau, and join them using a 1 = 1 clause

<!-- /wp:paragraph -->

<!-- wp:image {"id":289,"align":"center"} -->

<figure class="aligncenter"><img src="{{ site.baseurl }}/assets/images/2018/10/cohort3.png" alt="" class="wp-image-289"></figure>

<!-- /wp:image -->

<!-- wp:paragraph -->

4. Now for the tricky part! Depending on how you build your cohort analysis, at this stage you’ll need to create one or more calculated fields in Tableau. These will probably include:

<!-- /wp:paragraph -->

<!-- wp:list -->

- a ‘first visit’ flag
- a ‘last visit’ flag
- a ‘users’ calculation
- a ‘retained user’ flag
- a ‘percentage’ calculation

<!-- /wp:list -->

<!-- wp:paragraph -->

You will more than likely need to use the 'fixed' Level of Detail (LOD) in your Tableau calculations. If you aren’t familiar with these there is [more info on LOD calculations from Tableau.](https://onlinehelp.tableau.com/current/pro/desktop/en-us/calculations_calculatedfields_lod_overview.html) There is also an excellent example workbook that has been shared on the [Tableau forums](https://community.tableau.com/thread/255339) if you need a workbook to follow.

<!-- /wp:paragraph -->

<!-- wp:paragraph -->

5. To build the cohort visualisation, you will want:

<!-- /wp:paragraph -->

<!-- wp:list -->

- ‘users’ as well as Dates as discrete dimensions in Rows
- The imported list of numbers as a discrete dimension in Columns
- The AGG ‘percentage’ as a colour and label mark
- The SUM of ‘retained users’ as a detail mark

<!-- /wp:list -->

<!-- wp:image {"id":290,"width":940,"height":381,"linkDestination":"media"} -->

<figure class="wp-block-image is-resized"><a href="https://www.keithyap.com.au/wp-content/uploads/2018/10/cohort4.png"><img src="{{ site.baseurl }}/assets/images/2018/10/cohort4.png" alt="" class="wp-image-290" width="940" height="381"></a><br>
<figcaption>The completed cohort analysis in Tableau</figcaption>
</figure>

<!-- /wp:image -->

<!-- wp:paragraph -->

After all that, you can now appreciate that building a cohort analysis in Tableau is a fair bit more work than simply clicking a few buttons in Adobe Analytics. I’d say the total build time for an experienced Tableau user would be at least a few hours for the first run, not including the time needed to export to Data Warehouse and get it into Tableau.

<!-- /wp:paragraph -->

<!-- wp:paragraph -->

As such, I’d recommend sticking to running cohort analysis in Adobe Analytics unless one of the limitations is an absolute deal break for your analysis.

<!-- /wp:paragraph -->

