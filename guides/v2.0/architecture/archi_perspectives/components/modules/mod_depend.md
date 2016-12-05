---
layout: default
group: arch-guide
subgroup: Components
title: 模块依赖
menu_title: 模块依赖
menu_order: 6
level3_menu_node: level3child
level3_subgroup: modules
version: 2.0
github_link: architecture/archi_perspectives/components/modules/mod_depend.md
redirect_from: 
  - /guides/v1.0/architecture/modules/mod_depend.html
  - /guides/v2.0/architecture/modules/mod_depend.html
---

<h2 id="m2devgde-moddep-intro"> Module dependencies模块依赖</h2>

A <i>software dependency</i> identifies  one software component's reliance on another for proper functioning. A core principle of Magento architecture is the **minimization of software dependencies**. Instead of being closely interrelated with other modules, modules are optimally designed to be <i>loosely coupled</i>. Loosely coupled modules require little or no knowledge of other modules to perform their tasks. 

<i>软件依赖</i>识别一个软件组件为了合适的功能依赖于另一个。Magento架构的核心准则是**最小化软件依赖**。不是和其它模块紧紧联系，而是最适宜的设计成 <i>低耦合</i>。低耦合的模块为了执行它们的任务需求很少或不用知道其它模块。

Each Magento module is responsible for a unique feature. In practice, this means that:

每一个Magneto模块负责唯一的功能。事实上这意味者：

* Several modules cannot be responsible for one feature.
* 多个模块不能负责一个功能
* One module cannot be responsible for several features.
* 一个模块不能负责多个功能
* Module dependencies on other modules must be declared explicitly. You must also declare any dependency upon other components (for example, a theme, language package, or library).
* 模块依赖于其它模块必须是公开明确的。你还必须声明对其它组件的依赖关系（如主题、语言包或库）
* Removing or disabling a module does not result in disabling other modules.
* 移除或停用一个模块不会导致其它模块的关闭

<h3>What components can modules depend upon？</h3>
<h3>模块可以依赖于哪些组件之上</h3>
Although Magento architecture favors loosely coupled software components, modules can contain dependencies upon these software components:

尽管Magento架构喜欢低耦合的软件组件，模块也可以依赖于下面这些软件组件：

* other modules 其它模块
* PHP extensions PHP扩展
* libraries (either Magento Framework library or third party libraries)库（Magento框架库或第三方库）

<div class="bs-callout bs-callout-warning" id="warning">
<p>Note: You can lose the historical information contained in a module if the module is removed or disabled. We recommend alternative storage of module information before you remove or disable a module.
<br>
注意： 如果移除或关闭一个模块你就会丢失模块包含的信息，我们建议在移除或关闭一个模块前保存模块信息
</p></div>

<h3 id="m2devgde-moddep-intro">Manage module dependencies模块依赖</h3>

At a high level, there are three main steps for managing module dependencies:

在高水平，管理模块依赖有三个主要步骤：

1. Name and declare the module in the `module.xml` file.
1. 在module.xml文件命名和定义模块
2. Declare any dependencies that the module has (whether on other modules or on a different component) in the module's `composer.json` file.
2. 在模块的composer.json文件声明任何模块需要的依赖（在其它模块或不同的组件）
3. (*Optional*) Define the desired load order of config files and `.css` files in the `module.xml` file.
3. （*可选的*）在module.xml定义需要加载的配置文件和.css文件的顺序

Example: Module A declares a dependency upon Module B. Thus, in Module A's `module.xml` file, Module B is listed in the &lt;sequence> list, so that B’s files are loaded before A's. Additionally, you must declare a dependency upon Module B in A’s `composer.json` file. Furthermore, in the <a href="{{page.baseurl}}config-guide/config/config-php.html">deployment configuration</a>, Modules A and B must both be defined as enabled.

如：模块A声明依赖于模块B。然后在模块A的module.xml文件&lt;sequence> 列表列出模块B，因此模块B的文件会在A的文件之前加载。另外，你必须在A的composer.json文件声明依赖于模块B。而且在<a href="{{page.baseurl}}config-guide/config/config-php.html">部署配置</a>中模块A和B都必须定义为启用


<h2 id="m2arch-module-related">相关专题</h2>

<a href="{{page.baseurl}}architecture/archi_perspectives/components/modules/mod_intro.html">Module overview概览</a>


<a href="{{page.baseurl}}architecture/archi_perspectives/components/modules/mod_depend_types.html">Types of module dependencies模块依赖类型</a>




