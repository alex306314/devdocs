---
layout: default
group: arch-guide
subgroup: Components
title: 模块依赖类型
menu_title: 模块依赖类型
menu_order: 7
level3_menu_node: level3child
level3_subgroup: modules
version: 2.0
github_link: architecture/archi_perspectives/components/modules/mod_depend_types.md
redirect_from: /guides/v1.0/architecture/modules/mod_depend_types.html
---

<h2 id="m2devgde-moddep-declare-dep">Types of module dependencies模块依赖类型</h2>
There are two types of Magento module dependencies: hard and soft dependencies.

模块依赖有两种类型： 硬和软依赖

<h3>Hard dependencies硬依赖</h3>

Modules with a <i>hard dependency</i> on another module cannot function without the module it depends on. Specifically:

模块 <i>硬依赖</i>于另一个模块不能执行模块依赖之外的功能。特别地：

* The module contains code that directly uses logic from another module  (for example, the latter module's instances, class constants, static methods, public class properties, interfaces, and traits). 
* 这个模块包含直接使用另一个模块逻辑代码（如，后者的实例、类常量、表态方法、公开的类属性、接口、和特性）

* The module contains strings that include class names, method names, class constants, class properties, interfaces, and traits from another module. 
* 这个模块拥有从另一个模块的字符串，包括类名、方法名、类常量、类属性、接口和特性。
* The module deserializes an object declared in another module. 
* 这个模块反序列化另一个模块中声明的对象
* The module uses or modifies the database tables used by another module. 
* 这个模块使用或被另一个模块使用修改数据库表
	
<h3>Soft dependencies软依赖</h3>

Modules with a  <i>soft dependency</i> on another module can function properly without the other module, even if it has a dependency upon it. Specifically:

模块 <i>软依赖</i>于另一个模块可适当地执行除其它模块之外的功能，即使它依赖于它。特别地：

* The module directly checks another module's availability.
* 这个模块直接检测另一个模块的可用性
* The module extends another module's configuration.
* 这个模块扩展另一个模块的配置
* The module extends another module's layout.
* 这个模块扩展另一个模块的布局

<div class="bs-callout bs-callout-warning" id="warning">
<p>Note: If a module uses code from another module, it should declare the dependency explicitly.
<br>
注意： 如果一个模块使用来自另一个模块的代码， 它就必须明确声明依赖
</p>
</div>

Magento installs modules in the following order: <br>Magento使用如下顺序安装模块：


1) the module serving as a dependency for another module
1） 充当另一个模块依赖的模块
2) the module dependent on it
2） 依赖于它的模块

<h3 id="m2devgde-moddep-inapp-dep">Inappropriate dependencies不适当的依赖</h3>

Avoid creating the following dependencies:避免创建如下依赖：

* Circular dependencies (both direct and indirect)
* 循环依赖（直接和间接）
* Undeclared dependencies
* 未声明依赖
* Incorrect dependencies
* 不正确的依赖

<h3 id="m2devgde-moddep-diff-layer">Dependencies between modules in different product layers<br/>模块之间的依赖在不同的系统层</h3>
You can build dependencies between the modules belonging to different layers.<br/>
你可以在模块之间构建属于不同层的依赖

<h3 id="m2devgde-moddep-frmwk-layer">Dependencies in the Framework layer在框架层的依赖</h3>
Modules belonging to the Magento Framework can be used in the application layer by an explicit dependency.<br/>
属于Magento框架的模块能可通过明确的依赖作用于应用程序层

<div class="bs-callout bs-callout-info" id="info">
  <p>Note: In this case, using interfaces is preferable to using classes. <br/>注意：在这种情况，使用接口比使用类更好</p>
  <p>You can build dependencies between classes in the Magento Framework  even if they belong to different modules.<br/>你可以在Magento框架类之间构建依赖，即使他们属于不同的模块</p>
</div>


<h3 id="m2devgde-moddep-app-layer">Dependencies in the application layer<br/>应用程序层依赖</h3>
Modules belonging to the application layer cannot be used in the Magento Framework.
<br/>属于应用程序层的模块不能被用在Magento架构

You can build dependencies between classes in the application layer, but these classes must belong to the same module. Dependencies between the modules of the application layer should be built only by the service contract or the service provider interface (SPI).

你可以在应用程序层构建类之间的依赖，但这些类必须属于同一个模块。应用程序层模块之间的依赖应该只能通过服务契约或服务提供者接口（SPI）构建

<h2 id="m2arch-module-related">相关专题</h2>

<a href="{{page.baseurl}}architecture/archi_perspectives/components/modules/mod_depend.html">Module dependencies</a>


