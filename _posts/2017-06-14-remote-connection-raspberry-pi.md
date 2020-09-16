---
layout: post
title: Remote connection to Raspberry Pi
date: 2017-06-14 02:27:04.000000000 +10:00
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories: []
tags: []
meta:
  _jetpack_related_posts_cache: a:1:{s:32:"8f6677c9d6b0f903e98ad32ec61f8deb";a:2:{s:7:"expires";i:1525715023;s:7:"payload";a:3:{i:0;a:1:{s:2:"id";i:5;}i:1;a:1:{s:2:"id";i:140;}i:2;a:1:{s:2:"id";i:193;}}}}
  _yoast_wpseo_content_score: '60'
  _yoast_wpseo_primary_category: ''
  _wpas_done_all: '1'
  _edit_last: '1'
  dsq_thread_id: '5908411873'
author:
permalink: "/remote-connection-raspberry-pi/"
---
### Easy SSH when your computer and your PI are on the same network (wifi)

Mac/Linux: Open the terminal

Windows: Install Putty

Ensure the pi is turned on and connected to network

Find the ip address of the pi

SSH into the ip address to port 22

* * *

### Remote SSH when not on the same network

Android: Install Juice SS

Windows: Install Putty

Register for weaved account

Follow weaved instructions for installing on pi using the terminal

Add SSH service to weaved from terminal on Pi

Copy login details to Putty, Juice SSH

Login is ‘pi’, password default is ‘raspberry’.

Note: Whenever the pi restarts, the port details will change. Check your weaved account for the current port number.

Similar writeup: [http://readwrite.com/2014/04/09/raspberry-pi-projects-ssh-remote-desktop-static-ip-tutorial/#awesm=~oHt6ZNCfyofCiA](http://readwrite.com/2014/04/09/raspberry-pi-projects-ssh-remote-desktop-static-ip-tutorial/#awesm=~oHt6ZNCfyofCiA)

