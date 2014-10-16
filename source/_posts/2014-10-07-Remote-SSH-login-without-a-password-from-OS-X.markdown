---
layout: post
title: "Remote SSH login without a password from OS X"
date: 2014-10-07 18:56:53 +0300
comments: true
categories: 
---

There are several ways to connect from OS X via ssh to remote server with no need to specify a password each time.

This article from [DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys--2 "DigitalOcean - How to set up ssh keys") covers how to generate ssh public key and copy it to a server.
One of the ways is to copy a new key by using [ssh-copy-id](https://github.com/beautifulcode/ssh-copy-id-for-OSX) tool. But MaсOS does not shipped with it. 

You can install it manually

``` 
sudo curl https://raw.github.com/beautifulcode/ssh-copy-id-for-OSX/master/ssh-copy-id.sh -o /usr/local/bin/ssh-copy-id 
sudo chmod +x /usr/local/bin/ssh-copy-id
```
or use [Macports](https://www.macports.org/) tool

```
sudo port install openssh +ssh_copy_id
```

If you followed instruction and your public ssh key was copied to the server, check this file.

```
~/ssh/authorized_key
```

It should not be empty.

Then try to connect to server. 












