---
layout: default
group: fedg
subgroup: A_Themes
title: Magento 主题结构 
menu_title: Magento 主题结构
menu_order: 3
version: 2.0
github_link: frontend-dev-guide/themes/theme-structure.md
redirect_from: /guides/v1.0/frontend-dev-guide/themes/theme-structure.html
---

<h2 id="theme-structure-intro">What's in this topic这个专题有什么</h2>
A <a href="{{page.baseurl}}frontend-dev-guide/themes/theme-general.html#theme-gen-overview" target="_blank">design theme</a> is an important part of the Magento application. This topic describes the file structure of a Magento theme.

<a href="{{page.baseurl}}frontend-dev-guide/themes/theme-general.html#theme-gen-overview" target="_blank">设计主题</a> 是程序重要的一部分。本专题描述主题文件结构。

<h2 id="theme-structure-loc">Magento theme location 主题位置</h2>
Storefront themes are conventionally located under `app/design/frontend/<Vendor>/`. Though technically they can reside in other directories. For example Magento built-in themes can be located under `vendor/magento/theme-frontend-<theme_code>` when a Magento instance is deployed from the Composer repository.

店面主题按惯例放在 `app/design/frontend/<Vendor>/`下面。虽然它们可以存在任何目录下。如当Magento实例是通过Composer库部署Magento内建主题放在`vendor/magento/theme-frontend-<theme_code>`

Each theme must be stored in a separate directory:每个主题必须在分开的目录里：
<pre>
app/design/frontend/&lt;Vendor&gt;/
├──&nbsp;&lt;theme1&gt;
├──&nbsp;&lt;theme2&gt;/
├──&nbsp;&lt;theme3&gt;
├--...
</pre>

<h2 id="theme-structure-comp">Theme components主题组件</h2>
The structure of a Magento theme directory typically would be like following:

一般Magento主题结构如下：

<pre>
&lt;theme_dir&gt;/
├──&nbsp;&lt;Vendor&gt;_&lt;Module&gt;/&nbsp;
│	├──&nbsp;web/
│	│	├──&nbsp;css/
│	│	│	├──&nbsp;source/
│	├──&nbsp;layout/
│	│	├──&nbsp;override/
│	├──&nbsp;templates/
├──&nbsp;etc/
├──&nbsp;i18n/&nbsp;
├──&nbsp;media/
├──&nbsp;web/
│	├──&nbsp;css/
│	│	├──&nbsp;source/&nbsp;
│	├──&nbsp;fonts/
│	├──&nbsp;images/
│	├──&nbsp;js/
├──&nbsp;composer.json&nbsp;
├──&nbsp;registration.php&nbsp;
├──&nbsp;theme.xml&nbsp;
</pre>
Let's have a closer look at each particular sub-directory.

让我们详细查看每个子目录

<div class="bs-callout bs-callout-info" id="info">
  <p>The directories and files structure described below is the most extended one. It may not coincide with the structure of your store. 如下描述的目录和文件结构是大多数情况。可能与你的网店结构不一致</p>
