---
layout: post
title: "Automatically run commands after ssh login"
date: 2014-10-07 20:28:40 +0300
comments: true
categories: 
---

On your Linux server put the code in ~/.bashrc or /etc/bash.bashrc to to run commands for all users:

```
if [[ -n $SSH_CONNECTION ]] ; then
    echo "I'm logged in!"
    # put commands here 
fi
```