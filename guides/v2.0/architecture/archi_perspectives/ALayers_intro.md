---
layout: default
group: arch-guide
subgroup: Architectural Layers
title: 架构层概览
menu_title: 架构层
menu_node: parent
menu_order:
version: 2.0
github_link: architecture/archi_perspectives/ALayers_intro.md
redirect_from: /guides/v1.0/architecture/archi_perspectives/ALayers_intro.html
---


<h2>Architectural layers overview 架构层概览</h2>

At its highest level, Magento's product architecture consists of the core product code plus optional <i>modules</i>. These optional modules enhance or replace the basic product code.

在最高层级，Magento系统架构由核心系统代码加上会加 <i>模块</i>组成。这些附加模块增强或替换基础系统代码

If you are substantially customizing the basic Magento product, module development will be your central focus. Modules organize code that supports a particular task or feature. A module can include code to change the look-and-feel of your storefront as well as its fundamental behavior.

如果你大量定制基础Magento系统，模块开发会是你核心关注点。模块组织支持一个特定任务和作用的代码。一个模块可以包括用来改变你的网站外观和它的基本行为的代码

Your modules function with the core Magento product code, which is organized into layers. Understanding layered software pattern is essential for understanding basic Magento product organization.

你的模块功能和核心Magento系统代码是分层组织的。理解层分层软件模式是理解基本Magento系统组织的基本要素。

Layered software is a popular, widely discussed principle in software development. Many resources exist for this topic, but consider consulting Pattern-Oriented Software Architecture for a general discussion.

分层软件是一种知名的广泛讨论的软件开发原则。存在有很多和这个主题有关的资源，但对一般的讨论考虑商议面向模式的软件架构

<h3>Advantages of layered application design分层的应用程序设计的优点</h3>
Layered application design offers many advantages, but users of Magento will appreciate:

分层应用程序设计提供很多优点，但Magneto用户会感激：

* Stringent separation of business logic from presentation logic simplifies the customization process. For example, you can alter your storefront appearance without affecting any of the backend business logic.

* 严格的从展示逻辑分离出业务逻辑简化定制处理。如你可以修改店面外观而不用影响任何后台业务逻辑

* Clear organization of code predictably points extension developers to code location.

* 清楚的代码组织可预见的指引扩展开发者到编码位置。


<h3>相关主题</h3>

<a href="{{page.baseurl}}architecture/archi_perspectives/arch_diagrams.html">Architectural diagrams架构图</a>


<a href="{{page.baseurl}}architecture/archi_perspectives/present_layer.html">Presentation layer展示层</a>

<a href="{{page.baseurl}}architecture/archi_perspectives/service_layer.html">Service layer服务层</a>


<a href="{{page.baseurl}}architecture/archi_perspectives/domain_layer.html">Domain layer域层</a>

<a href="{{page.baseurl}}architecture/archi_perspectives/persist_layer.html">Persistence layer持久层</a>
