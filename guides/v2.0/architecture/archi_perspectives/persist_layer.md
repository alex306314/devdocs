---
layout: default
group: arch-guide
subgroup: Architectural Layers
title: 持久层
menu_title: 持久层
menu_order: 4
version: 2.0
github_link: architecture/archi_perspectives/persist_layer.md
redirect_from: /guides/v1.0/architecture/archi_perspectives/persist_layer.html
---


<h2 id="persistence">Persistence layer持久层</h2>

Magento uses an active record pattern strategy for persistence. In this system, the model object contains a *resource model* that maps an object to one or more database rows. A resource model is responsible for performing functions such as:

Magento对持久化使用Active Record模式策略。在这个系统里，模型对象包含一个映射一个对象到一个或多个数据表的*资源模型*。一个资源模型负责执行如下功能：

* Executing all CRUD (create, read, update, delete) requests. The resource model contains the SQL code for completing these requests.
* 运行所有的CRUD（增写改删）请求。资源模型包含完成这些请求的SQL代码

* Performing additional business logic. For example, a resource model could perform data validation, start processes before or after data is saved, or perform other database operations.
* 执行附加业务逻辑。如资源模型可以执行数据检测，执行在数据保存前或后的处理， 或执行其它数据库操作。


If you expect to return multiple items from a database query, then you would implement a special type of resource model known as a *collection*. A collection is a class that loads multiple models into an array-like structure based on a set of rules. This is similar to a SQL `WHERE` clause.

如果你期望从一条数据库查询获取多个项目，那么你需要实现一个特殊类型的被称为*集合*的资源模型。一个集合是一个加载多个模型成为符合一组规则的类似数组结构的类。有点像SQL的where子句

A simple resource model defines and interacts with a single table. However, some objects have a vast number of attributes, or they could have a set related objects that have varying numbers of attributes. In these cases, the objects are constructed using Entity-Attribute-Value (EAV) models. As a result, any model that uses an EAV resource has its attributes spread out over a number of MySQL tables. The `Customer` and `Catalog` resource models use EAV attributes.  

一个简单的资源模型会定义和交互单一的表。然而，一些对象拥有大量的属性，或它们会有一组相关的拥有很多不同属性的对象。在这种情况下，对象被构造成实体-属性-值（EAV）模型。因此，任何使用EAV资源的模型会使他的属性展开到多个Mysql数据表。 `Customer客户表` 和 `Catalog产品目录表`资源模型使用的就是EAV属性

<h3 id="related">相关专题</h3>
<a href="{{page.baseurl}}architecture/archi_perspectives/arch_diagrams.html">架构图表</a>

<a href="{{page.baseurl}}architecture/archi_perspectives/ALayers_intro.html">框架层概览</a>
