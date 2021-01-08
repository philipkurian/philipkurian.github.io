---
layout: post
title:  "Explicit or Implicit wait"
description: "A discussion about correct Selenium wait strategy"
author: philip
categories: [ Jekyll, tutorial ]
image: https://images.unsplash.com/photo-1523740856324-f2ce89135981?ixlib=rb-1.2.1&auto=format&fit=crop&w=798&q=80
tags: automation
---

Explicit or Implicit, whichever wait you are using; be careful not to mix them up. That means if you have instructed the driver to implicitly wait for an element, then you should not later user any kind of explicit wait in your tests. 

