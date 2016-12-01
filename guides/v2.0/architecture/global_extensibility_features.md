---
layout: default
group: arch-guide
subgroup: Architectural Basics
title: 支持扩展性的所有特点
menu_title: 支持扩展性的所有特点
menu_node:
menu_order:
version: 2.0
github_link: architecture/global_extensibility_features.md

---

<h2>支持扩展性的所有特点</h2>

所有Magento组件拥有扩展性的本质。这个讨论关注：

* Modularity 模块化
* Reliance on popular design patterns 依靠常用设计模式
* Coding standards 编码规范
* Flexible attribute types 灵活的属性类型
* Web APIs
* Service contracts and dependency injection 服务绑定和依赖注入
* Plug-ins 插件


<h3>模块化</h3>

<i>模块</i>的概念是Magento扩展开必的核心，软件组件（尤其, 模块, 主题和语言包）的模块化设计是产品的架构准则。离散代码通过特点组成独立的模块，因而降低了每个模块的外部依赖。

如果模块是独立的，你就可以修改或替换它而不会影响代码的其它地方。这种软件组件低隅合减少你的代码改动引起的涟漪效应

 如果开发模块的详细说明请查看<a href="{{page.baseurl}}extension-dev-guide/bk-extension-dev-guide.html">PHP 开发者指南</a> 。

<h3>依靠常用设计模式</h3>
Reliance on known architectural and programming structures helps PHP developers orient themselves to the specific development issues that affect coding in a particular product ecosystem. This can reduce the learning curve for new Magento developers.

使用知名的架构和程序结构帮助PHP开发者直接关注特定问题的开发修改个别系统代码。这样可以降低Magento开发者新手学习曲线。

Design patterns are time-tested, widely recognized software architecture constructs. Magento product architecture incorporates many well known patterns, but  Model-View-Controller (MVC)  holds particular interest for extension developers.

设计模式是经过时间考验的广泛认可的软件架构结构。Magento系统构架组合了很多知名模式，但Model-View-Controller (MVC)只有特定一部分是扩展开发者感兴趣的。

<h3>编码规范</h3>

Magento开发者需要熟悉我们编码规范、最佳实践和约定，特别是PHP文件格式、代码风格和文件全名规范的标准。Magento标准是基于ZF编码规范的。

指导手册和需求查看<a href="{{page.baseurl}}coding-standards/bk-coding-standards.html">编码规范</a>.


<h3>丰富的产品生态系统</h3>
The wider Magento ecosystem provides an extensive community and rich third-party marketplace for extensions. Visit Magento Marketplace for an overview of the many modules and themes available for download and to buy modules and theme packages, which offer more possibilities  for extending your storefront.  

Magneto生态系统提供很大的社区和丰富的第三方扩展市场。访问Magneto市场查看可以下载和购买的模块和主题及主题包，这些为你扩展网店提供更多的可能性。

<h3>弹性的属性类型</h3>
You can enhance your storefront by adding unique attributes to the default product attributes. For example, you might need to add a new attribute to describe a product, such as texture or an industry-specific rating. You can add these attributes from the Magento Admin, and the storefront  displays them.

你可以丰富的网店通过给默认的产品属性增加唯一的属性。如你可能需要添加一个新属性来描述一个产品，如质地或工业级评级， 你可以在magneto后台添加这些属性，然后在网店展示他们。


<table>
   <tbody>
      <tr style="background-color: lightgray">
         <th>属性类型</th>
         <th>是否在网店前端显示?</th>

      </tr>
<tr>
         <td>EAV
         </td>
         <td>no</td>
         </tr>

         <tr>
         <td>Custom
         </td>
         <td>yes</td>
         </tr>
         <tr>
         <td>Extension
         </td>
         <td>no</td>
         </tr>


</tbody>
</table>

Attribute types fall into three general categories:

属性类型分为三种类型：

* <b>EAV (Entity-Attribute-Value) attributes</b> are site-specific attributes that you can define for a local site using the Magento Admin.

* <b>EAV (Entity-Attribute-Value) 属性</b>是你可以为本地网站使用Magento后台定义的网站特定属性。

* <b>Custom attributes</b> are a subset of EAV attributes. Objects that use EAV attributes typically store values in several MySQL tables. The Customer and Catalog modules use EAV attributes.

