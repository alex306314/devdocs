---
layout: default
group: arch-guide
subgroup: Architectural Layers
title: 展示层
menu_title: 展示层
menu_order: 1
version: 2.0
github_link: architecture/archi_perspectives/present_layer.md
redirect_from: /guides/v1.0/architecture/archi_perspectives/present_layer.html
---




<h2> Presentation layer 展示层</h2>
When you interact with the Magento web interface, you are directly working with <i>presentation layer</i> code. The presentation layer contains both view elements (layouts, blocks, templates) and controllers, which process commands to and from the user interface). Presentation code controls web user interaction with the product and its appearance. You can extensively customize the user interface by using HTML, CSS, and PHTML files to modify elements of the presentation layer.

当你和Magneto网页接口交互时，你是直接和<i>展示层</i>代码一起工作。展示层包括视图元素（布局、区块、模板）和控制器，这个处理来自和到用户界面的命令。展示层代码控制网络用户和产品的交互及它的外观。你可以使用HTML、CSS和PHTML文件自由扩展用户界面来修改展示层元素。

<h3>Who uses the Presentation layer?谁使用展示层</h3>
Three types of Magento users interact with Presentation layer code. Magento uses *areas* to efficiently make web service calls, loading only the dependent code that is required for the particular type of user. Types of users and their associated areas include:

有三类Magento用户会和展示层代码交互。Magento使用*区域*来高效的调用网页服务，指定类型的用户的需求只加载依赖的代码。用户的分类和对应的区域包括：

* <b>Web users</b> interact with the store front, where they can see the View model of data displayed by Magento and interact with product UI elements to request data for view and manipulation. These users work within the (`frontend`) area.

* <b>网络使用者</b>和网店前端交互，他们可以在这里浏览由Magento展示的数据视图模型也可以和产品UI元素交互来为视图和操作请求数据。这些用户作用区域是（前台）

* <b>System administrators</b> customizing a storefront can indirectly manipulate the presentation layer by, for example, adding themes or widgets to the front end.

* <b>系统管理员</b>可以间接地操作展示层定制前台，如通过给前台添加主题或小部件。

* <b>Web API calls</b> can be made through HTTP just like browser requests, and can be made via AJAX calls from the user interface.

* <b>网络API调用</b>可以和浏览器请求一样通过HTTP产生，也可以由用户界面通过AJAX调用产生。


<h3>Presentation layer components展示层组件</h3>

One helpful way of understanding the Magento presentation layer components is by examining Magento <i>themes</i>. Magento themes organize both the visual aspect of your storefront and certain aspects of product behavior.

一种有效的理解Magento展示层组件的方式是通过检查Magento <i>主题</i>。 Magento主题组织网店视觉方面和某些产品行为方面。

Each theme resides in a unique directory and contains custom page layouts, templates, skins, and language files that work together to create a distinct user experience.

每个主题存在于唯一的目录里并包含工作在一起的自定义页面布局、模板、皮肤和语言文件来创建一个独特的用户体验。

For an extensive introduction to theme elements and an overview of how to extend and override the default Magento themes, see the <a href="{{page.baseurl}}frontend-dev-guide/bk-frontend-dev-guide.html">Frontend Developer Guide</a>.

大量的主题元素介绍和如何扩展或覆写默认主题概览， 查看<a href="{{page.baseurl}}frontend-dev-guide/bk-frontend-dev-guide.html">前台开发者指南</a>.

<h3>View model 视图模型</h3>

Magento generates the HTML for a page to display to a user from a tree of view elements.

Magento从一个视图元素树为一个用户展示页面生成HTML

View elements fall into two main categories: Blocks and containers.

视图元素主要有两大类： 区块和容器

* Blocks can generate dynamic content and can contain named child view elements that are similar to arguments being passed in. (The `as` attribute holds the child view element names for the parent block to reference them)

* 区块可以生成动态内容也可以和参数传递一样包含有名称的子视图元素。（as属性保存子视图元素名称以可以让父区块引用它们）

* Containers collect an ordered group of children view elements.

* 容器收集一组有序的子视图元素。

The browser forms a product web page by asking the view element tree to render itself into HTML. Containers and blocks emit HTML that encloses their children appropriately. Blocks can generate their content using static HTML, Knockout JS scripts, and PHTML.

浏览器通过请求视图元素树来渲染成HTML形成一个产品网页。容器和区块发出合理包含他们的子元素的HTML。区块可以使用HTML、Knockout JS脚本和PHTML生成它们的内容

<h3>How Presentation code calls other layers 展示层代码是如何调用其它层的</h3>
Presentation code typically calls service contracts, particularly for a store front. However, presentation code is occasionally dependent on a specific implementation that requires the presentation code to directly call the <i>business logic</i> layer. For example, the Admin UI screens are often tightly linked to a specific implementation and are not generic across implementations.

展示层代码代表性的调用服务绑定，特别是网店前台。然而，展示层代码偶尔会基于需要展示层直接调用<i>业务逻辑</i>的特定实现。 如后台UI界面会经常紧紧的连接到特定实现而不是普通的横过实现

The View layer calls code from the Model to get information about the state of the application (for example, the price of a product). Typically, the way it accesses the Model is through service contracts.

实图层从模型调用代码来获取关于应用程序状态（如产品的价格）的信息。作为特色的它获取模型是通过服务绑定

<h3>Presentation layer flow 展示层流程</h3>
Web users interact with components of the presentation layer to select actions that initiate calls to the underlying product layers. Presentation layer components make calls to the Service layer, which in turn sends requests to the Domain (or business logic) layer.

网络用户和展示层组件交互来选择开始调用在产品层下面的操作。 展示层组件调用服务层，然后轮流向域（或业务逻辑）层发送请求。

<h3 id="related">相关主题</h3>
<a href="{{page.baseurl}}architecture/archi_perspectives/arch_diagrams.html">架构图</a>

<a href="{{page.baseurl}}architecture/archi_perspectives/ALayers_intro.html">架构层概览</a>
