---
layout: default
group: arch-guide
subgroup: Logical View
title: Magento 框架
menu_title: Magento 框架
menu_order: 4
version: 2.0
github_link: architecture/archi_perspectives/framework.md
redirect_from: /guides/v1.0/architecture/archi_perspectives/framework.html
---


<h2>Magento Framework框架</h2>
The Magento Framework controls how application components interact, including request flow, routing, indexing, caching, and exception handling. It provides services that reduce the effort of creating modules that contain business logic, contributing to the goal of both making Magento code more modular as well as decreasing dependencies. 

Magneto框架控制应用程序组件如何影响，包括请求流程、路由、索引、缓存和异常处理。它提供减少创建包含业务逻辑的模块的影响的服务，作用于让Magento代码更模块化同时减少依赖的目标。

This primarily PHP software component is organized into logical groups called <i>libraries</i>, which all modules can call.  Most of the framework code sits under the domain layer or encloses the presentation, service, and domain layers. The framework contains no business logic.
(Although the Magento Framework does not contain resource models, it does contain a library of code to help implement a resource model.) 

这种PHP软件组件被组织按逻辑分组叫做<i>库</i>， 所有模块都可以调用。大多数框架代码放在域层下或靠近显示、服务和域层。框架包含非业务逻辑（即使Magento框架不包含资源模型，它也会包含一个库的代码来帮助实现一个资源模型）

<div class="bs-callout bs-callout-info" id="info">
  <p>Note: Don’t confuse the Magento framework with the Zend web application framework that ships with Magento.<br/>注意：不要困惑Magento框架使用zend应用程序框架</p>
</div>

You should never modify Framework files, although if you are extending Magento, you must know how to call Framework libraries. Modules you create will typically inherit from classes and interfaces defined in the Framework directories.  

你永远不要修改框架文件，即使你在扩展Magento，你必须知道怎么调用框架库。你创建的模块一般会继承自框架目录定义的类和接口

<h3>Magento Framework responsibilities框架职责</h3>
The Magento framework provides libraries that help reduce the effort of creating modules that contain business logic.

框架提供帮助减少创建包含业务逻辑的模块的影响

The framework is responsible for operations that are useful for potentially all modules, including: 

框架负责对所有潜在模块有用的操作包括：

* handling HTTP protocols 处理HTTP协议
* interacting with the database and filesystem 与数据库和文件系统交互 
* rendering content 渲染内容

<h3>Magento Framework organization 框架组织 </h3>
Here is the Magento framework folder structure:

这是框架文件夹结构 

```
Lib/
 ../Internal
    ../Magento
      ../Framework
 ```

* `/lib/internal` contains some non-PHP as well as PHP components. Non-PHP framework libraries includes JavaScript and LESS/CSS. 
* `/lib/internal` 包含一些非PHP和PHP组件。非PHP框架库包括JS和CSS

* `/lib/internal/Magento/Framework`  contains only PHP code. These are libraries of code plus the application entry point that routes requests to modules (that in turn call the framework libraries). For example,  libraries in the framework help implement a resource model (base classes and interfaces to inherit from) but not the resource models themselves. Certain libraries also support CSS rendering.
* `/lib/internal/Magento/Framework` 只包含PHP代码。这些是代码库加上路由请求到模块的应用程序入口点（轮流调用框架库）。如，框架里的库帮助实现资源模型（用于继承的基类和接口）但没有资源模型它本身。具体的库也包含CSS渲染

* `/lib/web` contains JavaScript and CSS/LESS files. These files reside  under `web` and not `internal` because they are accessible from a web browser, while the PHP code under `internal` is not. (Any code that a web browser must access should be under `web`, while everything else under `internal`.)
* `/lib/web` 包含JS和CSS文件。 这些文件在web下而不是internal， 因为它们从web 浏览器是可获取的，而在internal下面的PHP代码不是。（任何在浏览器可获取的代码必须在web下，而任何其它都在internal下面）

<div class="bs-callout bs-callout-info" id="info">
  <p>Note: The <code>lib/internal/Magento/Framework</code> directory maps to the <code>Magento\Framework</code> namespace.<br/>注意：<code>lib/internal/Magento/Framework</code>目录映射到<code>Magento\Framework</code>命名空间</p>
</div>


<h3>Highlights of the Magento Framework框架亮点</h3>
The Magento Framework (`lib/internal/Magento/Framework/`) provides a robust range of functionality. If you are an extension developer, you may be interested in this subset of Framework namespaces.
 
 框架提供一个健壮的一系列功能。如果你是扩展开发者，你会对架构命名空间子集感兴趣.

