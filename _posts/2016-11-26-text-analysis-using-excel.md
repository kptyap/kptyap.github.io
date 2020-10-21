---
layout: post
title: Text Analysis using Excel
date: 2016-11-26 03:35:04.000000000 +11:00
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
  _jetpack_related_posts_cache: a:2:{s:32:"8f6677c9d6b0f903e98ad32ec61f8deb";a:2:{s:7:"expires";i:1526335035;s:7:"payload";a:3:{i:0;a:1:{s:2:"id";i:231;}i:1;a:1:{s:2:"id";i:24;}i:2;a:1:{s:2:"id";i:180;}}}s:32:"0fc297954b162181672663da43ebaa6c";a:2:{s:7:"expires";i:1526346550;s:7:"payload";a:3:{i:0;a:1:{s:2:"id";i:231;}i:1;a:1:{s:2:"id";i:24;}i:2;a:1:{s:2:"id";i:180;}}}}
  _jetpack_dont_email_post_to_subs: '1'
  _yoast_wpseo_content_score: '30'
  _yoast_wpseo_primary_category: ''
  dsq_thread_id: '5497963969'
  _thumbnail_id: '21'
  _yoast_wpseo_linkdex: '67'
  _yoast_wpseo_metadesc: Perform simple text analysis in excel. Word clouds, word
    and sentence counts, topic modelling, sentiment analysis and more.
  _yoast_wpseo_focuskw: text analysis in excel
  _yoast_wpseo_focuskw_text_input: text analysis in excel
