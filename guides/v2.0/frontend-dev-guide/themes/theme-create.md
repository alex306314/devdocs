---
layout: default  
group: fedg
subgroup: A_Themes
title: 创建一个店面主题
menu_title: 创建一个店面主题
menu_order: 2
version: 2.0
github_link: frontend-dev-guide/themes/theme-create.md
redirect_from: /guides/v1.0/frontend-dev-guide/themes/theme-create.html
---

<h2 id="layout_theme_how-to_overview">What's in this topic 这个专题有什么</h2>

This topic discusses how to create the files that make up a theme, how to add a logo to a theme, and how to size images. 

这个专题讨论如何创建文件来组成一个主题，如何给主题添加一个LOGO，如何调整图片大小

* TOC
{:toc}

<div class="bs-callout bs-callout-info" id="info">
<p>A new theme you create is not applied for your store automatically. You need to apply it manually in the Admin panel. This procedure is described in the <a href="{{page.baseurl}}frontend-dev-guide/themes/theme-apply.html">Apply and configure a theme in Admin</a> topic.
<br>   
你创建的新主题不会自动应用到店面。你需要在管理界面手动应用它。这个操作在专题应用和配置主题专题
</p>
</div>

## Prerequisites 先决条件

1. For the sake of compatibility, upgradability, and easy maintenance, do not modify the out of the box Magento themes. To customize the design of your Magento store, create a new custom theme.
1. 为了兼容性、升级能力和容易维护性，不要修改开箱即用的Magento主题。为了自定义网店主题，创建一个新的自定义主题。
2. [Set]({{page.baseurl}}config-guide/cli/config-cli-subcommands-mode.html) your Magento application to the developer [mode]({{page.baseurl}}config-guide/bootstrap/magento-modes.html). The application mode influences the way static files are cached by Magento. The recommendations about theme development we provide in this chapter are developer/default-mode specific.
2. 设置你的应用程序为开发者模式。应用程序的模式影响表态文件的缓存。推荐的我们在本章提供的关于主题开发特指开发者/默认模式

## Create a theme directory {#layout_theme_how-to_dirs} 创建一个主题目录

To create the directory for your theme: 为你的主题创建目录

1.	Go to `<your Magento install dir>/app/design/frontend`.

3.	Create a new directory named according to your vendor name: `/app/design/frontend/<Vendor>`. 
3. 基于你的包名创建一个目录叫： `/app/design/frontend/<Vendor>`. 
4.	Under the vendor directory, create a directory named according to your theme.
4. 在vendro目录创建你的主题目录

<pre>
app/design/frontend/
├──&nbsp;&lt;Vendor&gt;/
│&nbsp;&nbsp;&nbsp;│&nbsp;&nbsp;&nbsp;├──...&lt;theme&gt;/
│&nbsp;&nbsp;&nbsp;│&nbsp;&nbsp;&nbsp;│&nbsp;&nbsp;&nbsp;├──&nbsp;...
│&nbsp;&nbsp;&nbsp;│&nbsp;&nbsp;&nbsp;│&nbsp;&nbsp;&nbsp;├──&nbsp;...
</pre>

The folder name conventionally matches naming used in the theme's code: any alphanumeric set of characters, as the vendor sees fit, is acceptable. This convention is merely a recommendation, so nothing prevents naming this directory in another way.

目录名按惯例符合主题代码使用: vendor认为合适的任何字母数字的字符都可以接受，

## Declare your theme {#fedg_create_theme_how-to_declare} <br/>定义你的主题

After you create a directory for your theme, you must create `theme.xml` containing at least the theme name and the parent theme name (if the theme <a href="{{page.baseurl}}frontend-dev-guide/themes/theme-inherit.html" target="_blank">inherits</a> from one). Optionally you can specify where the theme preview image is stored.

在为主题创建一个目录后，必须添加theme.xml最少要包含主题名称和父主题名称（如果主题从一个继承的话）。额外地你可以指定主题预览图片的位置。

1. Add or copy from an existing `theme.xml` to your theme directory `app/design/frontend/<Vendor>/<theme>` <br/>添加或复制已有的theme.xml到你的主题目录

2. Configure it using the following example: <br/>使用如下示例设置：