</div>
<table>
  <tbody>
    <tr>
      <th>Directory</th>
      <th colspan="1">Required</th>
      <th>Description</th>
    </tr>
    <tr>
      <td colspan="1">
        <code>
          /&lt;Vendor&gt;_&lt;Module&gt;
        </code>
      </td>
      <td colspan="1">
        optional
      </td>
      <td colspan="1">
          Module-specific styles, layouts, and templates.特定模块样式、布局、模板
      </td>
    </tr>
    <tr>
      <td colspan="1">
        <code>/&lt;Vendor&gt;_&lt;Module&gt;/web/css/source</code>
      </td>
      <td colspan="1">
        optional
      </td>
      <td colspan="1">
          Module-specific styles (<code>.css</code> and/or <code>.less</code> files). General styles for the module are in the <code>_module.less</code> file, and styles for widgets are in <code>_widgets.less</code>.<br/>
          特定模块样式。一般模块样式在<code>_module.less文件，部分样式在 <code>_widgets.less</code>里面
      </td>
    </tr>
    <tr>
      <td colspan="1">
        <code>/&lt;Vendor&gt;_&lt;Module&gt;/layout</code>
      </td>
      <td colspan="1">
        optional
      </td>
      <td colspan="1">
        Layout files which extend the default module or parent theme layouts. <!--ADDLINK-->
        <br/>布局文件扩展默认的模块父主题布局
      </td>
    </tr>
    <tr>
      <td colspan="1">
        <code>/&lt;Vendor&gt;_&lt;Module&gt;/layout/override/base</code>
      </td>
      <td colspan="1">
        optional
      </td>
      <td colspan="1">
        Layouts that override the default module layouts.覆写默认模块布局
      </td>
    </tr>
    <tr>
      <td colspan="1">
        <code>/&lt;Vendor&gt;_&lt;Module&gt;/layout/override/&lt;parent_theme&gt;</code>
      </td>
      <td colspan="1">optional</td>
      <td colspan="1">
        Layouts that override the parent theme layouts for the module.覆写父主题布局的布局
      </td>
    </tr>
    <tr>
      <td colspan="1">
        <code>/&lt;Vendor&gt;_&lt;Module&gt;/templates</code>
      </td>
      <td colspan="1">
        optional
      </td>
      <td colspan="1">
        This directory contains theme templates which override the default module templates or parent theme templates for this module. Custom templates are also stored in this directory.这个目录包含主题模板，覆写默认模块模板或父主题这个模块的模块。自定义模板也保存在这个目录
      </td>
    </tr>
    <tr>
      <td colspan="1">
        <code>
          /etc/view.xml
        </code>
      </td>
      <td colspan="1">required for a theme, but optional if exists in the parent theme</td>
      <td colspan="1">
        This file contains images configuration for all storefront product images and thumbnails.
        这个文件包含所有店面产品图片和缩略图图片配置
      </td>
    </tr>
    <tr>
      <td colspan="1">
        <code>/i18n</code>
      </td>
      <td colspan="1">optional</td>
      <td colspan="1">.csv files with translations. 翻译用.csv文件</td>
    </tr>
    <tr>
      <td colspan="1">
        <code>/media</code>
      </td>
      <td colspan="1">required</td>
      <td colspan="1">
        This directory contains a theme preview (a screenshot of your theme).
        这个目录包含主题预览（主题的截图）
      </td>
    </tr>
    <tr>
      <td colspan="1">
        <code>/web</code>
      </td>
      <td colspan="1">
        optional
      </td>
      <td colspan="1">Static files that can be loaded directly from the frontend.可以从前端直接加载的静态文件</td>
    </tr>
    <tr>
      <td colspan="1">
        <code>/web/css/source</code>
      </td>
      <td colspan="1">
        optional
      </td>
      <td colspan="1">This directory contains theme
        <code>less</code>
         configuration files that invoke mixins for global elements from the Magento UI library, and
        <code>theme.less</code>
         file which overrides the default variables values. <!--ADDLINK-->
         这个目录包含主题LESS配置文件，从覆写默认变量值的UI库和theme.less文件调用混合全局元素
      </td>
    </tr>
    <tr>
      <td colspan="1">
        <code>/web/css/source/lib</code>
      </td>
      <td colspan="1">
        optional
      </td>
      <td colspan="1">
        View files that override the UI library files stored in <code>lib/web/css/source/lib</code>
        覆写存储在<code>lib/web/css/source/lib</code>的UI库文件的视图文件
      </td>
    </tr>
    <tr>
      <td colspan="1">
        <code>/web/fonts</code>
      </td>
      <td colspan="1">
        optional
      </td>
      <td colspan="1">
        Theme fonts.
      </td>
    </tr>
    <tr>
      <td colspan="1">
        <code>/web/images</code>
      </td>
      <td colspan="1">
        optional
      </td>
      <td colspan="1">
        Images that are used in this theme.此主题用到的图片
      </td>
    </tr>
    <tr>
      <td colspan="1">
        <code>/web/js</code>
      </td>
      <td colspan="1">
        optional
      </td>
      <td colspan="1">
        Theme JavaScript files.
      </td>
    </tr>
    <tr>
      <td colspan="1">
        <code>
          /composer.json
        </code>
      </td>
      <td colspan="1">optional</td>
      <td colspan="1">
        Describes the theme dependencies and some meta-information. Will be here if your theme is a Composer package.
        描述主题依赖和一些元信息。如果你的主题是composer包会存在
      </td>
    </tr>
    <tr>
      <td colspan="1">
        <code>/registration.php</code>
      </td>
      <td colspan="1">required</td>
      <td colspan="1">
        Required to register your theme in the system. 需要注册你的主题到系统
      </td>
    </tr>
    <tr>
      <td colspan="1">
        <code>/theme.xml</code>
      </td>
      <td colspan="1">required</td>
      <td colspan="1">
        The file is mandatory as it declares a theme as a system component. It contains the basic meta-information, like the theme name and the parent theme name, is the theme is inherited from an existing theme. The file is used by the Magento system to recognize the theme.
        这个文件是强制的作为声明一个主题为系统组件。它包含基本的元信息如主题名称和父主题名称，主题是否继承自已存在主题。这个文件被系统使用来识别主题。
      </td>
    </tr>
  </tbody>
</table>

<h2 id="theme-structure-files">Theme files主题文件</h2>

Apart from the configuration file and theme metadata file, all theme files fall into the following two categories:

* Static view files
* Dynamic view files

<h3 id="theme-structure-pub">Static view files</h3>
A set of theme files that are returned by the server to a browser as is, without any processing, are called the *static files* of a theme.

Static files can be located in a theme directory as follows:
<pre>
&lt;theme_dir&gt;/
├──&nbsp;media/
├──&nbsp;web
│	├──&nbsp;css/&nbsp;(except&nbsp;the&nbsp;&quot;source&quot;&nbsp;sub-directory)
│	├──&nbsp;fonts/
│	├──&nbsp;images/
│	├──&nbsp;js/
</pre>
The key difference between static files and other theme files is that static files appear on a web page as references to the files, while other theme files take part in the page generation, but are not explicitly referenced on a web page as files.

Static view files that can be accessed by a direct link from the store front, are distinguished as public theme files.

<div class="bs-callout bs-callout-info" id="info">
  <p>To be actually accessible for browsers public static files are <a href="{{page.baseurl}}architecture/view/static-process.html#publish-static-view-files" target="_blank">published</a> to the <code>/pub/static/frontend/&lt;Vendor&gt;/&lt;theme&gt;/&lt;language&gt;/css/</code> directory.</p>
</div>

<h3>Dynamic view files</h3>
View files that are processed or executed by the server in order to provide result to the client. These are: `.less` files, templates, and layouts.

Dynamic view files are located in a theme directory as follows:
<pre>
&lt;theme_dir&gt;/
├──&nbsp;Magento_&lt;module&gt;/&nbsp;
│	├──&nbsp;web/
│	│	├──&nbsp;css/
│	│	│	├──&nbsp;source/
│	├──&nbsp;layout/
│	│	├──&nbsp;override/
│	├──&nbsp;templates/
├──&nbsp;web/
│	├──&nbsp;css/
│	│	├──&nbsp;source/

</pre>
