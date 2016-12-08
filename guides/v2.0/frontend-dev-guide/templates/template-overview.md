---
layout: default  
group: fedg
subgroup: C_Templates
title: 模板概览
menu_title: 模板
menu_order: 1
menu_node: parent
version: 2.0
github_link: frontend-dev-guide/templates/template-overview.md
redirect_from: /guides/v1.0/frontend-dev-guide/templates/template-overview.html
---

<h2>Introduction to customizing a theme using templates 使用模板定制主题的介绍</h2>


In Magento application templates are the part of the view layer. Templates define exactly how the content of <a href="{{page.baseurl}}frontend-dev-guide/layouts/layout-overview.html" target="_blank">layout blocks</a> is presented on a page: order, CSS classes, elements grouping, and so on. 
In most cases, templates do not contain any logic about whether they will or will not be rendered, this is typically handled by the layout files. Once a template is called in a layout, it will be displayed.

在Magento应用模板是视图层的一部分。模块具体定义布局块的内容如何显示到一个页面：顺序、CSS类、元素组等。大多数情况下，模板不包含任何关于它们是否渲染的逻辑，这个主要由布局文件处理。一量布局调用了模板，它就会显示出来。

Default Magento templates are PHTML files. Also HTML templates are used for [Knockout JS](http://knockoutjs.com/index.html) scripts. 

默认的Magento模块是PHTML文件。此外HTML模板用Knockout JS脚本

<div class="bs-callout bs-callout-info" id="info">
<span class="glyphicon-class">
 <p><a href="{{page.baseurl}}architecture/view/template-engine.html" target="_blank">The Magento template rendering subsystem</a> supports multiple template engines, including the default PHP-based engine for processing PHTML templates.
 <br/>
 Magento模块渲染子系统支持多种模板引擎，包括默认处理PHTML模板的基于PHP的引擎
 </p></span>
</div>

This chapter describes how to customize templates in your design theme, and provides both the practice reference and the theoretical background of how templates are applied in a Magento store. 

本章节描述如何在你的设计主题自定义模板，并提供关于模板在网店如何应用的实践手册和理论背景


We strongly recommend that you do not change the default templates, because if you do edit them, your changes can be overwritten by the new version of the default files during upgrades.
The best practice is <a href="{{page.baseurl}}frontend-dev-guide/themes/theme-create.html" target="_blank">creating a new design theme</a> and adding your modified templates there.

我们强列建议不要修改默认的模板，因为如果你修改的他们，在升级时你的修改会被新版本覆写。

This chapter contains the following topics: 本章节包括如下专题：

* <a href="{{page.baseurl}}frontend-dev-guide/templates/template-walkthrough.html" target="_blank">Template customization walkthrough模板定制演练</a>
* <a href="{{page.baseurl}}frontend-dev-guide/templates/template-override.html" target="_blank">Templates basic concepts模板基本概念</a>
* <a href="{{page.baseurl}}frontend-dev-guide/templates/template-sample.html" target="_blank">Illustration of customizing templates 自定义模板例证</a>
* <a href="{{page.baseurl}}frontend-dev-guide/templates/template-email.html" target="_blank">Customizing email templates 自定义邮件模板</a>










