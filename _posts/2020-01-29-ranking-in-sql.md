---
layout: post
title: Ranking in SQL
date: 2020-01-29 04:04:05.000000000 +11:00
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories: []
tags: []
meta:
  _yoast_wpseo_content_score: '90'
  _yoast_wpseo_primary_category: ''
  _edit_last: '3'
author:
permalink: "/ranking-in-sql/"
---
<!-- wp:paragraph -->

Rank results by the values in a column:

<!-- /wp:paragraph -->

<!-- wp:preformatted -->

```
SELECT \*, RANK() OVER (PARTITION BY column1 ORDER BY column2 DESC) AS rnk
FROM table
```

<!-- /wp:preformatted -->

<!-- wp:paragraph -->

Restrict the number of results to return only the top or bottom X results

<!-- /wp:paragraph -->

<!-- wp:preformatted -->

```
SELECT \*, RANK() OVER (PARTITION BY column1 ORDER BY column2 DESC) AS rnk
FROM tableSELECT \*
FROM (
 SELECT \*, RANK() OVER (PARTITION BY keywords ORDER BY impressions DESC) AS rnk
 FROM a1
) AS x
WHERE rnk \<= 17
;
```

<!-- /wp:preformatted -->

<!-- wp:paragraph -->

<!-- /wp:paragraph -->

