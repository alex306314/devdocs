---
layout: default
group: arch-guide
subgroup: A_Introduction
title: 什么是Magento?
menu_title: 介绍
menu_node: parent
menu_order: 1
version: 2.0
github_link: architecture/arch_whatis.md
redirect_from: /guides/v1.0/architecture/arch_whatis.html
---

<h2 id="m2arch-whatis-overview">什么是Magento?</h2>

Magento是一个高可定制电子商务平台和内容管理系统，你可以用来构建销售商品的网店或网站。Magneto提供通用电子商务特点，如购物车和存货管理， 并且鼓励自定义扩展来满足你的公司特定需求

强大和高度可扩展的Magento产品架构基本原理包括：

### OOP 架构和编码原则

面向对象编程 (OOP) 设计模式允许保证软件组件最大限度的灵活性和扩展性，让你可以设计实现可定制网站。OOP原则的优点包括加入行业标准编程设计模式并严格分离业务逻辑和展示。对象继承也很重要： 按照经典的面向对象编程方法，Magento平台提供的实现基本功能的核心组件可以被特定网站或应用自定义组件继承

### 强大的分层产品架构 layered product architecture

这种架构支持将视觉展示从业务逻辑分离。这种区分简化自定义网店外观和行为。架构层也为程序开发者提供一个高层编程模型（high level-model）来理解优化配置和复杂系统中的代码。Magento微调传统的MVC架构模型，通过：模块的文件是能过功能而不是文件类型进行代表性分组

<i>Magento框架</i>定义网站组件可以表现的基本概念和规则。 Magento框架包含模块权限的库而没有业务逻辑组件。它接收HTTP请求并路由到合适的模块

Magento框架集成以下软件层：

* <b>展示层</b>提供视图组件（view components）(布局、区块、模板，layouts, blocks, templates)和处理发送和接收来自用户界面的命令的控制器。展示层还包含WEB API服务绑定。（我们把这些服务器绑定放在展示层讨论是国为web API调用是和浏览器请求一样都通过HTTP，也可以通过用户端发送AJAX调用。所以web API调用可以由外部程序发起也可以从用户界面发起）

* <b>服务层</b>, 通过使用服务绑定， 定义所有界面与业务逻辑交互（如：创建消费者和获取税率）。服务务绑定简化替换或修改（通过插件）服务的操作。


* <b>领域层Domain layer</b>在基类、资源模型和数据存取功能提供让你可以扩展和自定义的核心业务逻辑和功能。业务逻辑规则定义数据如何从数据库获取和操作，都保存在业务逻辑层Business Logic layer.


### 灵活的扩展性
Magento uses dependency injection and service contracts to simplify the process of supplying a new implementation of a defined API.

Magneto使用依赖注入和服务绑定来简化一个新实现调用一个已定义的API的操作

依赖注入的优点有：

* 调用一个模块或服务的客户不用关心模块或服务的具体实现
* 你可以修改模块而不用替换任何你使用依赖注入框架把应用逻辑绑到一起的客户端

Service Contracts provide a new way to access public API endpoints. These PHP interfaces to modules streamline the use of APIs for most modules.

服务绑定提供一种新的方式访问仅供API端点。这些模块的API接口简化大多数模块使用API

### 模块化Modularity

模块组成一个Magneto系统最基本的功能单元。 Magneto模块包含要运行的请求的操作和功能逻辑。你通过编写和合并新模块到你的安装文件来扩展核心功能。使用Magneto主题和语言包来创建你的店面显示和语言

### 高可定制网站品牌
扩展和自定义你基于PHP-, HTML5- 和 CSS3-的网店核心组件主题和语言包来精确的控制网站的行为和外观

 <h3>开源技术栈</h3>
Magento技术栈提供一组健状的工具为你的特定需求自定义产品来开发大型的、分布式网店。Magento栈包括流行开源技术如Linux OS, Apache/Nginx server, MySQL, Zend, and Composer.

Magento技术栈更详细的描述，查看 <a href="{{page.baseurl}}architecture/tech-stack.html">Magento Technology Stack技术栈</a>.



<div class="bs-callout bs-callout-info" id="info">

  <p>关于设计和扩展Magnto组件更详细信息在<a href="{{page.baseurl}}extension-dev-guide/bk-extension-dev-guide.html">PHP 开发者指南</a>.</p>

</div>
