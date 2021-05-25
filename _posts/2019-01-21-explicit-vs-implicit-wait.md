---
layout: post
title:  "Explicit or Implicit wait in Selenium"
description: "A discussion about correct Selenium wait strategy"
author: philip
categories: [ Selenium, Automation ]
image: assets/images/waittypes.jpg
tags: automation
---

Explicit or Implicit, whichever wait you are using, be careful not to mix them up. That means if you have instructed the driver to implicitly wait for an element, then you should not later user any kind of explicit wait in your tests. The resason is that implicit wait is applied to the driver and explicit wait is directed by your test/ program scripts. When they mix up you will get unexpected results. 

Implicit wait would cause a delayed start and generally advised not to be used. Also different browsers implement implicit wait in different ways and a consistent performace is not guaranteed. 

There is no surprise if your automation is running terribly slow if you mix these two different types of waits together