* <b>自定义属性</b>是EAV属性的子集。使用EAV属性的对象特点是把值存储在多个mysql数据表中。顾客和产品模块都使用EAV属性。

* <b>Extension attributes</b>  often use more complex data types than custom attributes. These attributes do not appear in the storefront. Extension attributes are introduced by modules.

* <b>Extension attributes扩展属性</b>通常使用比自定义属性更复杂的数据类型。这些属性不会出现在前端。扩展属性由模块引入。

关于属性使用更多信息查看<a href="{{page.baseurl}}extension-dev-guide/bk-extension-dev-guide.html">PHP开发者指南</a>.

<h3>Web APIs</h3>
Magento or third-party services can be configured as a web API (REST or SOAP) with some simple XML. You can use these services to integrate your Magento installation into third-party applications, such as CRM (Customer Relationship Management), ERP (Enterprise Resource Planning) back office systems, and CMS (Content Management Systems).

Magento或第三方服务通过简单的XML可以被设置为WEB API(REST 或 SOAP)。你可以使用这些服务把magento集成到其它应用程序，如果CRM（客户关系管理系统）、ERP（企业资源规划）后台办公系统及CMS（内容管理系统）。

查看 <a href="{{page.baseurl}}get-started/bk-get-started-api.html">开始使用Magento Web APIs</a>获取更多信息.

<h3>Service contracts服务绑定, dependency injection依赖注入, and dependency inversion和依赖倒置</h3>
<i>Service contracts</i> provide a new way to access public API endpoints. These PHP interfaces offer robust, stable extension points to which clients can connect.  Service contracts define the endpoints that function as a module's public API. Defining these endpoints is an essential part of adding a module.

<i>服务绑定</i>提供一种新的方式来访问公共API节点。那些PHP接口为客户端提供可链接的健状稳定的扩展点。服务绑定定义模块公共API终点函数。定义这些终点是添加一个模块最基本的部分。

服务绑定在整个文档集都有讨论。 更详尽的介绍查看 <a href="{{page.baseurl}}architecture/archi_perspectives/service_layer.html">Service layer服务层</a>. 更多关于服务绑定和依赖注入查看<a href="{{page.baseurl}}extension-dev-guide/bk-extension-dev-guide.html">PHP开发者指南</a>。


Magento implements <i>dependency injection</i> along with service contracts. Dependency injection provides a mechanism for changing a module's behavior without altering the client or understanding nitty-gritty details of implementation. Both dependency injection and its related concept dependency inversion support Magento's fundamental architectural principles of modularity and ease-of-extensibility. They strongly encourage basic coding practices that support the loose coupling of software modules.

Magento通过服务绑定实现了<i>依赖注入</i>。依赖注入提供了一种机制可以改变模块行为而不用修改调用者或理解实现细节。无论依赖注入还是它相关概念依赖反转都是支持Magento基本架构模块化和易于扩展的本源。都鼓励支持软件模块松耦合基础代码实践

更多关于依赖注入和服务绑定查看<a href="{{page.baseurl}}extension-dev-guide/bk-extension-dev-guide.html">PHP 开发者指南</a>


<h3>Plug-ins插件</h3>

Plug-ins, like modules, are a mechanism for adding features to the core Magento product. <i>Plug-ins</i> enable you to make changes to the behavior of any public method in a Magento class. You can consider it a form of extension that uses the `Plugin` class.

插件和模块一样都是一种给Magneto核心添加新功能的机制。<i>插件</i>让你可以修改任何一个Magneto类的公共方法的行为。你可以把它当作使用了`Plugin`类的一种扩展。

Plug-ins are also called <i>interceptors</i>.  Applications use the plug-in pattern to change method behavior without modifying the actual class. Plug-ins can typically intercept method processing before or after the method runs, or only when the method throws an exception.

插件也可以叫<i>拦截器</i>。应该程序使用插件机制来修改方法的行为而不用修改真实的类。插件可以特定的拦截方法处理，在方法执行前或后或仅当方法抛出一个异常

关于定义和指定插件优先级更多信息查看 <a href="{{page.baseurl}}extension-dev-guide/bk-extension-dev-guide.html">PHP 开发者指南</a>


<h3 id="m2arch-related">相关主题</h3>
<a href="{{page.baseurl}}architecture/extensibility.html">扩展性和模块化</a>
