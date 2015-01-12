---
layout: post
title: "gem nokogiri install error"
date: 2015-01-12 12:45:36 +0200
comments: true
categories: 
---
Recently I tried  to install the nokogiri rails gem and got the error:

```
ERROR: Error installing nokogiri:
ERROR: Failed to build gem native extension.
```  

There also was a long text describing what is also was wrong. And I found another hint:

```
libxml2 is missing. Please locate mkmf.log to investigate how it is failing.
``` 

So, what I did to solve this problem:

```
brew install libxml2 libxslt
```

And run this command:

```
NOKOGIRI_USE_SYSTEM_LIBRARIES=1 gem install nokogiri -- --use-system-libraries --with-iconv-dir=/usr/lib --with-xml2-config="$(brew --prefix libxml2)/bin/xml2-config" --with-xml2-include="$(brew --prefix libxml2)/include/libxml2" --with-xslt-config="$(brew --prefix libxslt)/bin/xslt-config"
```

After that I could install nokogiri.

Here is also a [tutorial how to install nokogiri.](http://www.nokogiri.org/tutorials/installing_nokogiri.html)
