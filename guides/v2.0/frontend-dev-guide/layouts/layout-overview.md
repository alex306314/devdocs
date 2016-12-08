---
layout: default
group: fedg
subgroup: B_Layouts
title: 布局概览
menu_title: 布局
menu_order: 1
menu_node: parent
version: 2.0
github_link: frontend-dev-guide/layouts/layout-overview.md
redirect_from: /guides/v1.0/frontend-dev-guide/layouts/layout-overview.html
---

<h2>Introduction 介绍</h2>

Magento application implements the <a href="http://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller" target="_blank">Model-view-controller</a> architecture pattern; meaning, the Magento software is architected into *layers*, including the *view layer*.

Magento应用实现了MVC架构模型，意味着Magento软件是层装架构，包括视图层。

The major part of the view layer of Magento application is layout. Functionally, layout is a page structure, represented by hierarchy of elements (element tree), which can be of two types: blocks and containers. Technically, layout is defined in the .xml files, which contain element declarations and element manipulation instructions.

视图层主要部分是布局。功能上布局是一个页面结构，由层级元素代表，可以有两种类型：区块和容器。技术上讲，布局是定义在.xml文件中，包含元素定义和元素操作指令。

This article describes the basic concepts you need to know to create layouts for your custom theme.

此文描述为你的自定义主题创建布局你需要知道的基本概念

**Contents**

 * TOC
 {:toc}

## Terms used {#layout-over-terms} 用到的术语

<span id="handle">*Layout handle布局句柄*</span>

A *layout handle* is a uniquely identified set of layout instructions that serves as a name of a layout file.

一个布局句柄是一个唯一标识符作为一个布局文件的名字。

There are three kinds of layout handles:这有三种布局句柄类型：

- **page type layout handles** – Synonyms of the page type identifiers. Correspond to "full action names" of controller actions, for example, catalog_product_view.<br/>
**页面类型布局句柄** - 页面类型标识符的同义词。符合控制器动作的全动作名称，如catalog_product_view
- **page layout handles** – Identifiers of specific pages. Correspond to controller actions with parameters that identify specific pages, for example, catalog_product_view_type_simple_id_128.<br/>
**页面布局句柄** 指定页面的标识符。相当于有参数的控制器动作标识指定页面，如catalog_product_view_type_simple_id_128
- **arbitrary handles** - Do not correspond to any page type, but other handles use them by including.<br/>
**任意的句柄** 不符合任何页面类型，但其它句柄通过包含使用它们。

## Basic layout elements {#layout_overview_blocks} 基本布局元素

The basic components of Magento page design are blocks and containers. 

页面设计的基本组件是区块和容器

A *container* exists for the sole purpose of assigning content structure to a page. A container has no additional content except the content of included elements. Examples of containers include the header, left column, main column, and footer.

容器的存在只为一个目的就是分派内容结构到一个页面。一个容器除了内容包含的元素没有其它内容。窗帘的示例包括：header,left column, main column, and footer.

The following figure shows an example:

<img src="{{ site.baseurl }}common/images/layouts_containers_defn.jpg" />

 A *block* represents each feature on a page and employs templates to generate the HTML to insert into its parent structural block. Examples of blocks include a category list, a mini cart, product tags, and product listing.
 <br/>
 一个区块代表页面每个功能并使用模板来生成HTML插入到父结构区块。区块示例有分类列表、购物车、产品标签和产品列表。

The following figure shows an example:

<img src="{{ site.baseurl }}common/images/layouts_block_defn.jpg"/>.

## Basic layouts 基本布局

The basic view of all Magento storefront pages in defined in two page configuration layout files located in the Magento_Theme module: 

所有前端页面基本视图被定义为两种页面配置布局文件，在Magento_Theme模块：

* `<Magento_Theme_module_dir>/view/frontend/layout/default.xml`: defines the page layout. 
* `<Magento_Theme_module_dir>/view/frontend/layout/default_head_blocks.xml`: defines the scripts, images, and meta data included in pages' `<head>` section. 

These basic page configuration layouts are extended in other Magento modules and in Magento themes.

这些基础页面配置布局在其它模块和主题被扩展

You can also [extend]({{page.baseurl}}frontend-dev-guide/layouts/layout-extend.html) or [override]({{page.baseurl}}frontend-dev-guide/layouts/layout-override.html) these files in your custom theme. 

你也可以在你的自定义主题扩展或覆写这些文件

## Layout files types and conventions 布局文件类型的约定

### Layout file types: by role 布局文件类型： 由角色

