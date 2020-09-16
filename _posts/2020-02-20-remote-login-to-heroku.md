---
layout: post
title: Remote login to Heroku
date: 2020-02-20 11:43:47.000000000 +11:00
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories: []
tags: []
meta:
  _yoast_wpseo_content_score: '60'
  _edit_last: '1'
  _yoast_wpseo_primary_category: '1'
author:
permalink: "/remote-login-to-heroku/"
---
<!-- wp:paragraph -->

Open terminal, navigate to project folder, assume Heroku CLI and Git installed

<!-- /wp:paragraph -->

<!-- wp:preformatted -->

```
heroku login
heroku git:remote -a 'name of heroku project'
```

<!-- /wp:preformatted -->

<!-- wp:paragraph -->

If using a database:

<!-- /wp:paragraph -->

<!-- wp:preformatted -->

```
heroku addons:create heroku-postgresql:hobby-dev
heroku pg:psql
```

<!-- /wp:preformatted -->

<!-- wp:paragraph -->

<!-- /wp:paragraph -->

