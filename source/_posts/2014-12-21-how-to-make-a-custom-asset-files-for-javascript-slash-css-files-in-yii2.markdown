---
layout: post
title: "How to make a custom Asset files for javascript/css files in Yii2"
date: 2014-12-21 18:20:18 +0200
comments: true
categories: 
---
For example, we have a such task: use any javascript library to make image gallery. And the site is running [Yii 2 framework](http://www.yiiframework.com/).
It may seems too easy: just find any suitable jquery plugin and include it. But there is another, more beatuful, way how to accomplish it.

We can use a [bower](http://bower.io/) (a package manager for client side) to install and manage plugins we need. But Yii 2 comes with composer which will help us. We will edit config file and specify what bower packages do we need and they will be installed.

What we need to do:

1. Install new bower package
2. Make Asset to manage and include new files
3. Use Asset in the application 

####Install bower packages
I have decided to use [ekko-lightbox](http://ashleydw.github.io/lightbox). On the [search page](http://bower.io/search/) we can check if that plugin is available for the bower. And it is.

So we need to update **require** section of **composer.json** file and set a plugin name.

```
"require": {
        "php": ">=5.4.0",
        "yiisoft/yii2": "*",
        "yiisoft/yii2-bootstrap": "*",
        "yiisoft/yii2-imagine": "*",
        "yiisoft/yii2-codeception": "*",
        "bower-asset/ekko-lightbox": "*"
    },
```

Then run command

```
composer install
```

After that check the **vendor/bower** directory. 

![vendor-bower directory](/images/posts/yii2-assets/bower.png)

From now we can include javascript/css files using **$this->registerJs()** method in any view file.

But we are going to use [assets](http://www.yiiframework.com/doc-2.0/guide-structure-assets.html).

To make a new one create a file called **LightBoxAsset.php** under assets directory. And put the code below.

```
namespace app\assets;

use yii\web\AssetBundle;

class LightBoxAsset extends AssetBundle
{
    public $sourcePath = '@bower/ekko-lightbox';
    public $baseUrl = '@web';
    public $css = [
        'dist/ekko-lightbox.min.css',
    ];
    public $js = [
        'dist/ekko-lightbox.min.js',
   
```

**@bower** alias represents a path to the vendor/bower directory.
We use $css ans $js properties to specify what files should be included.

Then we update application main asset file **AppAsset.php** and make it dependes on the asset we just created.

```
namespace app\assets;

use yii\web\AssetBundle;

class AppAsset extends AssetBundle
{
    public $basePath = '@webroot';
    public $baseUrl = '@web';
    public $css = [
        'css/site.css',
    ];
    public $js = [
    ];
    public $depends = [
        'yii\web\YiiAsset',
        'yii\bootstrap\BootstrapAsset',
        '\app\assets\LightBoxAsset',
    ];
}
```

AppAsset can be loaded like this

```
AppAsset::register($this);
```

After that a new javascript and css files will be appear in the source code of the page.