For a particular page, its layout is defined by two major layout components: *page layout* file and *page configuration* file (or *generic layout* for pages returned in AJAX requests, emails, and so on).

在特定的页面，它的布局由两个主要布局组件定义：页面布局文件和页面配置文件（或AJAX请求、email等一般布局）

Following are the definitions of each layout file type:下面是每种布局文件类型定义

* *Page layout*: an XML file declaring a page wireframe inside the `<body>` section of the HTML page markup, for example, two-column page layout. <br/>一种xml文件声明HTML页面标记的body区域页面线框。如两列页面布局
* *Page configuration*: an XML file declaring detailed structure, contents and meta-information of a page (includes the `<html>`, `<head>`, and `<body>` sections of the HTML page markup).
<br/>
*页面配置*： 一种xml文件声明页面（包括html, head, bdoy ）详细结构、内容和元信息
* *Generic layout*: an XML file declaring page detailed structure and contents inside the `body` section of the HTML page markup. Used for pages returned by AJAX requests, emails, HTML snippets, and so on.
*一般布局*： 一种xml文件声明页面详细结构和body区域内容，用于返回AJAX请求emailHTML片断等。

For details, refer to <a href="{{page.baseurl}}frontend-dev-guide/layouts/layout-types.html" target="_blank">Layout file types</a>.

In this guide we use *layout files* when talking about concepts which are similarly applied to all of these types of layout files.

在本指定我们使用*布局文件*当谈到应该到所有类型布局文件的概念

<h3 id="layout-loc">Module and theme layout files 模块和主题布局文件</h3>

The following terms are used to distinguish layouts provided by different application components:
下面的条件用来区别不用应用组件提供的布局

* *Base layouts*: Layout files provided by modules. Conventional location: 
	* Page configuration and generic layout files: `<module_dir>/view/frontend/layout`
	* Page layout files: `<module_dir>/view/frontend/page_layout`
* *Theme layouts*: Layout files provided by themes. Conventional location:
	* Page configuration and generic layout files: `<theme_dir>/<Namespace>_<Module>/layout`
	* Page layout files: `<theme_dir>/<Namespace>_<Module>/page_layout`


## Customize layout {#layout-custom} 定制布局

To ensure stability and secure your customizations from being deleted during upgrade, do not change out-of-the-box Magento module and theme layouts.

在升级时为确保稳定性和保护你的修改被删除，不要修改默认模块和主题布局

To make the necessary changes, create <a href="{{page.baseurl}}frontend-dev-guide/layouts/layout-extend.html" target="_blank">extending</a> and <a href="{{page.baseurl}}frontend-dev-guide/layouts/layout-override.html" target="_blank">overriding</a> layout files in your custom theme. 

做必要的修改， 在你的自定义主题创建扩展和覆写布局文件

## Layout files processing {#layout_processing} 布局文件处理


The Magento application processes layout files in the following order:

Magento应用处理布局文件按如下顺序：

1.	Collects all layout files from modules. The order is determined by the modules order in the module list from `app/etc/config.php`.<br/>从所有模块收集布局文件。顺序取决于app/etc/config.php列出的模块顺序。
2.	Determines the sequence of <a href="{{page.baseurl}}frontend-dev-guide/themes/theme-inherit.html" target="_blank">inherited</a> themes `[<parent_theme>, ..., <parent1_theme>] <current_theme>`确定继承的主题顺序
3.	Iterates the sequence of themes from last ancestor to current:遍历主题序列从最后祖先到当前。

	a.	Adds all extending theme layout files to the list.添加所有扩展主题布局文件到列表

	b.	Replaces overridden layout files in the list.替换列表中覆写的布局文件


1.	Merges all layout files from the list. 从列表融合所有布局文件

<div class="bs-callout bs-callout-info" id="info">
  <p>Layout files that belong to inactive modules or modules with disabled output are ignored.未激活模块或未启用模块的布局文件输出被忽略</p>
</div>



## Related topics

*	<a href="{{page.baseurl}}frontend-dev-guide/layouts/xml-instructions.html" target="_blank">Layout instructions</a>
*	<a href="{{page.baseurl}}frontend-dev-guide/layouts/xml-manage.html" target="_blank">Common layout customization tasks</a>
*	<a href="{{page.baseurl}}frontend-dev-guide/layouts/layout-extend.html" target="_blank">Extend a layout</a>
*	<a href="{{page.baseurl}}frontend-dev-guide/layouts/layout-override.html" target="_blank">Override a layout</a>
*	<a href="{{page.baseurl}}frontend-dev-guide/layouts/layout-practice.html" target="_blank">Customizing layout - step-by-step illustration</a>



