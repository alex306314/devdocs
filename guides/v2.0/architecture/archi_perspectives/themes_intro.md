---
layout: default
group: arch-guide
subgroup: Architectural Layers
title: Magento主题
menu_title: Magento主题
menu_order: 1
version: 2.0
github_link: architecture/archi_perspectives/themes_intro.md
redirect_from: /guides/v1.0/architecture/archi_perspectives/themes_intro.html
---



<h2>Magento themes 主题</h2>

A theme is a component of Magento application that provides a consistent look and feel (visual design) for entire application area (for example, storefront or Magento admin) using a combination of custom templates, layouts, styles or images.

主题是Magento应用程序的一个组件使用组合自定义模板、布局、样式或图片为整个应用程序区域（如前台或后台）提供一致的外观（视觉设计）

 Out-of-the-box Magento application provides two design themes: Luma, as a demonstration theme, and Blank as a basis for custom theme creation.

 开始即用的Magneto应用程序提供两个主题设计：作为示范主题Luma和作为用户自定义主题基础的Blank

All theme files are stored under app/design/<area>/<Vendor>/<theme>/.

所有主题文件都保存在 app/design/<area>/<Vendor>/<theme>/ 目录下面

Apart from the configuration file and theme metadata file, all theme files fall into the following two categories:

除了配置文件和主题元数据文件，所有主题文件分为以上两类：

* Static view files are a set of theme files that are returned by the server to a browser as is, without any processing, are called the static files of a theme.

* 静态视图文件是由服务器原样发送到浏览器一组视图文件，没有经过任何处理，被叫做主题静态文件。

* Dynamic view files are view files that are processed or executed by the server in order to provide result to the client. These are: .less files, templates, layouts .

* 动态视图文件是由服务器为了向客户端提供内容处理或执行过的视图文件。包括：.less文件、模板、布局。

 design packets are collections of related themes plus nondefault variants.

 设计包是相关主题加个非默认变体的集合

 Magento supports multi theme model. Themes are highly extensible. control 1) the visual aspect of site design (skinning). Includes CSS, images, design/UI- specific Javascript. Templates control which data is shown and how. No business logic included in themes.

 Magento支持多种主题模型。主题具有高可扩展性。控制网站视觉方面设计，包括CSS、图片、UI设计-特别是JS。模板控制哪些及如何显示数据主题没有业务逻辑。

<h3>Theme components主题组件</h3>


Magento theme components include: 主题组件包括：

* Layout:  This includes all your layout XML files. This defines which template file to load.
* 布局： 包括你所有XML布局文件，这个定义加载哪个模板文件
* Template:  This includes all your template files which are generally .phtml files. 
* 模板： 包括所有.phtml的模板文件
* Skin:  This includes all your static files like images, css and js.
* 皮肤： 包括所有静态文件如图片、CSS和JS
* Local:  This includes all your language related file. This will be used when you want to make your theme compatible with different languages.
* 本地： 包括所有语言相关的文件。当你想让你的主题兼容不同的语言就要用到这个

<h3>Theme process flow主题处理流程</h3>

Process flow:

处理流程：

 In general Magento’s fallback technique for theme is as below:
Your Custom Package >> Default Package >> Base Package >> Error Message
From above hierarchy you can imagine that if any of the requested file is not available in your theme then it will look for default package first and after that look into Base package and at last it will show error message if requested file is not available in any of the package.

一般来讲Magento主题的回退机制如下：

你的自定义包 >> 默认包 >> 基础包 >> 错误信息

从上面的层次关系你可想象到如果任何被请求文件不在你的主题里然后它会先查找默认包再查找基础包最后如果请求文件所有包都没找到会显示错误信息。

Theme inheritance  based on the fallback mechanism, which guarantees that if a view file is not found in the current theme, the system searches in the ancestor themes, module view files or library

主题机制继承了回退机制，这种机制保证了如果视图文件在当前主题没有找到，系统会查找父级主题、模块视图文件或库

— page templates 页面模板<br/>
— block templates 区块模板<br/>
— layouts 布局


Apart from the configuration file and theme metadata file, all theme files fall into the following two categories:

除了配置文件和主题元数据文件，所有主题分为如下两类：

	*	Static view files. These theme files are returned by the server to a browser as is, without any processing, and are called the static files of a theme.
	* 静态视图文件。这些主题文件是被服务器原样发送到浏览器，不做任何处理，也叫做主题静态文件

	*	Dynamic view files. View files that are processed or executed by the server in order to provide result to the client. These are: .less files, templates, layouts
	* 动态视图文件。 服务器为了向客户端发送结果处理或运行的视图文件。它们是：.less文件、模板、布局

Where do themes live?

主题在哪些地方？

Each theme resides in a unique directory
每个主题存在于唯一的目录
 Themes live in two different directories:
 主题有两种不同的目录：

/skin/frontend: contains images and CSS for a theme. 包含主题的图片和CSS

/app/design/frontend: contains page templates and layouts。 包含页面模板和布局

Base package provides hooks to all of Magento’s core features.

基础包为所有Magneto的核心功能提供钩子

Add override features rather than edit default theme files.

添加覆写功能而不是编辑默认的主题文件





主题和布局进一步讨论在
<h2 id="related">相关讨论主题</h2>
<a href="{{page.baseurl}}architecture/archi_perspectives/arch_diagrams.html">框架图</a>

视图层