<table>
   <tbody>
      <tr style="background-color: lightgray">
         <th>Namespace</th>
         <th>Purpose</th>
         
      </tr>
      <tr>
         <td><code>Magento\Framework\Object</code>
         </td>
         <td>Provides standard functionality for storing and retrieving data through magic methods. This is the base class for many Magento classes.<br/>
         提供通过魔术方法保存和获取数据的标准功能。这是很多类的基类。
         </td>
      </tr><tr>
         <td><code>Magento\Framework\Object\Model</code>
         </td>
         <td>Contains base Model classes that almost all Magento Model classes extend from.
         <br>包含几乎所有模型类都继承的基模型类
         </td>
      </tr><tr>
         <td><code>Magento\Framework\Object\AbstractModel</code>
         </td>
         <td></td>
      </tr>
      <tr>
         <td><code>Magento\Framework\Object\AbstractResource</code></td>
         <td></td>
      </tr>
      <tr>
         <td><code>Magento\Framework\Object\Controller</code></td>
         <td>Contains classes to help return different types of results (for example, JSON and redirects).包含的类来帮助返回不同类型结果</td>
      </tr>
      <tr>
         <td><code>Magento\Framework\Object\View</code></td>
         <td>Contains code to render pages and layouts.包含渲染页面和布局的代码</td>
      </tr><tr>
         <td><code>Magento\Framework\Object\Data</code></td>
         <td>Contains additional classes that handle forms.包含处理表间的附加类</td>
      </tr><tr>
         <td><code>Magento\Framework\Object\URL</code></td>
         <td>Contains code to look up other pages in Magento.包含查看Magento其它页面的代码</td>
      </tr>
   </tbody>
</table>

<p>Other namespaces under <code>Magento\Framework</code> that will interest extension developers: <br>
扩展开发者会对<code>Magento\Framework</code>下面的其它命名空间感兴趣：
</p>

<table>
   <tbody>
      <tr style="background-color: lightgray">
         <th>Namespace</th>
         <th>Purpose</th>
         
      </tr><tr>
         <td><code>Magento\Framework\ObjectManager</code>
         </td>
         <td>Used to provide <i>dependency injection</i>.用来提供依赖注入 </td>
      </tr><tr>
         <td><code>Magento\Framework\App</code>
         </td>
         <td>Contains framework code that has knowledge about the Magento application. This code bootstraps the application and reads in the initial configuration. It also contains the entry point to the command line tools, the web application, and the cron job. And finally, it routes requests while providing the deployment context (such as reading in the configuration for the database configuration, languages, caching systems).
         <br>
         包含知道Magento应用程序的框架代码。这些代码引导应用程序然后读取初始化配置。它也包含命令工具、CRON定时工作的入口文件。最后它路由请求及提供布署上下文（如读取数据库参数、语言、缓存系统的设置）
</td>
      </tr><tr>
         <td><code>Magento\Framework\Api</code>
         </td>
         <td>Contains base classes for advanced functionality of extendable objects through the system (that is, objects that can be extended to add new data using Magento Marketplace extensions).包含基类用于整个系统高级功能可扩展对象（也就是可以被扩展使用市场的扩展来添加新数据的对象）</td>
      </tr><tr>
         <td><code>Magento\Framework\Config</code>
         </td>
         <td>Contains the generic configuration reader. Each config file has its own specialized reader extending these classes.包含一般的设置读取器。每一种配置文件拥有它自己特有的扩展自这些类的读取器</td>
      </tr><tr>
         <td><code>Magento\Framework\Filesystem</code>
         </td>
         <td>Contains classes that handle reading from and writing to the file system.包含处理读取表单和写到文件系统的处理</td>
      </tr><tr>
      <tr>
         <td><code>Magento\Framework\HTTP\PhpEnvironment</code>
         </td>
         <td></td>
      </tr><tr>
         <td><code>Magento\Framework\Session</code>
         </td>
         <td></td>
      </tr><tr>
         <td><code>Magento\Framework\Stdlib\Cookie</code>
         </td>
         <td>Code to handle the HTTP request/responses as well as session/cookies is found here.处理HTTP请求/响应和session/cookie的代码可以在这找到</td>
      </tr><tr>
         <td><code>Magento\Framework\Exception</code>
         </td>
         <td>Contains the basic exceptions that are thrown throughout the Magento codebase.包含贯穿基础代码的的基本异常</td>
      </tr>
      <tr>
         <td><code>Magento\Framework\Event</code>
         </td>
         <td>Contains the code that publishes synchronous events and that handles observers for any Magento event is handled here.包含发布同步事件和对任何Magento事件被处理的处理观察者代码
</td>
      </tr>
<tr>

         <td><code>Magento\Framework\Validator</code>
         </td>
         <td>Contains the code that validates data (currencies, not empty) and that handles observers for any Magento event.包含验证数据的代码（货币，非空）
</td>
      </tr>
      <tr>
      <td><code>Magento\Framework\Amqp</code></td>
      <td><p>Enterprise Edition only.</p>
      <p></p>Supports the Advanced Message Queuing Protocol, which is used by the Magento Message Queue Framework.支持高级信息队列协议，被消息队列框架使用</td>
      </tr>
</tbody>
</table>


