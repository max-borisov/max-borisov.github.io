---
layout: post
title: "Sass in your projects"
date: 2014-10-09 08:13:51 +0300
comments: true
categories: 
---
The other day I have open for myself a [Sass](http://sass-lang.com/) tool. I knew about it, but there was no a good reason to start using it. Until this time. 

I have a project where we use a bunch of css files. I don't spend much creating css code, I update and maintain it instead. It wasn`t a problem but I started to think how to make this process more friendly. And [Sass](http://sass-lang.com/) appeared on the stage. It provides many features to make css development easier such as: **variables**, **nesting** and  **partials**. 

A short example: I have defined several variables and then imported partial files where those variables are used. This file is called **application.scss**.

```
$images-dir: '../images';
$fonts-dir: '../fonts';
$PIE-file: '/frontend/css/PIE.htc';

@import "../base/all";
@import "../base/up";
```

A frontend directory structure:

![sass-yii](/images/posts/sass_yii/sass-yii.png)

### How to install Sass.

Here is a [tutorial](http://sass-lang.com/install "Install Sass") how it can be done.

If everything was done correct this code(in terminal) will show a **sass** version.

```
sass -v
```

In my particular case I have already had a project with complete css styles. To start to write css in a new way I had to reformate it before(make a sass compatible). 
If you have instaled **sass**, it means you also have a tool **sass-convert** which helps you convert existing css files to scss format.

```
sass-convert -F css -T scss frontend/existing_css frontend/scss
```

This command converts all css files to scss format. After that you can refactor them, if you want, and use a new syntax to create rules.

This command will convert all scss to css.

```
sass --style compact --no-cache --update frontend/scss:frontend/css
```

There are several ways how to convert your scss to css.

##### Manually update using terminal
How to make it was shown above.

##### Use File watchers. For those who uses PHPStorm
![phpstorm-file-watcher](/images/posts/sass_yii/phpstorm-file-watcher.png)

##### Convert files on the fly each time a page was requested
In **PHP** there is a function called [exec()](http://php.net/manual/en/function.exec.php) which can be used to run system commands. In my particular case a project is built upon [Yii framework](http://yiiframework.com).
In configuration file **main.php** I put the following code:

```
'onBeginRequest' => function($event) {      
        if (YII_DEBUG) {
			exec('sass --style compact --no-cache --update frontend/scss:frontend/css', $resp);
        }
    },
``` 