author:
permalink: "/text-analysis-using-excel/"
---
- [Word Counts](https://www.keithyap.com.au/text-analysis-using-excel#word-counts)
- [Word Clouds](https://www.keithyap.com.au/text-analysis-using-excel/#word-clouds)
- [Sentence Counts](https://www.keithyap.com.au/text-analysis-using-excel/#Sentence-counts)
- [Sentiment Analysis](https://www.keithyap.com.au/text-analysis-using-excel/#sentiment-analysis)
- [Topic Modelling](https://www.keithyap.com.au/text-analysis-using-excel/#topic-modelling)
- [Combining it all together](https://www.keithyap.com.au/text-analysis-using-excel/#combine)

> _Below is a summary of my explorations using excel for text analysis. The example used in this article focuses on customer feedback for a hypothetical bank’s mobile app, however the methods described here could be used to analyse any body of text (or corpus_**_)_** _in excel._

There are plenty of companies out there that claim to offer complete end to end text analysis solutions to ‘help you uncover actionable insights from customer feedback’. These solutions tend to vary wildly in sophistication and usefulness, from the downright useless to the one or two that are at the cutting edge of text analysis. What they all have in common though, is that you will eventually need to pay to access their services. Most likely, you will also have to upload your customer feedback, which may be quite sensitive, onto their platforms and servers.

Fortunately, one is able to run decent text analysis from the comfort of excel. Below is a quick guide to the types of analysis you can run, ranging from easy to hard.

Before trying any of these, make sure your body of feedback has been spell checked. Customer written feedback is rarely without spelling or grammatical error.

&nbsp;

#### Word counts in excel (or very basic topic modelling)

Simple word count of unique word occurrences can go a long way towards uncovering the overall themes in the text, once common words (eg. ‘a’, ‘the’, ‘is’, etc.) are removed.

1. Split the body of text into single words (Consultant Robert Mundigl has made a [handy macro](http://www.clearlyandsimply.com/clearly_and_simply/2015/03/the-implementation-of-word-clouds-with-excel.html)that does just this)
2. Count the number of each word occurrence using a Pivot Table. Select the column of single words and create a pivot table with the word column being in both ‘rows’ and ‘values’ of the pivot, then sort descending (if using Robert’s tool this is done for you).
3. Review the top word occurrences and discard common or superfluous words not that may cloud your analysis.

Optional: It may then be helpful to create a simple bar chart to visually see the occurrences of words relative to each other.


<img src="{{ site.baseurl }}/assets/images/2016/11/1-90ST0nvyXRmiSjMXSvzYxw.png" alt="Word count results displayed in a bar chat is a quick way to derive insights from a body of text"> <i>Word count results displayed in a bar chart is a quick way to derive insights from a body of text</i>

&nbsp;
#### Word clouds in&nbsp;Excel

A word cloud is basically a fancy way to display a word count. In terms of actual usefulness for text analysis, a word count and associated bar chart is far more insightful. However, word clouds do look pretty. If you are set on creating a word cloud, consultant Robert Mundigl has created a [handy excel template and accompanying article](http://www.clearlyandsimply.com/clearly_and_simply/2015/02/word-clouds-with-microsoft-excel.html) on how to do so.

![Example word cloud from excel]({{ site.baseurl }}/assets/images/2016/11/1-nfoVPlQK3QjrvkcwjkKRaA.png)

<figure class="graf graf--figure"></figure>
&nbsp;
#### Sentence counts

This can be a useful precursor to the sentiment analysis and topic modelling methods below. If your body of text is broken down sentence by sentence (eg. a body of survey responses) it may be useful to eliminate the responses that have too few words to be useful in analysis. The formula below returns the number of words in a cell (A1).

```
=LEN(a1)-LEN(SUBSTITUTE(a1," ",""))+1
```

You can then filter out all sentences below a certain word count.

<img src="{{ site.baseurl }}/assets/images/2016/11/1-BcFTg9H4d-5ub5liXONe6g.png" alt="Screenshot of Filtering out any feedback less than 3 words in length as they do not add to our analysis and only create noise">
<i>Filtering out any feedback less than 3 words in length as they do not add to our analysis and only creates noise</i>

&nbsp;
#### Sentiment Analysis

When we read a sentence, we can usually infer from the subjective information supplied what the sentiment, or mood, of that sentence is.

> Eg1. Your banking app is crap, I’ve seen other banks do better = negative

> Eg2. The banking app does the job. Would like a chat option though = neutral

> Eg3. Awesome! Love your app ever since the fingerprint login update= positive

Sentiment analysis **is** possible in excel, albeit with a caveat — you need to have accompanying scores to go with your feedback. Let’s look at the examples again, this time with a numbered score next to each. The number is the rating that particular customer gave when providing their feedback; this could be in response to a quantitative question such as a 1–10 satisfaction or Net Promoter Score (**NPS)** question:

> Eg1. Your banking app is crap, I’ve seen other banks do better ~ 2

> Eg2. The banking app does the job. Would like a chat option though ~ 5

> Eg3. Awesome! Love your app ever since the fingerprint login update ~ 9

Depending on how we wish to categorise customer sentiment, we can now do so by simply applying their number rating to their feedback.

![Screenshot of Feedback with sentiment derived from the previous quantitative question]({{ site.baseurl }}/assets/images/2016/11/1-Uowi2I7spX_iEJ7OSBRuTw.png) Feedback with sentiment derived from the previous quantitative question

In the example above, a nested IF statement is used to assign the ‘sentiment’ (or in this example, the [NPS category](https://www.netpromoter.com/know/)) to each response:

```
=IF(B1\>8,"PROMOTER",IF(B1\>6,"PASSIVE","DETRACTOR")))
```

You are then free to categorise feedback by sentiment category.


<img src="{{ site.baseurl }}/assets/images/2016/11/1-NqyPW7jAl11XuNYAAs5few.png" alt="Screenshot of Using a pivot table we can filter all detractor comments to see which areas of improvement we should focus on"> 
<i>Using a pivot table we can filter all detractor comments to see which areas of improvement we should focus on</i>


This method is by no means perfect; constructive feedback may be left even after a customer has given a low rating, and likewise a complaint may be made by the same customer who has given a high rating. However, from my experience it returns accurate results more than 80% of the time, _as long as the quantitative rating question is asked right before the open text feedback question._

True sentiment analysis derived purely from the text itself is unfortunately outside the capabilities of excel, to my knowledge. If your text is fairly linear, it may be possible to build up a library of sentiment triggering words and feed that into a large decision making macro to come up with a sentiment. Otherwise, the only alternative will be to use proper text analysis solutions.

&nbsp;
#### Theme / Topic modelling in&nbsp;excel

When we read a sentence, we can usually infer from the subjective information and context supplied what the overall themes or topics are.

> Eg1. Your banking app is crap, I’ve seen others do better ~ ‘Competitors’, ‘App’

> Eg2. The app does the job. Would like a live chat option though ~ ‘Chat’, ‘App’

> Eg3. Awesome! Love your app ever since the fingerprint login update ~ ‘Fingerprint login’, ‘App’

Topic modelling is a form of text mining to identify patterns and hence topics in a body of text without needing to read it; it is an entire area of linguistic research in its own right. And any online text analysis solution that can do this even partially well currently requires a powerful semantic and linguistic processing engine, backed up by extensive database of topics.

However, if you know your body of text well enough, and it is sufficiently narrow, topic modelling is possible in excel.

1. Organise your feedback with individual responses on separate rows. If you have accompanying feedback scores, make sure these sit on the same row. This will be the **Analysis** sheet.
2. Set up the topics in a separate sheet. This will be the **Topic Models** sheet. The first row of the sheet should contain the individual topic titles. In each column, under each title, list out the words that correspond to the topic.

<img src="{{ site.baseurl }}/assets/images/2016/11/1-88mobO2wgdE1maMIUOBcVQ.png" alt="List of A simple topic model"><i> A simple topic model</i>

3. Define each group, setting the title as the name for the group. Each of these will be a **Topic Group.**


<img src="{{ site.baseurl }}/assets/images/2016/11/1-ZzPdOaeZ35UHVt_yKx5VuQ.png" alt="Screenshot of Using excel's names feature to make topic groups"><i> Use excel’s inbuilt Names feature to use as your Topic Groups. You can use either the ‘Define Name’ function (pictured) or the ‘Create from Selection’ function underneath. Both will achieve the same result.</i>

3. Copy and paste the first row containing the topic titles into the Analysis sheet, alongside the feedback.

4. Command excel to take each response and match it against the topics which we have defined. If a word in a topic matches, then return the title of the Topic Group in each corresponding cell.

```
=IF(SUMPRODUCT(--ISNUMBER(SEARCH(Topic Group,Feedback)))\>0,Title of Topic Group,""))
```

<img src="{{ site.baseurl }}/assets/images/2016/11/1-TrgE3o3x3Fddx4CbsIgxbA.png" alt="Screenshot of the formula at work"><i> The formula at work matching the feedback to our pre-defined topic. Note the anchors ($) in the formula, this is necessary to copy the formula across and down.</i>

&nbsp;
In the example above, for cell E2:

```
=IF(SUMPRODUCT( — ISNUMBER(SEARCH(NFC,$B2)))\>0,E$1,””)
```

5. Copy the formula lengthways and down-ways (making sure to anchor the relevant cells correctly). Unfortunately you will need to manually edit the name of each Topic Group you call (or code a macro to automate this).

6. Summarise the calls at the bottom of your topic matrix.

7. Use pivot tables and graphs to present a nice summary. In the example below, we can instantly see that Quick Balance and NFC are the two major topics that our customers are talking about

&nbsp;


<img src="{{ site.baseurl }}/assets/images/2016/11/1-D-IWjeVFalKS_Jllbsz-jw.png" alt="Example feedback for mobile app in excel"> <i>Our feedback can now be read at a glance</i>

&nbsp;
#### Extra: Dynamic Topic Modelling without Defined Names

Editing topics with this setup can be cumbersome at times, as the name ranges we have set for our topics above have to be manually reset every time we add or subtract a topic from a topic set. By using the OFFSET function we can set up topic to dynamically resize depending on the number of topics we have, without needing to manage topics using the Name Manager. First, in our 'Topics' sheet we add a 'Topic Word Counts' row which contains a COUNTA formula of each topic column.

<img src="{{ site.baseurl }}/assets/images/2016/11/counta-topics-model.png" alt="COUNTA in the Topics sheet of the workbook">
    <br>
    <i>COUNTA in the Topics sheet of the workbook</i>

In the main topic matching sheet, we pull through these topic word counts. Lastly, we modify the matching formula in the main matching sheet.

<img src="{{ site.baseurl }}/assets/images/2016/11/Offset-matching.png" alt="updated main sheet with topic word count"><i>The updated Main sheet, with the topic word count pulled in as well as the updated matching formula with OFFSET</i>

Building it this way means we can modify our topic word lists and the matching formula will automatically adjust for the new matching list. Many thanks to reader Andrew Ward for coming up with this improvement and sharing it.

&nbsp;
#### Combining it all&nbsp;together

By joining sentiment analysis and topic modelling, we can generate lists of topics important to our happy customers (promoters) or customers at risk of leaving (detractors). The below example uses the previously discussed sentiment grouping to add further insight to the feedback. You can now also use filters to sort and read feedback by topic groups.


<img src="{{ site.baseurl }}/assets/images/2016/11/1-y_q83Ds1JeqVJDjz95qH_A.png" alt="Filtering and sorting feedback graph"><i>Filtering for promoter feedback only, we can see that Quick Balance is the main feature that currently delights our customers.</i>

If you'd like to explore and play around with the formulas and methods described in this article, the below excel sheet was used to create the examples in this article and should be a good starting point:

[email-download download\_id=”264” contact\_form\_id=”267”]

&nbsp;

If this article has helped you in any way, or if you have any feedback on how it could be improved, please leave a comment below!

