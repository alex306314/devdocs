---
layout: default
group: arch-guide
subgroup: Architectural Basics
title: 简化前端定制
menu_title: 简化前端定制
menu_node:
menu_order:
version: 2.0
github_link: architecture/frontend_custom_strategies.md
---

<h2 id="m2arch-whatis-overview">简化前端定制</h2>


The Magento frontend is designed to optimize storefront customization. Merchants are encouraged to use Magento components to customize the look-and-feel of their storefronts.

Magento 前端是设计成优化前端定制。鼓励店主使用magento组件来定制他们的店面的外面。

Highly extensible <i>themes</i> are the central mechanism for Magento front-end customization. Merchants are encouraged to extend and transform the appearance of their storefronts using themes.

Magento前端定制的核心机制是高可扩展的<i>主题</i>, 鼓励店主使用主题来扩展和改变他们店面外面。

Magento provides several tools to help you significantly jumpstart the storefront customization process:

Magneto 提供了一些工具来帮助你有效的开始进行前端定制操作：

* Magento Blank Theme 空白主题

* <a href="{{page.baseurl}}ui-components/ui-component.html">Magento UI库组件</a>

* <a href="{{page.baseurl}}pattern-library/bk-pattern.html">Magento Admin Pattern Library</a>


查看<a href="{{page.baseurl}}frontend-dev-guide/bk-frontend-dev-guide.html">前端开发者指南</a>获取更多创建主题的信息.  


<h3>Magento 空白主题</h3>
The Magento blank theme template provides a launchpad for storefront customization. You can use this boilerplate as a robust starting point for your own theme development.

Magento 空白主题模板为前端定制提供了一个发射台，你可以使用这个空白模板做为你的主题开发起点。


<h3>Magento UI 组件</h3>
Using Magento standard coding and styling tools can help:

使用Magento标签代码和样式工具可以帮助：

* 保持前端设计的一致性
* 简化（加快）设计过程

This component library contains standard reusable components for form features, such as fields and buttons, and navigation elements. The Magento UI library is a set of generic web components and Magento-specific patterns, which simplifies the process of Magento theme creation and customization.

这个组件库包括一些可重用标签表单组件，如域和按钮、导航元素。Magento UI库是一组能用网页组件和magento特有模式， 简化主题创建和定制的过程。

这个库的事多信息查看<a href="{{page.baseurl}}ui-components/ui-component.html">Magento UI 库组件</a>.

<h3>Magento 后台基准库</h3>

A <i>pattern library</i> is a collection of user interface (UI) design patterns that can be re-used in locations throughout your product installation. The <a href="{{page.baseurl}}pattern-library/bk-pattern.html">Magento Admin Pattern Library</a> defines examples of components that administrators working with the storefront can use.

基准库是一组可重用用户界面设计模式，存在于整个产品安装。<a href="{{page.baseurl}}pattern-library/bk-pattern.html">Magento后台基准库</a>定义了后台管理员管理店面可以使用的一些示例组件

Form elements included in the Magento Admin pattern library include:

Magento后台基准库包括的静音元素有：

* address form 地址表单
* button bar 按钮条
* container 容器
* tabs
* sign in form 登陆表单

这些表单元素在默认的magento店面到处都有。这种模式为扩展开发者和管理员提供了一套有价值的软件组件（和间接的，用户体验）语言

Magneto后台基准库作为一个模块建立在LESS预编译器之上。你可以从Magento市场免费下载这个模块的当前版本


更新关于使用这个库的更多信息查看<a href="{{page.baseurl}}pattern-library/bk-pattern.html">Magento 后台基准库</a>.


<h3 id="m2arch-related">相关讨论主题</h3>

<a href="{{page.baseurl}}architecture/extensibility.html">扩展性和模块化</a>

<a href="{{page.baseurl}}architecture/global_extensibility_features.html">Global extensibility features</a>

<a href="{{page.baseurl}}pattern-library/bk-pattern.html">Magento 后台基准库</a>

<a href="{{page.baseurl}}ui-components/ui-component.html">Magento UI组件库</a>
