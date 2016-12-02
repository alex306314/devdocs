---
layout: default
group: arch-guide
subgroup: Components
title: 模块和区域
menu_title: 模块和区域
menu_order: 4
level3_menu_node: level3child
level3_subgroup: modules
version: 2.0
github_link: architecture/archi_perspectives/components/modules/mod_and_areas.md
redirect_from: 
  - /guides/v1.0/architecture/modules/mod_and_areas.html
  - /guides/v2.0/architecture/modules/mod_and_areas.html
---

<h2 id="m2arch-module-areas-overview"> Overview概览</h2>
An <i>area</i> is a logical component that organizes code for optimized request processing. Magento uses areas to streamline web service calls by loading only the dependent code for the specified area.  Each of the default areas defined by Magento can contain completely different code on how to process URLs and requests. 

一个 <i>区域</i>是一个为了优化请求处理组织的代码的逻辑组件。Magento使用区域网络服务调用合理化通过在特定区域只加载依赖的代码。Magento定义的每一个默认区域对如何处理URL和请求都可以包含完全不同的代码

For example, if you are invoking a REST web service call, rather than load all the code related to generating user HTML pages, you can specify a separate area that loads code whose scope is limited to answering  REST calls. 

例如，如果你请求一个REST网络服务调用，不是加载所有有关生成用户HTML页面的代码，你可以指定一个独立的区域来加载代码这个范围仅限于响应REST调用。


<h3>Magento area types 区域类型</h3>

Magento is organized into these main areas:

Magento被组织成如下区域：

*     **Magento Admin** (`adminhtml`): entry point for this area is `index.php` or `pub/index.php`. The Admin panel area includes the code needed for store management. The /app/design/adminhtml directory contains all the code for components you'll see while working in the Admin panel. 
*     **Magento后台** (`adminhtml`): 这个区域的入口点是index.php或pub/index.php。后台面板区域包括网店管理需要的代码。 /app/design/adminhtml目录包含使用后台面板能看见的所有组件代码

*     **Storefront** (`frontend`): entry point for this area is `index.php` or `pub/index.php`. The storefront (or `frontend`)  contains template and layout files that define the appearance of your storefront. 
*     **前端** (`frontend`): 这个区域入口点是index.php或pub/index.php。 前端包含定义前端外观的模板和布局文件

*     **Basic** (`base`): used as a fallback for files absent in `adminhtml` and `frontend` areas.
*     **基础** (`base`): 在`adminhtml` 区域`frontend`用作备用的缺省文件

You can also send requests to Magento using the SOAP and REST APIs. These two areas 

你也可以使用SOAP和REST API发送请求到magento。这有两个区域

*     **Web API REST** (`webapi_rest`): entry point for this area is `index.php` or `pub/index.php`. The REST area has a front controller that understands how to do URL lookups for REST-based URLs.
*     **Web API REST** (`webapi_rest`): 入口点是index.php或pub/index.php。REST区域有一个前端控制器可以理解如何处理基于REST的URL

*     **Web API SOAP** (`webapi_soap`): entry point for this area is `index.php` or `pub/index.php`. 


<h2 id="m2arch-module-using">How areas work with modules 区域和模块如何工作</h2>

Modules define which resources are visible and accessible in an area, as well as an area's behavior. The same module can influence several areas. For instance, the RMA module is represented partly in the `adminhtml` area and partly in the `frontend` area.

模块定义哪些资源在区域是可见的，以及区域的行为。相同的模块可以影响多个区域。如RMA模块代表性的一部分在`adminhtml`区域和另一部分在`frontend`区域

If your extension works in several different areas, ensure it has separate behavior and view components for each area.

如果你的扩展作用在多个不同区域，确保每个区域它拥有分开的行为和视图组件

Each area declares itself within a module. All resources specific for an area are located within the same module as well.

每个区域在一个模块定义它自己。特定区域的所有资源也放在相同模块里。

You can enable or disable an area within a module. If this module is enabled, it injects an area's routers into the general application's routing process. If this module is disabled, Magento will not load an area's routers and, as a result, an area's resources and specific functionality are not available.

你可启用或关闭一个模块区域。如果这个模块是启用的，它会把区域的路由注入到一般的应用程序路由处理中。如果模块是关闭的，Magneto不会加载区域的路由，同时区域的资源和相应功能也不能访问到。

<h3>Quick view of module/area interactions快速浏览模块/区域交互</h3>


* Modules should not depend on other modules' areas.
* 模块不能依赖于其它模块的区域
* Disabling an area does not result in disabling the modules related to it.
* 关于一个区域不会影响关半它相关的模块
* Areas are registered in the Dependency Injection framework `di.xml` file.
* 区域被注册在依赖注入框架di.xml文件中。

<h3>Note about Magento request processing 注意Magneto请求处理</h3>

Magento processes a URL request by first stripping off the base URL. The first path segment of the remaining URL identifies the request area.

Magento通过第一次剥离基URL处理一个URL请求。剩下URL第一部分指示了请求区域

After the area name, the URI segment specifies the *full front name*. When an HTTP request arrives, the handle is extracted from the URL. Magento uses the handle to identify which controller (a PHP class) and action (a PHP method in the class) to execute. A common action to display a HTML page is `index`, which returns an HTML page.

在区域名称之后，URI片段指定*全前端名称*. 当获取到一个HTTP请求，从URL取出操作。Magento使用这个操作区分运行哪个控制器和方法。显示一个HTML页面通用方法是index，返回一个HTML页面

<h2 id="m2arch-module-related"> Related topics相关专题</h2>

* <a href="{{page.baseurl}}architecture/archi_perspectives/components/modules/mod_intro.html">Module overview模块概览</a>



