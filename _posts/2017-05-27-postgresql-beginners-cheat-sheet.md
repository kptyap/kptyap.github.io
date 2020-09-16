---
layout: post
title: PostgreSQL Beginner's Cheat Sheet
date: 2017-05-27 06:48:23.000000000 +10:00
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories: []
tags: []
meta:
  _jetpack_related_posts_cache: a:1:{s:32:"8f6677c9d6b0f903e98ad32ec61f8deb";a:2:{s:7:"expires";i:1525788604;s:7:"payload";a:3:{i:0;a:1:{s:2:"id";i:231;}i:1;a:1:{s:2:"id";i:54;}i:2;a:1:{s:2:"id";i:5;}}}}
  _edit_last: '1'
  _yoast_wpseo_content_score: '30'
  _yoast_wpseo_primary_category: ''
  _wpas_done_all: '1'
  dsq_thread_id: '5854618577'
author:
permalink: "/postgresql-beginners-cheat-sheet/"
---
Terminal commands:

Launch PostgreSQL terminal - psql

Copy table from one db to another -&nbsp;pg\_dump -t table\_name&nbsp;copyfrom\_db\_name | psql&nbsp;copyto\_db\_name

&nbsp;

PSQL commands:

List databases - \d

List tables in current database - \dt

List table structure - \d table\_name

List table contents - TABLE table\_name;

Connect to a different database - \c database\_name

&nbsp;

&nbsp;

