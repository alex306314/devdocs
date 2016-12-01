---
layout: default
group: arch-guide
subgroup: Architectural Basics
title: 扩展性和模块化
menu_title:
menu_node:
menu_order:
version: 2.0
github_link: architecture/extensibility.md
---

<h2 id="m2arch-whatis-overview">扩展性和模块化</h2>


Product <i>extensibility</i> describes how easy  it is to expand  a product's feature set. An extensible product has been designed from its earliest  stages for  customization and enhancement. Extensible products are designed for ease in expanding your installation's feature set, enriching current features, and integrating with third-party software.

系统<i>扩展性</i>描述的是扩展系统的功能很简单。一个可扩展的系统是从他的早期阶段被设计为可定制化和优化处理。可扩展系统被设计为容易扩展原有特性，增强现有功能及集成第三方软件。


Maximizing extensibility has been our goal through all aspects of Magento development.  Core tasks such as shipping are packaged as discrete modules, and you expand your features by installing modules that you either buy from third-party vendors or create yourself. While logic specific to each shipping carrier is packaged in a discrete module, you can easily add or delete shipping providers by simply adding or deleting modules. The Magento Framework provides common logic to control routing and other core application functions.  

最大限度的可扩展性是我们开发Magento的所有方面的目标。核心功能如发货都打包成独立模块，你可以通过安装买来的第三方扩展或自定义模块来扩展需要的特性。同时每个货运公司的特定逻辑是被打包成了独立模块，你可以很容易通过添加或删除模块来添加或删除货运提供者。Magneto框架提供通用的逻辑来控制路由和其它一些核心应用程序函数。


<h3>是什么保证系统的可扩展性? </h3>

<i>Magento extensibility</i> describes the product's built-in ability for developers and merchants to routinely extend their storefront’s capabilities as their business grows.

<i>Magento可扩展性</i>为开发者和商户描述了系统的内建功能，保证在他们业务增长时可以一致的扩展他们的网店功能。


<h4>Which factors affect extensibility? 哪些因素影响可扩展性</h4>

* <b>architectural principles that guide product structure</b>. Central to the Magento model of software development is the practice of replacing or extending core code rather than editing it. This strategy supports your efforts to maintain the integrity of the tested code we provide while still extensively customizing your storefront.

* <i>指导系统结构的架构原则</i>。深入Magento软件开发模型的是尝试替换或扩展核心代码而不是编辑它。这种策略支持你的影响支保持我们提供的测试过代码的完整性，同时也可以全面自定义网店。

* <b>open-source software to create and manage extensions</b>. Magento is built on open-source technologies, built  for the development community. It uses Composer, an open-source tool, to manage dependencies. See <a href="{{page.baseurl}}architecture/tech-stack.html">Technology Stack</a>  for a complete list.

* <b>开源软件来创建和管理扩展</b>。Magento是建立在开源技术之上的，由开发社区构建。它使用Composer, 一个开源工具，来管理依赖。完整列表查看<a href="{{page.baseurl}}architecture/tech-stack.html">技术栈</a>

* <b>coding standards</b>. Adherence to  standard best practices for PHP and JavaScript code ensures that the code base is sound. Magento has adopted most of the Zend Framework Coding Standards for PHP. See <a href="{{page.baseurl}}coding-standards/bk-coding-standards.html">Coding Standards</a> for more information.

* <b>编码规范</b>。坚持PHP和JS代码最佳标准实践

* <b>upgrade and versioning strategies</b>. Magento has well-defined upgrade and versioning strategies that can help you avoid any problems with software component dependencies. Add modules after confirming that the module version is compatible with the Magento Framework version.


<h3 id="m2arch-related">Related topics</h3>


<a href="{{page.baseurl}}architecture/archi_perspectives/ABasics_intro.html">Architectural basics</a>

<a href="{{page.baseurl}}architecture/global_extensibility_features.html">Global product features that support extension development</a>

<a href="{{page.baseurl}}architecture/frontend_custom_strategies.html">Ease of frontend customization</a>
