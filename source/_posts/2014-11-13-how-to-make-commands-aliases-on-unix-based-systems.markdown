---
layout: post
title: "How to make commands aliases on Unix based systems."
date: 2014-11-13 22:42:26 +0200
comments: true
categories: 
---
Unix based systems can make your life easier allowing you to create aliases for commands/operations you run often.

Just open your profile file with any text editor.

On MacOS

```
nano ~/.profile
```

or Linux

```
nano ~/.bashrc
```

and add your own alias like in examples below.

Here is some examples I use for myself:

```
alias ls="ls -la"
alias octo="cd path_toproject_folder && pwd"
# reload profile
alias rl="source ~/.profile"
# restart Apache server
alias apa="sudo apachectl restart"
alias gb="git branch"
alias sts="git status"
# ssh connect to remote server
alias vds="ssh root@10.11.12.13"
# Start Selenium server
alias selenium="java -jar selenium-server-standalone-2.43.0.jar -browserSessionReuse"
alias r:s="rails server"
alias r:g="rails generate"
alias r:g:c="rails generate controller"
alias r:g:s="rails generate scaffold"
```