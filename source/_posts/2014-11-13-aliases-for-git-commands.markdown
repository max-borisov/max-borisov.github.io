---
layout: post
title: "Aliases for Git commands."
date: 2014-11-13 23:09:27 +0200
comments: true
categories: 
---
I used to type full git commands in console.
But there is a way to make short forms by using git aliases.
Like this:

```
git config --global alias.ci commit
git config --global alias.co checkout
git config --global alias.pl pull
git config --global alias.ph push
git config --global alias.mr merge
```

And use them like that:

```
git ci
git co
git mr
```