---
layout: default
group: arch-guide
subgroup: Components
title: 模块概览
menu_title: 模块概览
menu_order: 3
level3_menu_node: level3child
level3_subgroup: modules
version: 2.0
github_link: architecture/archi_perspectives/components/modules/mod_intro.md
redirect_from: 
  - /guides/v1.0/architecture/modules/mod_intro.html
  - /guides/v2.0/architecture/modules/mod_intro.html
---

<h2 id="arch-modules-overview">Module overview 模块概览</h2>
A <i>module</i> is a logical group -- that is, a directory containing blocks, controllers, helpers, models -- that are related to a specific business feature. In keeping with Magento's commitment to optimal modularity, a module encapsulates one feature and has minimal dependencies on other modules.

一个 <i>模块</i>是一个逻辑组——也就是一个目录包含了针对特定业务逻辑相关的区块、控制器、助手、模型。与Magneto的最佳模块化承若一致，一个模块封装一个功能并对其它模块依赖最小。

Modules and themes are the units of customization in Magento. Modules provide business features, with supporting logic,  while themes strongly influence user experience and storefront appearance. Both components have a life cycle that allows them to be installed, deleted, and disabled. From the perspective of both merchants and extension developers, modules are the central unit of Magento organization. 

模块和主题都是Magento自定义的单元。模块提供业务功能，有逻辑支持， 而主题主要影响用户体验和店面外观。两个组件都有生命周期来被安装、删除、关闭。从商人和扩展开发者角度模块是Magneto组织的核心

The Magento Framework provides a set of core logic: PHP code, libraries, and the basic functions that are inherited by the modules and other components.

Magento框架提供一组核心逻辑： 继承自其它模块和组件的PHP 代码、库、和基础功能，


<h3>Module purpose 模块目的</h3>

The purpose of each module is to provide specific product features by implementing new functionality or extending the functionality of other modules. Each module is designed to function independently, so the inclusion or exclusion of a particular module does not typically affect the functionality of other modules.

每个模块的目的是通过实现新的功能或是扩展其它模块的功能来提供特定的系统功能。每个模块都被设计为功能独立的，包含或排队指定模块一般不会影响其它模块的功能。

<h3>Module components 模块组件</h3>

A module is a directory that contains the PHP and XML files (blocks, controllers, helpers, models) that are related to a specific business feature, such as Shipping. Specifically, a Magento module is composed of these software components: <a href="{{page.baseurl}}architecture/archi_perspectives/components/arch_themes.html">themes</a>, <a href="{{page.baseurl}}architecture/archi_perspectives/components/arch_libraries.html">libraries</a>, and <a href="{{page.baseurl}}architecture/archi_perspectives/components/arch_translations.html">language packages</a>. 

一个模块是包含一个特定业务功能相关的PHP和XML文件（区块、控制器、助手、模型）的一个目录，如配送。特别地，一个Magento模块是由这些软件组件组成的：<a href="{{page.baseurl}}architecture/archi_perspectives/components/arch_themes.html">主题</a>, <a href="{{page.baseurl}}architecture/archi_perspectives/components/arch_libraries.html">库</a>和 <a href="{{page.baseurl}}architecture/archi_perspectives/components/arch_translations.html">语言包</a>. 

模块结构概览查看 <a href="{{page.baseurl}}architecture/archi_perspectives/components/modules/mod_anatomy.html">Module anatomy模块剖析</a> . 


<h3>Where do modules live? 模块存在哪些地方</h3>

Modules typically live in the `app/code` directory of a Magento installation, in a directory with the following PSR-0 compliant format: `app/code/<Vendor>/<ModuleName>`. For example, the Customer module of Magento can be found at `app/code/Magento/Customer`. 

Magento安装后模块一般在app/code目录，目录服从PSR-0格式`app/code/<Vendor>/<ModuleName>`。如自定义模块可以在`app/code/Magento/Customer`目录找到。

Inside this folder, you will find all the code related to this module, including the `etc/module.xml` file, which contains the name and version of the module, as well as any dependencies.

这个目录你可找到所有和这个模块相关的代码， 包括`etc/module.xml`文件，XML文件定义这个模块名称和版本号及任何依赖

The standard placement of the `<ModuleName>` directory within the overall Magento file structure is `app/code/<Vendor>/<ModuleName>`. However, if you are creating a new module for distribution, you can just create the `<ModuleName>` directory and the required directories within it.

`<ModuleName>`目录标准占位包含完整的Magneto文件结构是`app/code/<Vendor>/<ModuleName>`。但如果你创建一个新的发布模块就可以只创建`<ModuleName>` 目录和它需要的子目录。

<h3>Working with modules 使用模块</h3>

Magento developers, administrators, and anyone building a Magento web site will want to review all relevant topics surrounding their particular goals and use cases.

Magneto开发者、系统管理员和任何构建Magento网站的人都会想回顾所有有关它们特定目标和使用案例的相关专题

有关扩展模块特定说明查看 <a href="{{page.baseurl}}extension-dev-guide/bk-extension-dev-guide.html">PHP开发者指南</a>



有关实现主题和其它组件信息查看 
<a href="{{page.baseurl}}frontend-dev-guide/bk-frontend-dev-guide.html">前端开发者指南</a>



<h3 id="arch-modules-related">相关专题</h3>

<a href="{{page.baseurl}}architecture/archi_perspectives/components/modules/mod_depend.html">模块依赖</a>

<a href="{{page.baseurl}}architecture/archi_perspectives/components/modules/mod_and_areas.html">模块和区域</a>

<a href="{{page.baseurl}}architecture/archi_perspectives/components/modules/mod_conventions.html">模块地址和全名规则</a>



