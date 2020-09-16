---
layout: post
title: Exluding SQL results with Left Outer Join
date: 2019-12-05 00:17:37.000000000 +11:00
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- SQL
tags: []
meta:
  _yoast_wpseo_content_score: '90'
  _yoast_wpseo_primary_category: '11'
  _edit_last: '1'
author:
permalink: "/exluding-sql-results-with-left-outer-join/"
---
<!-- wp:paragraph -->

Imagine you have a data set 'a' which contains data from another data set 'b'. You want to retrieve the data that exists in 'a' but not in b. This can be accomplished using a left outer join filtering on where b is null:

<!-- /wp:paragraph -->

<!-- wp:preformatted -->

```
LEFT OUTER JOIN b ON a.key=b.key WHERE b.key IS NULL
```

<!-- /wp:preformatted -->

