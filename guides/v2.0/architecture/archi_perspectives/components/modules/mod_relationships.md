---
layout: default
group: arch-guide
subgroup: Components
title: 模块关系
menu_title: 模块关系
menu_order: 5
level3_menu_node: level3child
level3_subgroup: modules
version: 2.0
github_link: architecture/archi_perspectives/components/modules/mod_relationships.md
redirect_from: 
  - /guides/v1.0/architecture/modules/mod_relationships.html
  - /guides/v2.0/architecture/modules/mod_relationships.html
---

<h2 id="m2arch-module-relationships-overview">概览</h2>

Understanding how one module relates to another helps determine how it reacts to changes in that module. 

理解一个模块和其它模块的联系有助于确定它如何应对其它模块的变化

A single module can have the following types of relationships with another module:

一个模块和另一个模块可以有以下几种类型关系：

* **uses**: module A uses module B if it invokes behavior of module B 

* **使用**: 如果模块A调用模块B的动作，模块A使用模块B

* **reacts to**: module A reacts to module B if its behavior is triggered by an event in module B without module B knowing about module A 

* **响应**: 模块A响应模块B，如果它的动作是由模块B的事件触发而模块B不用知道模块A

* **customizes**: module A customizes module B if it modifies the behavior of module B 

* **定制**: 模块A定制模块B， 如果它修改模块B的行为

* **implements**: module A implements module B if it implements some, not necessarily all, behavior that is defined in module B 

* **实现**: 模块A实现模块B，如果它实现了一些模块B中的行为，不需要全部实现

* **replaces**: 	module A replaces module B if it provides its own version of the API exposed and implemented by module B 

* **替换**: 模块A替换模块B，如果由模块B暴露和实现的API它提供它自己的版本

<p>In a scenario where module A uses module B and module C customizes module B, the customizations in module C cannot break the API of module B so that module A still functions properly in the face of these customizations.</p>

<p>有一种场景，模块A使用模块B然后模块C定制模块B，模块C的定制是不会中断模块B的API，因此模块A面对这种定制依然功能正常</p>

<p><span class="image-wrap" style=""><img src="{{ site.baseurl }}common/images/archi_first_relate.png" style="border: 0px solid black"></span></p>

<p>Similarly, in a case where module A reacts to module B and module C customizes module B, the customizations in module C must not interfere with the events in module B that module A depends on.</p>

<p>同样地，在模块A响应模块B而模块C定制模块B的情形，模块C的定制肯定不会妨碍模块A依赖的模块B的动作</p>

<p><span class="image-wrap" style=""><img src="{{ site.baseurl }}common/images/archi_second_relate.png" style="border: 0px solid black"></span></p>

<p>If both module A and C customize module B, be careful about how these customizations are implemented so that you avoid conflicts (see below).</p>

<p>如果模块A和C同时定制了模块B，就要小心这些定制是如何实现的，好让你避免冲突（如下）</p>

<p><span class="image-wrap" style=""><img src="{{ site.baseurl }}common/images/archi_third_relate.png" style="border: 0px solid black"></span></p>

<p>If module A replaces module B, it needs to be able to do so in such a way that other modules are not affected.  That will mean not having direct hard dependencies on module B, but rather dependencies on a third module, module C, that both module A and B implement.</p>

<p>如果模块A替换模块B，要实现这种机制并且不影响其它模块需要这样， 就是不直接硬依赖于模块B，而是依赖于第三个模块，模块A和B都实现的模块C，</p>

<p><span class="image-wrap" style=""><img src="{{ site.baseurl }}common/images/archi_fourth_relate.png" style="border: 0px solid black"></span></p>


<h2 id="m2arch-module-related"> 相关专题</h2>

* <a href="{{page.baseurl}}architecture/archi_perspectives/components/modules/mod_intro.html">模块概览</a>



