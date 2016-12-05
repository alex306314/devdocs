---
layout: default
group: fedg
subgroup: A_Themes
title: 主题
menu_title: 主题
menu_order: 1
menu_node: parent
version: 2.0
github_link: frontend-dev-guide/themes/theme-general.md
redirect_from: /guides/v1.0/frontend-dev-guide/themes/theme-general.html
---

<h2 id="theme-gen-overview">Overview 概览</h2>
A *theme* is a component of Magento application which provides a consistent look and feel (visual design) for entire application area (for example, storefront or Magento admin) using a combination of custom templates, layouts, styles or images.

主题是Magento应用程序的一种组件，它使用自定义模板、布局、样式或图片为整个应用程序区域（如前端或后台）提供一致的外观（视觉设计）

Themes are designed to override or customize view layer resources, provided initially by modules or libraries.<!--ADDLINK to Fallback--> Themes are implemented by different vendors (frontend developers) and intended to be distributed as additional packages for Magento system similar to other components.

主题被设计成覆写或自定义视图层资源，由模块或库最初提供。主题由不同的供应商（前端开发者）实现，并打算像其它组件一样做为Magento系统附加包发布

Out-of-the-box Magento application provides two design themes: Luma, as a demonstration theme, and Blank as a basis for custom theme creation.

开箱即用的Magento应用程序提供两个主题设计： Luma，作为演示主题， 和Blank作为自定义主题创建的基础。

There are no restrictions on using the demonstration Luma theme for a live store, but if you want to customize the default design, you need to create a new theme. We strongly recommend not to change the default Luma and Blank theme files, because if you do edit the default files, your changes can be overwritten by the new version of the default files during upgrades.

没有限制将演示用的Luma主题用于线上网店，但如果你想自定义默认设计，你需要创建一个新主题。我们强烈建议不修改默认的Luma和Blannk主题文件， 因为如果你编辑了默认文件，在升级时你的修改会被新版本的默认文件覆盖

Your new theme can be a standalone new theme, or can inherit from the default or any other existing one. The theme inheritance concept implemented in the Magento system allows you changing only certain theme files, and <a href="{{page.baseurl}}frontend-dev-guide/themes/theme-inherit.html">inheriting the rest necessary files from a parent theme</a>. 

你的新主题可以是完全独立的新主题，也可以继承自默认或任何其它已经存在的一个。Magento系统实现了主题继承概念允许你只修改指定的主题文件，然后从父主题继承其它需要的文件。

The Create a new theme chapter provides all information, including theoretical concepts and practical references, a frontend developer might need to efficiently create a new theme in Magento application.

创建一个新主题章节提供所有信息，包括理论概念和实际操作，一个前端开发者或许需要在Magento系统高效的创建一个新主题。

<h2 id="theme-gen-walkthrough">Add a theme: walkthrough 添加一个主题</h2>
The high-level steps required to add a new theme in the Magento system are the following:

在Magento系统添加新主题需要如下步骤：

1. Create a directory for the theme under `app/design/frontend/<your_vendor_name>/<your_theme_name>`.创建目录
2. Add a declaration file `theme.xml` and optionally create `etc` directory and create a file named `view.xml` to the theme directory.
2. 在主题目录添加定义文件theme.xml及可选的添加etc目录及创建名为view.xml的文件
3. Add a `composer.json` file.
4. Add `registration.php`.
3. Create directories for CSS, JavaScript, images, and fonts.
3. 创建css、js、image和font目录
4. Configure your theme in the Admin panel.
4. 在管理界面配置你的主题

<h2 id="theme-gen-read">Recommended reading推荐阅读</h2>

* <a href="{{ site.mage2000url }}app/code/Magento" target="_blank">Checklist of modules</a>
* <a href="{{page.baseurl}}architecture/view/static-process.html" target="_blank">Static view files processing</a>
