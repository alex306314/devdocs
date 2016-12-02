---
layout: default
group: arch-guide
subgroup: Architectural Layers
title: 服务层
menu_title: 服务层
menu_order: 2
version: 2.0
github_link: architecture/archi_perspectives/service_layer.md
redirect_from: /guides/v1.0/architecture/archi_perspectives/service_layer.html
---

<h2>Service layer服务层</h2>
The service layer provides a bridge between the presentation layer and the model layer of domain logic and resource-specific data. This is implemented using *service contracts*, which are defined using PHP interfaces.

服务层为展示层和动态逻辑及资源相关数据模型之间提供了一座桥梁。这种是通过使用PHP接口定义的*服务契约*实现的

In general, the service layer

一般来讲服务服务层

* Resides below the presentation layer and above the domain layer.

* 存在于展示层之下而在领域层之上。

* Contains service contracts, which define how the implementation will behave.  

* 包括定义了实现如何表现的服务契约

* Provides an easy way to access the REST/SOAP API framework code (which also resides above the service contracts). You can bind service contracts to web service APIs in configuration files -- no coding required.

* 提供了一种简单的方式来获取REST/SOAP API框架代码（这个也存在于服务绑定之上）。不需要写代码只在配置文件就可以绑定服务契约到网络服务API。

* Provides a stable API for other modules to call into.

* 为其它模块提供了可以调用的稳定API



<h3>Who accesses the service layer? 谁可以获取服务层</h3>

All calls from web service interfaces, or users working with your storefront (that is, controller-initiated requests), are typically routed through the service layer. We strongly encourage the use of service contracts to call business logic.

所有从网络服务接口调用的，或用户操作你的店面（也就是控制器发起的请求），都是具有代表性的被路由通过服务层。我们鼓励使用服务契约来调用业务逻辑

External applications can make requests for business logic with simple SOAP and REST calls. With some simple XML or JSON, you can expose the service layer’s PHP API and make it accessible to REST or SOAP web services. Once implemented, a web service can make a single API call and return an information-rich data structure.

外部应用程序可以使用简单的SOAP和REST发起请求调用业务逻辑。使用一些简单的XML或JSON，你可暴露一些服务层PHP API让它们可以被REST或SOAP网络服务获取到。一旦实现，一个网络服务可以发起单一API调用并返回信息丰富的数据结构。

Service contract clients include:

服务契约客户包括：

* Controllers (initiated by actions of users of the storefront)
* 控制器（由用户操作从店面发起）
* Web services (SOAP and REST API calls)
* 网络服务（SOAP和REST API调用）
* Other Magento modules through service contracts
* 其它使用了服务契约的Magento模块

<h3>Service contract anatomy服务契约剖析</h3>

The service contract of a module is defined by the set of interfaces in the module's `/Api`. It typically consists of:

一个模块的服务契约被一组接口定义，在模块的/Api目录。特点包括：

* service interfaces in the `/Api` namespace of the module
* 服务接口在模块的/Api命名空间里
* data (or *entity*) interfaces in the `Api/Data` directory. *Data entities* are data structures passed to and returned from service interfaces.
* 数据（或*实体*）接口是在Api/Data目录。 *数据实体*是被发送到或接收自服务接口的数据结构


Typically, service contracts provide three distinct types of interfaces:
典型的， 服务契约提供三种不同的接口：

* Repository interfaces 仓库接口
* Management interfaces 管理接口
* Metadata interfaces 元数据接口

However, there is no requirement that service contracts conform to all three patterns.
不管怎样，服务契约没有必要三种模式全部遵从。

<h3>Advantages of service contracts服务契约的优点</h3>
Service contracts permit you to add a new customer extension that adds or changes business logic-level resource models and models without breaking the system. How? Through the use of the &lt;preference&gt; element of a dependency injection config file (`di.xml`) file. The `di.xml` file specifies which PHP class to use for the interface `Magento\Customer\Api\CustomerRepositoryInterface`.

服务契约允许你添加新的自定义扩展来增加或改变业务逻辑层资源模型和模型， 而不用破坏系统。如何做？ 通过使用依赖配置文件（di.xml）&lt;个性化&gt;元素。 di.xml文件指定让`Magento\Customer\Api\CustomerRepositoryInterface`接口使用哪个PHP类

Another module can change this interface file by specifying a different class name. However, if the client code uses the interface definition only, no class change is necessary.

其它模块可以通过指定一个不同的类名来改变这个接口文件。而如果客户端代码只是使用接口定义，就没必要修改类。

<h3 id="related">相关专题</h3>

<a href="{{page.baseurl}}architecture/archi_perspectives/arch_diagrams.html">架构图</a>

<a href="{{page.baseurl}}architecture/archi_perspectives/ALayers_intro.html">架构层概览</a>