{% highlight xml %}
<theme xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:Config/etc/theme.xsd">
     <title>New theme</title> <!-- your theme's name 主题名称-->
     <parent>Magento/blank</parent> <!-- the parent theme, in case your theme inherits from an existing theme 父主题，当你的主题继承自另一个 -->
     <media>
         <preview_image>media/preview.jpg</preview_image> <!-- the path to your theme's preview image 预览图片路径-->
     </media>
 </theme>
{% endhighlight %}

If you change the theme title or parent theme information in `theme.xml` after a theme was already [registered](#register_theme), you need to open or reload any Magento Admin page for your changes to be saved in the database.

如果在主题已经注释后你在theme.xml修改了主题标题或父主题信息，你需要打开或重载任何管理界面来让你的修改可以保存进数据库。

## Make your theme a Composer package (optional) {#fedg_create_theme_composer} <br/>使你的主题为composer包(可选)


Magento default themes are distributed as <a href="https://getcomposer.org/" target="_blank">Composer</a> packages.

Magento默认主题都发布为<a href="https://getcomposer.org/" target="_blank">Composer</a>包

To distribute your theme as a package, add a `composer.json` file to the theme directory and register the package on a packaging server. A default public packaging server is <a href="https://packagist.org/" target="_blank" >https://packagist.org/</a>.

为了发布你的主题为一个包，在主题目录添加composer.json文件并在包服务器注册这个包。默认公开包服务器是<a href="https://packagist.org/" target="_blank" >https://packagist.org/</a>

`composer.json` provides theme dependency information.
composer.json提供主题依赖信息

Example of a theme `composer.json`:主题composer.json示例：

{% highlight json %}
{
    "name": "magento/theme-frontend-luma",
    "description": "N/A",
    "require": {
        "php": "~5.5.0|~5.6.0|~7.0.0",
        "magento/theme-frontend-blank": "100.0.*",
        "magento/framework": "100.0.*"
    },
    "type": "magento2-theme",
    "version": "100.0.1",
    "license": [
        "OSL-3.0",
        "AFL-3.0"
    ],
    "autoload": {
        "files": [
            "registration.php"
        ]
    }
}
{% endhighlight %}

You can find details about the Composer integration in the Magento system in <a href="{{page.baseurl}}extension-dev-guide/build/composer-integration.html">Composer integration</a>.

你可以Magento系统的<a href="{{page.baseurl}}extension-dev-guide/build/composer-integration.html">Composer集成</a>找到关于Composer集成的详细信息

## Add registration.php {#fedg_create_theme_reg}

To register your theme in the system, in your theme directory add a `registration.php` file with the following content:

为了在系统注册你的主题，在主题目录添加registration.php文件含以下内容：

{% highlight php %}

<?php
/**
 * Copyright © 2015 Magento. All rights reserved.
 * See COPYING.txt for license details.
 */
\Magento\Framework\Component\ComponentRegistrar::register(
    \Magento\Framework\Component\ComponentRegistrar::THEME,
    'frontend/<Vendor>/<theme>',
    __DIR__
);

{% endhighlight %}

Where `<Vendor>` is your vendor name, `<theme>` is the theme code.

其中`<Vendor>`是你的vendor名称， `<theme>`是主题代码

For illustration, see the <a href="{{site.mage2000url}}app/design/frontend/Magento/luma/registration.php">registration.php</a> file of the Magento Luma theme.

示例查看Luma主题的 <a href="{{site.mage2000url}}app/design/frontend/Magento/luma/registration.php">registration.php</a>文件

## Configure images {#fedg_create_theme_how-to-images} 配置图片

Product image sizes and other properties used on the storefront are configured in a `view.xml` configuration file. It is required for a theme, but is optional if exists in the parent theme.

网店系统图片大小和其它使用到的属性都配置在view.xml配置文件。它是一个主题必需的，但如果在父主题已经存在就是可选的。

If the product image sizes of your theme differ from those of the parent theme, or if your theme does not inherit from any theme, add `view.xml` using the following steps:

如果你的主题系统图片大小和父主题不同，或如果你的主题不继承任何主题，如下添加view.xml：

1.	Log in to your Magento server as a user with permissions to create directories and files in the Magento installation directory. (Typically, this is the <a href="{{page.baseurl}}install-gde/prereq/apache-user.html">the Magento file system owner</a>.)<br/>
使用有权限在Magento目录创建目录和文件的账户登入Magento服务器。（一般地是Magento文件系统所有者）

2.	Create the `etc` directory in your theme folder<br/>在主题目录添加etc目录

3.	Copy `view.xml` from the `etc` directory of an existing theme (for example, from the Blank theme) to your theme's `etc` directory.<br/>从已有主题etc目录复制view.xml到你的主题etc目录（如从blank主题）

4.	Configure all storefront product image sizes in `view.xml`.<br/>在view.xml配置所有店面用到的图片<br/>
For example, you can make the category grid view product images square by specifying a size of 250 x 250 pixels, here is how the corresponding configuration would look like:<br/>
例如,你可以创建分类网格视图产品图片由指定的250 x 250像素尺寸摆方格，相应配置看起来像这样：

{% highlight XML%}
...
    <image id="category_page_grid" type="small_image">
        <width>250</width>
        <height>250</height>
    </image>
...
{% endhighlight XML%}

For details about images configuration in `view.xml`, see the <a href="{{page.baseurl}}frontend-dev-guide/themes/theme-images.html" target="_blank">Configure images properties for a theme</a> topic. 更多关于view.xml里图片配置查看为主题配置图片属性

## Create directories for static files {#fedg_theme_how-to_static} <br/>为静态文件创建目录

Your theme will likely contain several types of static files: styles, fonts, JavaScript and images.
Each type should be stored in a separate sub-directory of `web` in your theme folder:
<br/>
你的主题会包含多种类型的静态文件：样式、字体、JS和图片。每种类型必须保存在分开的主题目录中的web子目录下。

<pre>
app/design/&lt;area&gt;/&lt;Vendor&gt;/&lt;theme&gt;/
├──&nbsp;web/
│&nbsp;├──&nbsp;css/
│&nbsp;│&nbsp;├──&nbsp;source/&nbsp;
│&nbsp;├──&nbsp;fonts/
│&nbsp;├──&nbsp;images/
│&nbsp;├──&nbsp;js/
</pre>

In the <code>.../&lt;theme&gt;/web/images</code> you store the general theme related static files. For example, a theme logo is stored in <code>...&lt;theme&gt;/web/images</code>.
It is likely that your theme will also contain module-specific files, which are stored in the corresponding sub-directories, like <code>.../&lt;theme&gt;/&lt;Namespace_Module&gt;/web/css</code> and similar. Managing the module-specific theme files is discussed in the following sections of this Guide.

在<code>.../&lt;theme&gt;/web/images</code>你保存一般主题相关的静态文件。如<code>...&lt;theme&gt;/web/images</code>存放主题LOGO。很可能斧的主题会包含模块特定文件，都保存在相应子目录，像这样<code>.../&lt;theme&gt;/&lt;Namespace_Module&gt;/web/css</code>。管理特定模块主题文件在本指南随后部分讨论。


<div class="bs-callout bs-callout-info" id="info">
<span class="glyphicon-class">
<p>

During theme development, when you change any files stored here, you need to clear <code>pub/static</code> and <code>var/view_preprocessed</code> directories, and then reload the pages. Otherwise the old versions of files are displayed on the storefront. 
<br/>
在主题开发过程中，当你修改任何文件，需要清除<code>pub/static</code> and <code>var/view_preprocessed</code> 目录，然后重载页面。否则老版本文件被显示在网店。
</p></span>
</div>


## Your theme directory structure now {#fedg_theme_how-to_structure}<br/>现在你的主题目录结构 

At this point your theme file structure looks as follows: <br/>现在你的主题文件结构看起来像下面：

<pre>
app/design/frontend/&lt;Vendor&gt;/
├──&nbsp;&lt;theme&gt;/
│&nbsp;&nbsp;&nbsp;├──&nbsp;etc/
│&nbsp;&nbsp;&nbsp;│&nbsp;&nbsp;&nbsp;├──&nbsp;view.xml
│&nbsp;&nbsp;&nbsp;├──&nbsp;web/
│&nbsp;&nbsp;&nbsp;│&nbsp;&nbsp;&nbsp;├──&nbsp;images
│&nbsp;&nbsp;&nbsp;│&nbsp;&nbsp;&nbsp;│&nbsp;&nbsp;&nbsp;├──&nbsp;logo.svg
│&nbsp;&nbsp;&nbsp;├──&nbsp;registration.php
│&nbsp;&nbsp;&nbsp;├──&nbsp;theme.xml
│&nbsp;&nbsp;&nbsp;├──&nbsp;composer.json
</pre>



## Theme logo {#theme_logo} 主题LOGO

In the Magento application, the default format and name of a logo image is `logo.svg`. When you put a `logo.svg` image in the conventional location, which is `<theme_dir>/web/images` directory, it is automatically recognized as theme logo. It is displayed in your store page header once the theme is <a href="{{page.baseurl}}frontend-dev-guide/themes/theme-apply.html" target="_blank">applied</a>.

在Magento应用中，默认的LOGO图片格式和名称是logo.svg。当你在常规位置`<theme_dir>/web/images`目录放一个logo.svg图片，它为自动被识别为主题LOGO。一旦应用它被显示在网店页面标题

In your custom theme, you can use a logo file with a different name and format, but you might need to declare it. 

在你的自定义主题，你可以使用一个不同名称和格式的LOGO文件，但你需要声明它。

The necessity of declaration depends on whether your theme has a <a href="{{page.baseurl}}frontend-dev-guide/themes/theme-inherit.html" target="_blank">parent</a> theme and its logo image. The following cases are possible:<br/>
声明的必要性取决于你的主题是否有父主题和它的LOGO图片。可能有下面的情况：

<ul>
<li>
Your theme does not have a parent theme:你的主题没有父主题
<ul>
<li> if your logo image name and format is default, <code>logo.svg</code>, there is no need to declare it; 如果你的LOGO图片名称和格式是默认的<code>logo.svg</code>， 就不需要声明它</li>
<li>if your logo image name or format is not default, you need to <a href="#logo_declare">declare it in layout</a>.如果你的LOGO图片名称或格式不是默认的，需要在布局声明它。</li>
</ul>
</li>
<li>Your theme has a parent theme:你的主题有一个父主题：
<ul>
<li>if your theme logo image has the same name and format as the parent's theme logo, there is no need to declare it;如果你的主题LOGO图片有和父主题LOGO相同的名称和格式，就不需要声明它。</li>
<li>if your logo image has different name or format, declare it in layout.如果你的LOGO图片有不同的名称和格式，在布局声明它。</li>
</ul>
</li>
</ul>

## Declaring theme logo {#logo_declare} 声明主题LOGO

To declare a theme logo, add an <a href="{{page.baseurl}}frontend-dev-guide/layouts/layout-extend.html" target="_blank">extending</a> `<theme_dir>/Magento_Theme/layout/default.xml` layout. 

为了声明主题LOGO，添加一个扩展布局。

For example, if your logo file is `my_logo.png` sized 300x300px, you need to declare it as follows:  

比如：如果你的主题文件是my_logo.png大小是300x300px, 需要如下声明：

{% highlight xml %}
<page xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:View/Layout/etc/page_configuration.xsd">
    <body>
        <referenceBlock name="logo">
            <arguments>
                <argument name="logo_file" xsi:type="string">images/my_logo.png</argument>
                <argument name="logo_img_width" xsi:type="number">300</argument> 
                <argument name="logo_img_height" xsi:type="number">300</argument>
            </arguments>
        </referenceBlock>
    </body>
</page>		
{% endhighlight %}

Declaring the logo size is optional. 声明LOGO大小是可选的

To learn more about theme layouts, refer to the <a href="{{page.baseurl}}frontend-dev-guide/layouts/layout-overview.html" target="_blank">Layout section</a> of this guide.

本指南更多关于主题布局查看<a href="{{page.baseurl}}frontend-dev-guide/layouts/layout-overview.html" target="_blank">布局区</a>

## What's next {#next}下一步

### Theme registration {#register_theme} 主题注册
Once you open the Magento Admin (or reload any  Magento Admin page) having added the theme files to the files system, your theme gets registered and added to the database.

在文件系统添加完主题文件后一旦你打开后台（或重载任何后台页面），你的主题就被注册并添加到数据表。

### Applying a theme 应用一个主题
For information on how to apply the theme for the storefront, see the [Apply and configure a theme in Admin]({{page.baseurl}}frontend-dev-guide/themes/theme-apply.html) topic.

关于如何为店页应用主题信息查看[在后台应用和设置主题]({{page.baseurl}}frontend-dev-guide/themes/theme-apply.html) 专题

## See also

 * [Uninstall a theme]({{site.gdeurl}}install-gde/install/cli/install-cli-theme-uninstall.html)