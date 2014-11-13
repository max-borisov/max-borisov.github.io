---
layout: post
title: "How to set up a form input value with PHPUnit Selenium2TestCase"
date: 2014-10-16 15:26:54 +0300
comments: true
categories: 
---

If you use PHPUnit_Extensions_Selenium2TestCase for functional test and there is a need to update a specific value for, let's say, input text field, you need at first clear it and only after that set a new value.

Example:

```
$this->byCssSelector('#content form input[name="user"]')->clear();
$this->byCssSelector('#content form input[name="user"]')->value(10);
```
