---
layout: post
title: "gem install mysql2 issue"
date: 2015-01-05 18:22:03 +0200
comments: true
categories: 
---
I tried to create a new Rails app with mysql2 database adapter on MacOS. 
But **bundle install** failed with an error:

```
ERROR: Error installing mysql2:
ERROR: Failed to build gem native extension
```

These actions helped me to solve the problem.

* Install mysql using [brew](http://http://brew.sh/) package manager.

```
brew install mysql
```

* Run this command to ensure the mysql has been installed.

```
brew list
```

This command returns information about package and installation directory.

```
brew info mysql
```

In my case it was **/usr/local/opt/mysql/**.

* Run the command and set path to the mysql config file.

```
gem install mysql2 -- --with-mysql-config=/usr/local/opt/mysql/bin/mysql_config
```
