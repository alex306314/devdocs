---
layout: default  
group: fedg 
subgroup: A_Themes
title: 添加自定义 favicons
menu_title:  添加自定义 favicons
menu_order: 7
version: 2.1
github_link: frontend-dev-guide/themes/favicon.md
---
<h2 id="favicon-intro">What's in this topic 此专题讲什么</h2>

This topic describes how to add custom favicons.
如何添加自定义图标

**Contents**

* TOC
{:toc}

## General overview 

Magento provides a default 16px x 16px favicon that you can override by uploading a custom icon in the Magento Admin, or by adding it manually in a specific location in a theme directory.
If both favicons exist, the one you uploaded in the Admin takes precedence.

Magento提供默认的16x16px图片你可以在后台界面通过上传自定义图标覆盖， 或通过手动添加一个主题目录的特定位置。如果两种图标都存在，在后台上传的具有优先权。

If you want to have favicons of different sizes, you need to add them manually in the file system and define in layout. 

如果你想有不同尺寸的图标，你需要手动添加他们到文件系统再到布局定义。

Magento supports the following file types for favicon: `.ico`, `.png`, `.gif`, `.jpg`, `.jpeg`, `.apng`, `.svg`. Not all browsers support all these formats. The most widely supported file format to use for a favicon is `.ico`. 

支持如下文件类型的图标：`.ico`, `.png`, `.gif`, `.jpg`, `.jpeg`, `.apng`, `.svg`.不是所有浏览器都支持这些格式。理广泛的支持的文件格式是使用.icon图标。

See the following sections for details about adding favicons.
查看下面关于添加图标的详情

## Adding a custom favicon in Admin 在后台添加自定义图标

To add a custom favicon in the Magento Admin, do the following:

1. Navigate to **CONTENT** > (**Design**) **Configuration**. 
2. In the scope grid, decide on which level you will configure the favicon and click **Edit**     in the corresponding row.
   
   <img style="border: 1px solid #ABABAB" src="{{site.baseurl}}common/images/favicon_2_21.png">
   
3. Under the **Other Settings** title, expand the **HTML Head** options.
4. Next to **Favicon Icon**, click **Upload**, and select the file.
   
   <img style="border: 1px solid #ABABAB" src="{{site.baseurl}}common/images/favicon_1_21.png">
   
5. Click **Save Configuration** in the upper right corner to save the changes.

If caching is enabled in your Admin, you get a notification that refreshing certain cache types is required. Click the link provided in the notification, and then click **Flush Magento Cache**.


## Add custom favicons manually 手动添加自定义图标

To override the default 16px x 16px favicon manually, add your custom `favicon.ico` in the `<your_theme_dir>/Magento_Theme/web/`directory. 

要手动覆写默认的图标，在这个目录添加自定义`favicon.ico`

To add favicon icons of other sizes, take the following steps:
要添加其它尺寸图标如下步骤：

1. Add your icons in the `<your_theme_dir>/Magento_Theme/web/` directory.
2. In the `<your_theme_dir>/Magento_Theme/layout/default_head_blocks.xml` layout file specify the paths to the icons and their sizes. 

For example, if you added a `favicon-32x32.png` icon and want it to be used as a 32px x 32px favicon, your `default_head_blocks.xml` would be like following:

例如：如果你添加了`favicon-32x32.png`图标然后想使用为32px x 32px的图标，你的xml会如下：

{%highlight xml%}
<page xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:View/Layout/etc/page_configuration.xsd">
    <head>
        <link src="Magento_Theme::favicon-32x32.png" rel="icon" sizes="32x32" />
    </head>
</page>

{%endhighlight%}

For your changes to be applied, clear the browser cache, and the following directories on the server (do not delete the `.htaccess` file!): 

让你的修改生效，清除缓存，然后删除服务器下面的目录（不要删除.htaccess文件！）

- `pub/static`
- all directories under `var`

