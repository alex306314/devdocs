---
layout: default
group: arch-guide
subgroup: Architectural Layers
title: 领域层
menu_title: 领域层
menu_order: 3
version: 2.0
github_link: architecture/archi_perspectives/domain_layer.md
redirect_from: /guides/v1.0/architecture/archi_perspectives/domain_layer.html
---



<h2>Domain layer 领域层</h2>
The domain layer holds the business logic layer of a Magento module. It typically does not contain resource-specific or database-specific information. Its primary functions include:

领域层保存Magneto模块的业务逻辑层。通常不会包含资源相关或数据库相关信息。主要功能包括：

* Defines the generic Magento data objects, or models, that contain business logic. This logic defines which operations can be performed on particular types of data, such as a Customer object. These models contain generic information only. Applications can also use SOAP or RESTful endpoints to request data from models.

* 定义一般的包含业务逻辑的Magento数据对象或模型。这些逻辑定义哪些操作可以执行在特定类型的数据上，如一个客户对象。这些模型只包含一般的信息。应用程序也可以使用SOAP或RESTfull终端从模型请求数据

* (Optionally) Includes the implementation of service contracts, although not their definition.
* （可选的）包含服务契约的实现， 虽然没有它们的定义

Best practice: Use service contracts to communicate to the domain layer by passing data types through strongly typed objects. This practice can help you avoid the need to replace presentation layer code when replacing business layer logic.

最佳实践：使用服务契约通过传递强类型对象数据类型和领域层通信。这种做法在修改了业务层逻辑时可以帮助你避免修改展示层代码


<h3>Models 模型</h3>

Each domain-layer model contains a reference to a resource model, which it uses to retrieve data from the database with MySql calls.  This resource model contains logic for connecting to the underlying database, typically MySQL. A model requires a resource model only if the model data must persist.

每个领域层模型包括一个到使用执行mysql从数据库调取数据的资源模型的引用。这种资源模型包含链接底层数据库通常是Mysql的逻辑。 一个模型仅当模型数据需求保存时才调用资源模型

<h3>Who accesses the domain layer? 谁可以操作领域层？</h3>
There are three primary ways of accessing a module's domain-layer code:

有三种主要的方式来操作模块的领域层代码：

* Service contracts are the recommended way for one module to access another module's domain-level code. This loosely coupled solution is the optimal way for most modules to access another module.
* 服务契约是比较推荐的做法来让一个模块可以获取另一个模块的领域层代码。这种低耦合的方案是大多数模块访问其它模块的最佳方式。

* A module can directly call into another module. This tightly coupled solution is not recommended for most situations, but is sometimes unavoidable.
* 一个模块也可以直接调用另一个模块。这种紧密耦合的方案在多数情况是不推荐的，但有些时候也不可避免

* Domain layer code in one module can also plug itself into another module by:
* 领域层代码在一个模块里也可以把自己插接到其它模块， 通过：

    * event hooks 事件钩子
    * plugins 插件
    * `di.xml` files (with an SPI contract使用API契约)

Your strategy for calling another module's domain-layer code is highly dependent upon the unique configuration and needs of your system.

你调用另一个模块领域层代码的策略主要取决于你的系统独特配置和需求。

<h2 id="related">Related topics相关专题</h2>
<a href="{{page.baseurl}}architecture/archi_perspectives/arch_diagrams.html">Architectural diagrams框架图</a>


<a href="{{page.baseurl}}architecture/archi_perspectives/ALayers_intro.html">Architectural layers overview架构层概览</a>
