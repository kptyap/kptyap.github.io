---
layout: post
title: Data visualisation with Python and Plotly - The Perth real estate market
date: 2017-10-22 07:14:43.000000000 +11:00
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- Analytics
tags: []
meta:
  _yoast_wpseo_primary_category: ''
  _jetpack_related_posts_cache: a:1:{s:32:"8f6677c9d6b0f903e98ad32ec61f8deb";a:2:{s:7:"expires";i:1526345294;s:7:"payload";a:3:{i:0;a:1:{s:2:"id";i:5;}i:1;a:1:{s:2:"id";i:140;}i:2;a:1:{s:2:"id";i:180;}}}}
  _yoast_wpseo_content_score: '30'
  _edit_last: '1'
  _wpas_done_all: '1'
  _jetpack_dont_email_post_to_subs: '1'
  dsq_thread_id: '6234085596'
  _thumbnail_id: '295'
author:
permalink: "/data-visualisation-python-plotly-perth-real-estate-market/"
---
Python is well known for its data science and analysis capabilities with packages such as [Numpy](http://www.numpy.org/), [Matplotlib](https://matplotlib.org/) and [Pandas](http://pandas.pydata.org/). Each of these packages also offer a variety of graphing and visualisation tools, the majority of which is already very well documented.

Recently, there has been a spate of new visualisation focused packages, some which have been well received and documented, and others, less so. [Plotly](https://plot.ly/), which we will explore in this post, is one of the latter ones.

For this exercise, we will use real-world real estate data of sold properties in the city of Perth, Western Australia.&nbsp;We will use our data to investigate the ever popular question - 'What is the current state of the market in July 2017?'

The general steps in this exercise were:

1. Data is scraped from real estate listing websites using a scraper built in Python using BeautifulSoup over a period of time
2. Data is stored in a PostgreSQL database that can be added to over time
3. For analysis, the database is exported to a Jupyter Notebook which serves as a working environment
4. The plotly package is installed in the Jupyter Notebook

To set some context, our data set looks like this:

![]({{ site.baseurl }}/assets/images/2017/10/Screen-Shot-2017-10-23-at-8.13.27-am.png)

Let's start off by exporting our data out from the PSQL database. While Jupyter Notebook has the ability to link directly to the database, for simplicity in this instance we will export a static CSV that we will upload to our notebook.

```
psql: \copy tablename to 'filename' csv;
```

&nbsp;

We then upload the CSV file to the server that hosts the notebook, and initialise the notebook with the relevant packages

```
import pandas as pd import numpy as np import plotly import plotly.plotly as py from plotly.graph\_objs import \* import plotly.figure\_factory as ff plotly.offline.init\_notebook\_mode(connected=True) df = pd.read\_csv("file\_location") df.head()
```

&nbsp;

For our first attempt, a simple property value over time bar chart.

```
# group dates by week df.Date = pd.to\_datetime(df.Date) - pd.to\_timedelta(7, unit='d') df = df.groupby([pd.Grouper(key='Date', freq='W-MON'), 'Price'])['Type'].count() df = df.reset\_index() # initialise bar chart using Plotly offline mode data = [Bar(x=df.Date, y=df.Price)] plotly.offline.iplot(data, filename='jupyter/basic\_bar')
```

&nbsp;

<iframe src="//plot.ly/~kptyap/1.embed" width="900" height="800" frameborder="0" scrolling="no"></iframe>  
That was pretty straight forward. A chart like this can be created by any other number of programs, so it is not terribly impressive.

Let's try something a little more complex. A nice heatmap delving further into the types of properties being sold.

```
# group data by number of bedrooms per week df = df.groupby(['Bed', pd.Grouper(key='Date', freq='W-MON')])['Type'].count() df = df.reset\_index() # intialise heatmap import plotly.graph\_objs as go data = [go.Heatmap( z=df.Type, x=df.Date, y=df.Bed )] layout = go.Layout( title='Perth properties sold by number of bedrooms (May - Jul 2017)', yaxis = dict( title='Number of beds' ), xaxis = dict( title='Date sold' ) ) fig = go.Figure(data=data, layout=layout) plotly.offline.iplot(fig, filename='datetime-heatmap')
```

<iframe src="//plot.ly/~kptyap/3.embed" width="900" height="800" frameborder="0" scrolling="no"></iframe>  
From this figure, we can see that 3 and 4 bedroom properties dominate the Perth market. We can also see sales volume dropping off towards the end of the month.

This is just the tip of the iceberg in terms of what Plotly can offer. It will be interesting to see where it lands amongst all the other visualisation tools in the market.

&nbsp;

